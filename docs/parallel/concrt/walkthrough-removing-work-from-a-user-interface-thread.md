---
title: 演练：从用户界面线程中移除工作
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377443"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>演练：从用户界面线程中移除工作

本文档演示如何使用并发运行时将 Microsoft 基础类 （MFC） 应用程序中的用户界面 （UI） 线程执行的工作移动到辅助线程。 本文档还演示如何提高冗长绘图操作的性能。

通过将阻塞操作（例如绘图）卸载到辅助线程，从 UI 线程中删除工作可以提高应用程序的响应能力。 本演练使用生成曼德布罗特分形的绘图例程来演示冗长的阻塞操作。 Mandelbrot 分形的生成也是并行化的良好候选项，因为每个像素的计算与所有其他计算无关。

## <a name="prerequisites"></a>先决条件

在开始本演练之前，请阅读以下主题：

- [任务并行度](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [并行算法](../../parallel/concrt/parallel-algorithms.md)

- [PPL 中的取消操作](cancellation-in-the-ppl.md)

我们还建议您在开始本演练之前了解 MFC 应用程序开发和 GDI+ 的基础知识。 有关 MFC 的详细信息，请参阅[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)。 有关 GDI+ 的详细信息，请参阅[GDI®](/windows/win32/gdiplus/-gdiplus-gdi-start)。

## <a name="sections"></a><a name="top"></a>部分

本演练包含以下各节：

- [创建 MFC 应用程序](#application)

- [实现曼德布罗特应用程序的串行版本](#serial)

- [从用户界面线程中删除工作](#removing-work)

- [提高绘图性能](#performance)

- [添加取消支持](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>创建 MFC 应用程序

本节介绍如何创建基本的 MFC 应用程序。

### <a name="to-create-a-visual-c-mfc-application"></a>创建可视化C++ MFC 应用程序

1. 使用**MFC 应用程序向导**创建具有所有默认设置的 MFC 应用程序。 请参阅[演练：使用新的 MFC 外壳控件](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)了解如何打开 Visual Studio 版本的向导的说明。

1. 键入项目的名称，例如 ，`Mandelbrot`然后单击 **"确定"** 以显示**MFC 应用程序向导**。

1. 在"**应用程序类型"** 窗格中，选择 **"单一文档**"。 确保清除**文档/视图体系结构支持**复选框。

1. 单击 **"完成"** 以创建项目并关闭**MFC 应用程序向导**。

   通过生成并运行应用程序，验证应用程序是否成功创建。 要生成应用程序，请在 **"生成"** 菜单上单击 **"生成解决方案**"。 如果应用程序生成成功，则通过单击 **"调试"** 菜单上的 **"开始调试**"来运行应用程序。

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>实现曼德布罗特应用程序的串行版本

本节介绍如何绘制曼德布罗特分形。 此版本将 Mandelbrot 分形绘制到 GDI+[位图](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)对象，然后将该位图的内容复制到客户端窗口。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>实现曼德布罗特应用程序的串行版本

1. 在*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中，添加以下`#include`指令：

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. 在 ChildView.h 中`pragma`，在指令之后`BitmapPtr`，定义类型。 类型`BitmapPtr`允许指向`Bitmap`对象的指针由多个组件共享。 当`Bitmap`对象不再被任何组件引用时，将删除该对象。

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. 在 ChildView.h 中，将以下代码`protected`添加到类的`CChildView`部分：

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. 在 ChildView.cpp 中，注释掉或删除以下行。

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   在调试生成中，此步骤可防止应用程序使用分配器`DEBUG_NEW`，该分配器与 GDI+ 不兼容。

1. 在 ChildView.cpp 中`using`，向`Gdiplus`命名空间添加一个指令。

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 将以下代码添加到类的构造函数和析构函数中`CChildView`，以初始化和关闭 GDI+。

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. 实现 `CChildView::DrawMandelbrot` 方法。 此方法将曼德布罗特分形绘制到指定`Bitmap`对象。

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. 实现 `CChildView::OnPaint` 方法。 此方法调用`CChildView::DrawMandelbrot`对象的内容，然后将`Bitmap`对象的内容复制到窗口。

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. 通过生成并运行应用程序，验证应用程序是否已成功更新。

下图显示了曼德布罗特应用程序的结果。

![Mandelbrot 应用程序](../../parallel/concrt/media/mandelbrot.png "Mandelbrot 应用程序")

由于每个像素的计算在计算上成本高昂，因此在整体计算完成之前，UI 线程无法处理其他消息。 这可能会降低应用程序中的响应能力。 但是，您可以通过从 UI 线程中删除工作来缓解此问题。

[[顶部](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>从 UI 线程中删除工作

本节演示如何从 Mandelbrot 应用程序中的 UI 线程中删除绘图工作。 通过将绘图工作从 UI 线程移动到辅助线程，UI 线程可以在工作线程在后台生成图像时处理消息。

并发运行时提供了三种运行任务的方法：[任务组](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[异步代理](../../parallel/concrt/asynchronous-agents.md)和[轻量级任务](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 尽管可以使用这些机制中的任何一种从 UI 线程中删除工作，此示例使用[并发：：task_group](reference/task-group-class.md)对象，因为任务组支持取消。 本演练稍后将使用取消来减少调整客户端窗口大小时执行的工作量，并在破坏窗口时执行清理。

此示例还使用[并发：：unbounded_buffer](reference/unbounded-buffer-class.md)对象，以使 UI 线程和辅助线程能够相互通信。 工作线程生成映像后，它将指向`Bitmap`对象的指针发送到对象，`unbounded_buffer`然后将绘制消息发布到 UI 线程。 然后，UI 线程从`unbounded_buffer``Bitmap`对象接收对象并将其绘制到客户端窗口。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>从 UI 线程中删除绘图工作

1. 在*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中，添加以下`#include`指令：

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. 在 ChildView.h`task_group`中`unbounded_buffer`，向`protected``CChildView`类的部分添加和成员变量。 对象`task_group`保存执行绘图的任务;对象`unbounded_buffer`保存已完成的曼德布罗特图像。

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. 在 ChildView.cpp 中`using`，向`concurrency`命名空间添加一个指令。

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. In the `CChildView::DrawMandelbrot` method, after the call to `Bitmap::UnlockBits`, call the [concurrency::send](reference/concurrency-namespace-functions.md#send) function to pass the `Bitmap` object to the UI thread. 然后向 UI 线程发布绘制消息，使工作区失效。

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 更新`CChildView::OnPaint`方法以接收更新`Bitmap`的对象，并将图像绘制到客户端窗口。

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   如果`CChildView::OnPaint`消息缓冲区中不存在一个图像，该方法将创建一个任务来生成 Mandelbrot 映像。 在初始绘制消息以及另一`Bitmap`个窗口在客户端窗口前面移动时，消息缓冲区将不包含对象。

1. 通过生成并运行应用程序，验证应用程序是否已成功更新。

UI 现在响应更快，因为绘图工作是在后台执行的。

[[顶部](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a>提高绘图性能

Mandelbrot 分形的生成是并行化的良好候选项，因为每个像素的计算与所有其他计算无关。 要并行化绘图过程，请将方法中的`for``CChildView::DrawMandelbrot`外部循环转换为对[并发：:p阿拉雷尔算法的](reference/concurrency-namespace-functions.md#parallel_for)调用，如下所示。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

由于每个位图元素的计算都是独立的，因此不必同步访问位图内存的绘图操作。 这使得性能能够随着可用处理器数量的增加而扩展。

[[顶部](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>添加取消支持

本节介绍如何处理窗口调整大小，以及如何在窗口被销毁时取消任何活动绘图任务。

[PPL 中的"取消"](cancellation-in-the-ppl.md)文档说明了取消在运行时的工作原理。 取消是合作的;因此，它不会立即发生。 要停止已取消的任务，运行时在后续调用从任务到运行时时引发内部异常。 上一节演示如何使用`parallel_for`该算法来提高绘图任务的性能。 调用 使`parallel_for`运行时停止任务，从而使取消工作。

### <a name="cancelling-active-tasks"></a>取消活动任务

Mandelbrot 应用程序创建`Bitmap`其维度与客户端窗口大小匹配的对象。 每次调整客户端窗口的大小时，应用程序都会创建一个额外的后台任务，以生成新窗口大小的映像。 应用程序不需要这些中间图像;因此，应用程序不需要这些中间图像。它只需要最终窗口大小的图像。 为了防止应用程序执行此附加工作，可以取消`WM_SIZE`和`WM_SIZING`消息的消息处理程序中的任何活动绘图任务，然后在调整窗口大小后重新安排绘图工作。

要在调整窗口大小时取消活动绘图任务，应用程序将`WM_SIZING``WM_SIZE`调用 和币处理程序中的[并发：：task_group：：取消](reference/task-group-class.md#cancel)方法。 消息的`WM_SIZE`处理程序还调用[并发：：：task_group：：等待](reference/task-group-class.md#wait)方法等待所有活动任务完成，然后为更新的窗口大小重新安排绘图任务。

销毁客户端窗口时，最好取消任何活动绘图任务。 取消任何活动绘图任务可确保工作线程不会在客户端窗口销毁后向 UI 线程发送消息。 应用程序取消`WM_DESTROY`消息处理程序中的任何活动绘图任务。

### <a name="responding-to-cancellation"></a>响应取消

执行`CChildView::DrawMandelbrot`绘图任务的方法必须响应取消。 由于运行时使用异常处理来取消任务，`CChildView::DrawMandelbrot`因此该方法必须使用异常安全机制来保证正确清理所有资源。 本示例使用*资源获取初始化*（RAII） 模式来保证在取消任务时未锁定位图位。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>在曼德布罗特应用程序中添加对取消的支持

1. 在 ChildView.h 中`protected`，在`CChildView`类部分中，为`OnSize`、`OnSizing`和`OnDestroy`消息映射函数添加声明。

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. 在 ChildView.cpp 中，修改消息映射以包含`WM_SIZE`的`WM_SIZING`处理程序。 `WM_DESTROY`

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. 实现 `CChildView::OnSizing` 方法。 此方法取消任何现有的绘图任务。

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. 实现 `CChildView::OnSize` 方法。 此方法取消任何现有绘图任务，并为更新的客户端窗口大小创建新的绘图任务。

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. 实现 `CChildView::OnDestroy` 方法。 此方法取消任何现有的绘图任务。

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. 在 ChildView.cpp 中`scope_guard`，定义实现 RAII 模式的类。

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 调用 后，将以下`CChildView::DrawMandelbrot`代码添加到 方法`Bitmap::LockBits`：

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   此代码通过创建`scope_guard`对象来处理取消。 当对象离开范围时，它将解锁位图位。

1. 修改方法的`CChildView::DrawMandelbrot`末尾以在位图位`scope_guard`解锁后（但在将任何消息发送到 UI 线程之前）关闭对象。 这可确保在未锁定位图位之前不更新 UI 线程。

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. 通过生成并运行应用程序，验证应用程序是否已成功更新。

调整窗口大小时，仅针对最终窗口大小执行绘图工作。 销毁窗口时，任何活动绘图任务也会被取消。

[[顶部](#top)]

## <a name="see-also"></a>另请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[任务并行度](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)
