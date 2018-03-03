---
title: "演练： 从用户界面线程中删除工作 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c32613aa6938b873a820fbb491fa2c507605a6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>演练：从用户界面线程中移除工作
本文档演示如何使用并发运行时移动的工作线程对 Microsoft 基础类 (MFC) 应用程序中的用户界面 (UI) 线程执行的工作。 本文档还演示如何提高长的绘制操作的性能。  
  
 通过将卸载的阻止操作，从 UI 线程中移除工作，例如，绘图，到工作线程可以提高你的应用程序的响应能力。 本演练使用生成 Mandelbrot 分形，来演示较长的阻止操作的绘制例程。 Mandelbrot 分形生成也是适合进行并行化，因为每个像素的计算是独立于所有其他计算。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前，请阅读以下主题：  
  
-   [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
-   [并行算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [PPL 中的取消操作](cancellation-in-the-ppl.md)  
  
 我们还建议你了解 MFC 应用程序开发的基础知识和[!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]在开始本演练之前。 有关 MFC 的详细信息，请参阅[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)。 有关详细信息[!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]，请参阅[GDI +](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533798)。  
  
##  <a name="top"></a> 部分  
 本演练包含以下各节：  
  
-   [创建 MFC 应用程序](#application)  
  
-   [实现 Mandelbrot 应用程序的序列化版本](#serial)  
  
-   [从用户界面线程中移除工作](#removing-work)  
  
-   [提高绘制性能](#performance)  
  
-   [添加对取消的支持](#cancellation)  
  
##  <a name="application"></a>创建 MFC 应用程序  
 本部分介绍如何创建基本的 MFC 应用程序。  
  
### <a name="to-create-a-visual-c-mfc-application"></a>创建 Visual c + + MFC 应用程序  
  
1.  在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
2.  在**新项目**对话框中，在**已安装的模板**窗格中，选择**Visual c + +**，然后在**模板**窗格中，选择**MFC 应用程序**。 为项目键入名称，例如， `Mandelbrot`，然后单击**确定**以显示**MFC 应用程序向导**。  
  
3.  在**应用程序类型**窗格中，选择**单个文档**。 确保**文档/视图体系结构支持**清除复选框。  
  
4.  单击**完成**以创建项目并关闭**MFC 应用程序向导**。  
  
     验证应用程序已成功创建，可以通过生成并运行它。 若要生成该应用程序，在**生成**菜单上，单击**生成解决方案**。 如果成功生成了应用程序，通过单击运行该应用程序**启动调试**上**调试**菜单。  
  
##  <a name="serial"></a>实现 Mandelbrot 应用程序的序列化版本  
 本部分介绍如何绘制 Mandelbrot 分形。 此版本绘制到 Mandelbrot 分形[!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)][位图](https://msdn.microsoft.com/library/ms534420.aspx)对象，然后将该位图的内容复制到客户端窗口。  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>若要实现 Mandelbrot 应用程序的序列化版本  
  
1.  在 stdafx.h 文件中，添加以下`#include`指令：  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  在 ChildView.h 后,`pragma`指令，定义`BitmapPtr`类型。 `BitmapPtr`类型可让指向的指针`Bitmap`要由多个组件共享的对象。 `Bitmap`不再被引用的任何组件时删除对象。  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  在 ChildView.h，添加以下代码到`protected`部分`CChildView`类：  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  在 ChildView.cpp，注释掉或删除以下行。  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     在调试版本中，此步骤会阻止应用程序使用`DEBUG_NEW`与不兼容的分配器[!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]。  
  
5.  在 ChildView.cpp，添加`using`指令至`Gdiplus`命名空间。  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  将以下代码添加到的构造函数和析构函数`CChildView`类来初始化和关闭[!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]。  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  实现 `CChildView::DrawMandelbrot` 方法。 此方法为指定绘制 Mandelbrot 分形`Bitmap`对象。  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  实现 `CChildView::OnPaint` 方法。 此方法调用`CChildView::DrawMandelbrot`，然后将复制的内容`Bitmap`到窗口的对象。  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. 验证应用程序已成功更新，可以通过生成并运行它。  
  
 下图显示 Mandelbrot 应用程序的结果。  
  
 ![Mandelbrot 应用程序](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 由于计算每个像素是计算开销很大，UI 线程无法处理其他消息，直到整体计算完成。 这会降低应用程序中的响应能力。 但是，你可以通过从 UI 线程中移除工作来缓解此问题。  
  
 [[返回页首](#top)]  
  
##  <a name="removing-work"></a>从 UI 线程中移除工作  
 本部分演示如何从 Mandelbrot 应用程序中的 UI 线程中移除绘图的工作。 通过将从 UI 线程的绘制工作移到辅助线程中，UI 线程可以处理消息，工作线程在后台生成映像。  
  
 并发运行时提供三种方法运行任务：[任务组](../../parallel/concrt/task-parallelism-concurrency-runtime.md)，[异步代理](../../parallel/concrt/asynchronous-agents.md)，和[轻量级任务](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 你可以使用任何一种机制从 UI 线程中移除工作，但此示例使用[concurrency:: task_group](reference/task-group-class.md)对象，因为任务组支持取消。 本演练更高版本使用取消，减少客户端窗口调整大小时，执行工作的同时销毁窗口时执行清理。  
  
 此示例还使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象，以允许 UI 线程和辅助线程相互通信。 工作线程生成的图像后，它将发送到指针`Bitmap`对象传递给`unbounded_buffer`对象，然后将对 UI 线程绘制消息。 UI 线程然后接收来自`unbounded_buffer`对象`Bitmap`对象，并将其绘制到客户端窗口。  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>从 UI 线程中移除绘图工作  
  
1.  在 stdafx.h 文件中，添加以下`#include`指令：  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  在 ChildView.h，添加`task_group`和`unbounded_buffer`到成员变量`protected`部分`CChildView`类。 `task_group`对象保存执行绘制; 的任务`unbounded_buffer`对象保存已完成的 Mandelbrot 映像。  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  在 ChildView.cpp，添加`using`指令至`concurrency`命名空间。  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  在`CChildView::DrawMandelbrot`方法，在调用后的`Bitmap::UnlockBits`，调用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数传递`Bitmap`对 UI 线程的对象。 然后将绘制消息发布到 UI 线程并使工作区无效。  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  更新`CChildView::OnPaint`方法来接收更新`Bitmap`对象，并在客户端窗口中绘制图像。  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     `CChildView::OnPaint`方法创建如果不存在的消息缓冲区中生成 Mandelbrot 映像的任务。 将不包含的消息缓冲区`Bitmap`在情况下，如初始绘制消息和另一个窗口移动客户端窗口的前面的对象。  
  
6.  验证应用程序已成功更新，可以通过生成并运行它。  
  
 UI 功能现在更快地响应，因为在后台执行绘制工作。  
  
 [[返回页首](#top)]  
  
##  <a name="performance"></a>提高绘制性能  

 Mandelbrot 分形生成是很适合并行化，因为每个像素的计算是独立于所有其他计算。 若要并行化绘制过程，将转换外部`for`循环中`CChildView::DrawMandelbrot`方法的调用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法，如下所示。  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 因为每个位图元素的计算是独立的你不需要同步访问的位图内存的绘制操作。 这样，性能将随可用的处理器增加的数量。  
  
 [[返回页首](#top)]  
  
##  <a name="cancellation"></a>添加对取消的支持  
 本部分介绍如何处理重设窗口大小以及如何销毁窗口时取消任何活动的绘制任务。  
  
 文档[PPL 中的取消](cancellation-in-the-ppl.md)说明取消如何在运行时配合工作。 取消是协作性;因此，它不会立即发生。 若要停止已取消的任务，则运行时会引发运行时期间从任务的后续调用出现内部异常。 上一节演示如何使用`parallel_for`算法提高绘制任务的性能。 调用`parallel_for`，运行时将停止该任务，并因此使取消操作起作用。  
  
### <a name="cancelling-active-tasks"></a>取消活动任务  
 Mandelbrot 应用程序创建`Bitmap`的维度与客户端窗口的大小匹配的对象。 每次客户端窗口的大小调整，应用程序创建一项额外的后台任务生成新的窗口大小的映像。 应用程序不需要这些中间的图像。针对最终的窗口大小，它需要唯一的映像。 若要防止应用程序中执行这一附加工作，您可以取消任何活动的绘制任务的消息处理程序中`WM_SIZE`和`WM_SIZING`后调整窗口大小时，然后重新计划绘制和消息将起作用。  
  
 若要调整窗口大小时，请取消活动的绘制任务，在应用程序调用[concurrency::task_group::cancel](reference/task-group-class.md#cancel)中的处理程序方法`WM_SIZING`和`WM_SIZE`消息。 处理程序`WM_SIZE`消息还调用[concurrency::task_group::wait](reference/task-group-class.md#wait)方法以等待所有活动任务完成，然后重新计划绘制任务的更新后的窗口大小。  
  
 客户端窗口销毁时，它是好的做法，以取消任何活动的图形任务。 取消任何活动的绘制任务可以确保工作线程在客户端窗口已销毁之后不会发布到 UI 线程的消息。 应用程序将取消任何活动的绘制任务的处理程序中`WM_DESTROY`消息。  
  
### <a name="responding-to-cancellation"></a>响应取消操作  
 `CChildView::DrawMandelbrot`方法，用于执行绘制任务，必须响应取消。 运行时使用异常处理来取消任务，因为`CChildView::DrawMandelbrot`方法必须使用异常安全机制来保证，所有资源被正确清理。 此示例使用*获取资源即初始化*(RAII) 模式，以保证在该任务被取消时不锁定位图位。  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Mandelbrot 应用程序在添加取消的支持  
  
1.  在 ChildView.h，在`protected`部分`CChildView`类中，添加声明`OnSize`， `OnSizing`，和`OnDestroy`消息映射函数。  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  在 ChildView.cpp，修改要包含的处理程序的消息映射`WM_SIZE`， `WM_SIZING`，和`WM_DESTROY`消息。  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  实现 `CChildView::OnSizing` 方法。 此方法用于取消任何现有绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  实现 `CChildView::OnSize` 方法。 此方法取消任何现有绘制任务，并创建新的更新的客户端窗口大小绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  实现 `CChildView::OnDestroy` 方法。 此方法用于取消任何现有绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  在 ChildView.cpp，定义`scope_guard`类，该类实现 RAII 模式。  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  以下代码添加到`CChildView::DrawMandelbrot`方法之后调用`Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     此代码通过创建处理取消`scope_guard`对象。 当对象离开范围时，它将解锁位图位。  
  
8.  修改的末尾`CChildView::DrawMandelbrot`方法以取消`scope_guard`对象不锁定，位图位之后但在任何消息发送到 UI 线程之前。 这可确保不锁定位图位之前不会更新 UI 线程。  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. 验证应用程序已成功更新，可以通过生成并运行它。  
  
 当您调整窗口大小时，绘制工作将执行仅针对最终的窗口大小。 销毁窗口时，还会取消任何活动的图形任务。  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)
