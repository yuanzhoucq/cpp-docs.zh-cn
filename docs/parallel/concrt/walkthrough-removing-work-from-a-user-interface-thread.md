---
title: 演练：从用户界面线程中移除工作
ms.date: 04/25/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 214796777968c8aec7116a848e791aeef0d3af7b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512263"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>演练：从用户界面线程中移除工作

本文档演示如何使用并发运行时将 Microsoft 基础类 (MFC) 应用程序中的用户界面 (UI) 线程执行的工作移到工作线程中。 本文档还演示了如何提高长时间的绘图操作的性能。

通过将阻止操作 (例如, 绘制) 移到工作线程, 从 UI 线程删除工作可以提高应用程序的响应能力。 本演练使用一个绘图例程, 该例程生成 Mandelbrot 分形以演示长时间的阻止操作。 Mandelbrot 分形的生成也是并行化的理想候选项, 因为每个像素的计算都独立于所有其他计算。

## <a name="prerequisites"></a>系统必备

在开始本演练之前, 请阅读以下主题:

- [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [并行算法](../../parallel/concrt/parallel-algorithms.md)

- [PPL 中的取消操作](cancellation-in-the-ppl.md)

在开始本演练之前, 我们还建议你了解 MFC 应用程序开发和 GDI + 的基本知识。 有关 MFC 的详细信息, 请参阅[Mfc 桌面应用程序](../../mfc/mfc-desktop-applications.md)。 有关 GDI + 的详细信息, 请参阅[Gdi +](/windows/win32/gdiplus/-gdiplus-gdi-start)。

##  <a name="top"></a> 部分

本演练包含以下各节：

- [创建 MFC 应用程序](#application)

- [实现 Mandelbrot 应用程序的串行版本](#serial)

- [从用户界面线程中移除工作](#removing-work)

- [提高绘图性能](#performance)

- [添加取消支持](#cancellation)

##  <a name="application"></a>创建 MFC 应用程序

本部分介绍如何创建基本 MFC 应用程序。

### <a name="to-create-a-visual-c-mfc-application"></a>创建 Visual C++ MFC 应用程序

1. 使用**Mfc 应用程序向导**创建具有所有默认设置的 mfc 应用程序。 请参阅[演练：使用新的 MFC Shell 控件](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)获取有关如何为你的 Visual Studio 版本打开向导的说明。

1. 键入项目的名称, 例如`Mandelbrot`,, 然后单击 **"确定"** 以显示 " **MFC 应用程序向导**"。

1. 在 "**应用程序类型**" 窗格中, 选择 "**单个文档**"。 确保清除 "**文档/视图体系结构支持**" 复选框。

1. 单击 "**完成**" 以创建项目并关闭 " **MFC 应用程序向导**"。

   通过生成并运行该应用程序, 验证该应用程序是否已成功创建。 若要生成应用程序, 请在 "**生成**" 菜单上单击 "**生成解决方案**"。 如果应用程序成功生成, 则通过单击 "**调试**" 菜单上的 "**启动调试**" 来运行该应用程序。

##  <a name="serial"></a>实现 Mandelbrot 应用程序的串行版本

本部分介绍如何绘制 Mandelbrot 分形。 此版本将 Mandelbrot 分形绘制到 GDI +[位图](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)对象, 然后将该位图的内容复制到客户端窗口。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>实现 Mandelbrot 应用程序的串行版本

1. 在 stdafx.h 中, 添加以下`#include`指令:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. 在 ChildView 中的`pragma`指令后, `BitmapPtr`定义类型。 类型允许多个组件共享指向`Bitmap`对象的指针。 `BitmapPtr` 当`Bitmap`对象不再被任何组件引用时, 将删除该对象。

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. 在 ChildView 中, 将以下代码添加到`protected` `CChildView`类的部分:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. 在 ChildView 中, 注释掉或删除以下行。

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   在调试版本中, 此步骤阻止应用程序使用`DEBUG_NEW`与 gdi + 不兼容的分配器。

1. 在 ChildView 中, 将`using`指令添加`Gdiplus`到命名空间。

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 将下面的代码添加到`CChildView`类的构造函数和析构函数, 以初始化并关闭 gdi +。

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. 实现 `CChildView::DrawMandelbrot` 方法。 此方法将 Mandelbrot 分形绘制到指定`Bitmap`的对象。

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. 实现 `CChildView::OnPaint` 方法。 此方法调用`CChildView::DrawMandelbrot` , 然后将`Bitmap`对象的内容复制到窗口。

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. 通过生成并运行应用程序, 验证该应用程序是否已成功更新。

下图显示了 Mandelbrot 应用程序的结果。

![Mandelbrot 应用程序](../../parallel/concrt/media/mandelbrot.png "Mandelbrot 应用程序")

由于每个像素的计算消耗大量计算, 因此在整个计算结束之前, UI 线程无法处理其他消息。 这可能会降低应用程序的响应能力。 不过, 您可以通过从 UI 线程删除工作来缓解此问题。

[[返回页首](#top)]

##  <a name="removing-work"></a>从 UI 线程移除工作

本部分说明如何从 Mandelbrot 应用程序中的 UI 线程删除绘图工作。 通过将绘图工作从 UI 线程移到工作线程, UI 线程可以处理消息, 因为工作线程会在后台生成图像。

并发运行时提供了三种运行任务的方法:[任务组](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[异步代理](../../parallel/concrt/asynchronous-agents.md)和[轻量级任务](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 尽管可以使用这些机制中的任何一种从 UI 线程中删除工作, 但此示例使用[concurrency:: task_group](reference/task-group-class.md)对象, 因为任务组支持取消操作。 此演练稍后将使用取消来减少调整客户端窗口大小时执行的工作量, 并在销毁窗口时执行清理。

此示例还使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象, 使 UI 线程和工作线程能够彼此通信。 工作线程生成图像后, 它会将指向对象的指针`Bitmap`发送`unbounded_buffer`到对象, 然后将一个绘制消息发送到 UI 线程。 然后, UI 线程从`unbounded_buffer` `Bitmap`对象接收对象并将其绘制到客户端窗口。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>从 UI 线程删除绘图工作

1. 在 stdafx.h 中, 添加以下`#include`指令:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. 在 ChildView 中, 将和`task_group` `unbounded_buffer`成员变量添加`CChildView`到`protected`类的部分。 对象包含执行绘制的任务`unbounded_buffer` ; 对象包含已完成的 Mandelbrot 图像。 `task_group`

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. 在 ChildView 中, 将`using`指令添加`concurrency`到命名空间。

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. 在方法中, 在`Bitmap::UnlockBits`调用后, 调用`Bitmap` [concurrency:: send](reference/concurrency-namespace-functions.md#send)函数将对象传递给 UI 线程。 `CChildView::DrawMandelbrot` 然后将绘制消息发布到 UI 线程, 并使工作区无效。

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 更新方法以接收更新`Bitmap`的对象, 并将图像绘制到客户端窗口。 `CChildView::OnPaint`

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   如果消息缓冲区中不存在 Mandelbrot 映像,方法会创建一个任务来生成它。`CChildView::OnPaint` 消息缓冲区将不包含`Bitmap`对象, 如初始绘制消息和在客户端窗口之前移动另一个窗口时。

1. 通过生成并运行应用程序, 验证该应用程序是否已成功更新。

UI 现在可以更快地响应, 因为在后台执行绘图工作。

[[返回页首](#top)]

##  <a name="performance"></a>提高绘图性能

Mandelbrot 分形的生成非常适合用于并行化, 因为每个像素的计算都独立于所有其他计算。 若要并行执行绘制过程, 请将`for` `CChildView::DrawMandelbrot`方法中的外部循环转换为对[concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法的调用, 如下所示。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

由于每个 bitmap 元素的计算是独立的, 因此您不必同步访问位图内存的绘图操作。 这样可以提高性能, 因为可用处理器的数量会增加。

[[返回页首](#top)]

##  <a name="cancellation"></a>添加取消支持

本部分介绍如何处理窗口大小调整, 以及如何在销毁窗口时取消任何活动的绘制任务。

[PPL 中](cancellation-in-the-ppl.md)的文档取消说明了取消在运行时中的工作方式。 取消是协作性的;因此, 它不会立即发生。 若要停止取消的任务, 运行时在从任务到运行时的后续调用期间引发内部异常。 上一部分说明如何使用`parallel_for`算法来提高绘图任务的性能。 对`parallel_for`的调用使运行时能够停止任务, 从而使取消操作生效。

### <a name="cancelling-active-tasks"></a>正在取消活动任务

Mandelbrot 应用程序创建`Bitmap`其维度与客户端窗口大小匹配的对象。 每次调整客户端窗口大小时, 应用程序将创建一个额外的后台任务, 以生成新窗口大小的图像。 应用程序不需要这些中间映像;它只需要用于最终窗口大小的图像。 若要防止应用程序执行此额外的工作, 您可以取消`WM_SIZE`和`WM_SIZING`消息的消息处理程序中的任何活动绘图任务, 然后在调整窗口大小后重新计划绘图工作。

若要在调整窗口大小时取消活动的绘制任务, 应用程序将在`WM_SIZING`和`WM_SIZE`消息的处理程序中调用[concurrency:: task_group:: cancel](reference/task-group-class.md#cancel)方法。 `WM_SIZE`消息的处理程序还会调用[concurrency:: task_group:: wait](reference/task-group-class.md#wait)方法以等待所有活动任务完成, 然后重新为已更新的窗口大小重新安排绘制任务。

销毁客户端窗口时, 最好取消任何活动的绘制任务。 取消任何活动的绘制任务可确保工作线程在销毁客户端窗口之后不会将消息发布到 UI 线程。 应用程序取消`WM_DESTROY`消息的处理程序中的任何活动绘制任务。

### <a name="responding-to-cancellation"></a>响应取消

执行绘图任务的方法必须响应取消。`CChildView::DrawMandelbrot` 由于运行时使用异常处理来取消任务, 因此`CChildView::DrawMandelbrot`该方法必须使用异常安全机制来确保正确清理所有资源。 此示例使用*资源采集为初始化*(RAII) 模式, 以确保在取消任务时取消锁定位图位。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>在 Mandelbrot 应用程序中添加对取消的支持

1. 在 ChildView 中`protected` , 在`CChildView`类的节中, 添加`OnSize`、 `OnSizing`和`OnDestroy`消息映射函数的声明。

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. 在 ChildView 中, 将消息映射修改为包含`WM_SIZE`、 `WM_SIZING`和`WM_DESTROY`消息的处理程序。

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. 实现 `CChildView::OnSizing` 方法。 此方法取消任何现有的绘图任务。

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. 实现 `CChildView::OnSize` 方法。 此方法取消任何现有的绘图任务并为更新的客户端窗口大小创建一个新的绘制任务。

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. 实现 `CChildView::OnDestroy` 方法。 此方法取消任何现有的绘图任务。

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. 在 ChildView 中, 定义`scope_guard`用于实现 RAII 模式的类。

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 调用后, 将以下代码`CChildView::DrawMandelbrot`添加到方法: `Bitmap::LockBits`

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   此代码通过创建`scope_guard`对象来处理取消操作。 当对象离开作用域时, 它将解锁位图位。

1. 修改`CChildView::DrawMandelbrot`方法的末尾, 在`scope_guard`取消锁定位图位之后但在将任何消息发送到 UI 线程之前消除对象。 这可确保在取消锁定位图位之前, UI 线程不会更新。

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. 通过生成并运行应用程序, 验证该应用程序是否已成功更新。

调整窗口大小时, 只会对最终窗口大小执行绘图工作。 销毁窗口时, 还会取消任何活动的绘制任务。

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)
