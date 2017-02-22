---
title: "演练：从用户界面线程中移除工作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "从用户界面线程中移除工作 [并发运行时]"
  - "用户界面线程, 移除工作 [并发运行时]"
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 演练：从用户界面线程中移除工作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档演示如何使用并发运行时将 Microsoft 基础类 \(MFC\) 应用程序中的用户界面 \(UI\) 线程所执行的工作移到辅助线程。  本文档还演示如何提高长时间绘制操作的性能。  
  
 通过将阻塞操作（例如绘制操作）卸载到辅助线程，从 UI 线程中移除工作，可以提高应用程序的响应能力。  本演练使用可生成 Mandelbrot 分形的绘制例程来演示长时间的阻塞操作。  生成 Mandelbrot 分形也很适合于并行化，因为每个像素的计算都独立于所有其他计算。  
  
## 系统必备  
 在开始本演练之前，请阅读下列主题：  
  
-   [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
-   [并行算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [取消](../../parallel/concrt/cancellation-in-the-ppl.md)  
  
 此外，建议您在开始本演练之前，先了解 MFC 应用程序开发和 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的基础知识。  有关 MFC 的更多信息，请参见 [MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)。  有关 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的更多信息，请参见 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
##  <a name="top"></a> 各节内容  
 本演练包含以下各节：  
  
-   [创建 MFC 应用程序](#application)  
  
-   [实现 Mandelbrot 应用程序的序列化版本](#serial)  
  
-   [从用户界面线程中移除工作](#removing-work)  
  
-   [提高绘制性能](#performance)  
  
-   [添加取消支持](#cancellation)  
  
##  <a name="application"></a> 创建 MFC 应用程序  
 本节描述如何创建基本 MFC 应用程序。  
  
### 创建 Visual C\+\+ MFC 应用程序  
  
1.  在**“文件”**菜单上单击**“新建”**，再单击**“项目”**。  
  
2.  在**“新建项目”**对话框的**“已安装的模板”**窗格中，选择**“Visual C\+\+”**，然后在**“模板”**窗格中选择**“MFC 应用程序”**。  为项目键入名称（例如 `Mandelbrot`），然后单击**“确定”**以显示**“MFC 应用程序向导”**。  
  
3.  在**“应用程序类型”**窗格中选择**“单个文档”**。  确保清除**“文档\/视图结构支持”**复选框。  
  
4.  单击**“完成”**以创建项目，然后关闭**“MFC 应用程序向导”**。  
  
     通过生成并运行应用程序来验证该应用程序已成功创建。  若要生成应用程序，请在**“生成”**菜单上单击**“生成解决方案”**。  如果成功生成了该应用程序，请单击**“调试”**菜单上的**“开始调试”**来运行该应用程序。  
  
##  <a name="serial"></a> 实现 Mandelbrot 应用程序的序列化版本  
 本节说明如何绘制 Mandelbrot 分形。  此版本向 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [Bitmap](https://msdn.microsoft.com/en-us/library/ms534420.aspx) 对象绘制 Mandelbrot 分形，然后将此位图的内容复制到客户端窗口中。  
  
#### 实现 Mandelbrot 应用程序的序列化版本  
  
1.  在 stdafx.h 中，添加以下 `#include` 指令：  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  在 ChildView.h 中，在 `pragma` 指令后面定义 `BitmapPtr` 类型。  `BitmapPtr` 类型允许多个组件共享指向 `Bitmap` 对象的指针。  当 `Bitmap` 对象不再由任何组件引用时，删除此对象。  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  在 ChildView.h 中，将以下代码添加到 `CChildView` 类的 `protected` 部分中：  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  在 ChildView.cpp 中，注释掉或移除以下行。  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     在调试版本中，此步骤可阻止应用程序使用与 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 不兼容的 `DEBUG_NEW` 分配器。  
  
5.  在 ChildView.cpp 中，将 `using` 指令添加到 `Gdiplus` 命名空间。  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  将以下代码添加到 `CChildView` 类的构造函数和析构函数中以初始化并关闭 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]。  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  实现 `CChildView::DrawMandelbrot` 方法。  此方法向指定的 `Bitmap` 对象绘制 Mandelbrot 分形。  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  实现 `CChildView::OnPaint` 方法。  此方法调用 `CChildView::DrawMandelbrot`，然后将 `Bitmap` 对象的内容复制到此窗口中。  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. 通过生成并运行应用程序来验证应用程序是否已成功更新。  
  
 下图演示 Mandelbrot 应用程序的结果。  
  
 ![Mandelbrot 应用程序](../Image/Mandelbrot.png "Mandelbrot")  
  
 由于计算每个像素要消耗大量的计算资源，因此在整体计算完成之前，UI 线程无法处理其他消息。  这会降低应用程序的响应能力。  但是，您可以通过从 UI 线程中移除工作来缓解此问题。  
  
 \[[Top](#top)\]  
  
##  <a name="removing-work"></a> 从 UI 线程中移除工作  
 本节演示如何从 Mandelbrot 应用程序的 UI 线程中移除绘制工作。  将绘制工作从 UI 线程移动到辅助线程后，辅助线程在后台生成图像，同时 UI 线程可以处理消息。  
  
 并发运行时提供三种运行任务的方式：[任务组](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[异步代理](../../parallel/concrt/asynchronous-agents.md)和[轻量级任务](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  尽管可以使用其中任一种方式从 UI 线程中移除工作，但因为任务组支持取消机制，所以此示例使用了 [concurrency::task\_group](../Topic/task_group%20Class.md) 对象。  本演练稍后将使用取消功能，以便在调整客户端窗口大小时减少所执行的工作量，并在窗口销毁时执行清理工作。  
  
 此示例还使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 对象，以允许 UI 线程和辅助线程相互通信。  辅助线程在产生图像后将一个指向 `Bitmap` 对象的指针发送到 `unbounded_buffer` 对象，然后将一条绘制消息发送给 UI 线程。  接着，UI 线程将从 `unbounded_buffer` 对象接收 `Bitmap` 对象，并将该对象绘制到客户端窗口。  
  
#### 从 UI 线程中移除绘制工作  
  
1.  在 stdafx.h 中，添加以下 `#include` 指令：  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  在 ChildView.h 中，将 `task_group` 和 `unbounded_buffer` 成员变量添加到 `CChildView` 类的 `protected` 部分。  `task_group` 对象保留执行绘制的任务；`unbounded_buffer` 对象保留已完成的 Mandelbrot 图像。  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  在 ChildView.cpp 中，将 `using` 指令添加到 `concurrency` 命名空间。  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  
4.  在 `CChildView::DrawMandelbrot` 方法中，在调用 `Bitmap::UnlockBits` 之后，调用 [concurrency::send](../Topic/send%20Function.md) 函数以将 `Bitmap` 对象传递给 UI 线程。  然后，将绘制消息发送到 UI 线程并使工作区无效。  
  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  更新 `CChildView::OnPaint` 方法以接收已更新的 `Bitmap` 对象并在客户端窗口中绘制图像。  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     如果消息缓冲区中不存在 Mandelbrot 图像，`CChildView::OnPaint` 方法将创建一个任务来生成 Mandelbrot 图像。  对于初始绘制消息和另一个窗口移到客户端窗口前面的情况，消息缓冲区中将不包含 `Bitmap` 对象。  
  
6.  通过生成并运行应用程序来验证应用程序是否已成功更新。  
  
 现在，UI 线程能够更快地响应，因为绘制工作在后台执行。  
  
 \[[Top](#top)\]  
  
##  <a name="performance"></a> 提高绘制性能  
 生成 Mandelbrot 分形很适合于并行化，因为每个像素的计算都独立于所有其他计算。  若要并行化绘制过程，请将 `CChildView::DrawMandelbrot` 方法中的外部 `for` 循环转换为调用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法，如下所示。  
  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 因为每个位图元素的计算都是独立的，所以您不必同步访问位图内存的绘制操作。  这样，性能将随可用处理器数的增加而进行调整。  
  
 \[[Top](#top)\]  
  
##  <a name="cancellation"></a> 添加取消支持  
 本节描述如何调整窗口大小，以及如何在窗口销毁时取消任何活动的绘制任务。  
  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)文档解释取消操作如何在运行时中工作。  取消是协作性的操作；因此，它不会立即发生。  若要停止已取消的任务，则在从任务中对运行时进行后续调用期间，运行时将引发内部异常。  上一节演示了如何使用 `parallel_for` 算法提高绘制任务的性能。  调用 `parallel_for` 后运行时将能够停止任务，并因此使取消操作起作用。  
  
### 取消活动任务  
 Mandelbrot 应用程序将创建其维度与客户端窗口大小匹配的 `Bitmap` 对象。  每次调整客户端窗口大小时，此应用程序都会另外创建一个后台任务，以便针对新的窗口大小生成图像。  此应用程序不需要这些中间图像，而只需要针对最终窗口大小的图像。  若要阻止此应用程序执行这一附加工作，您可以取消 `WM_SIZE` 和 `WM_SIZING` 消息的消息处理程序中的任何活动的绘制任务，然后在调整窗口大小之后重新计划绘制工作。  
  
 若要在调整窗口大小时取消活动的绘制任务，则此应用程序将在 `WM_SIZING` 和 `WM_SIZE` 消息的处理程序中调用 [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) 方法。  `WM_SIZE` 消息的处理程序还将调用 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md) 方法以等待所有活动任务完成，然后针对更新后的窗口大小重新计划绘制任务。  
  
 当客户端窗口销毁时，最好取消任何活动的绘制任务。  取消任何活动的绘制任务可确保在客户端窗口销毁后，辅助线程不会向 UI 线程发送消息。  此应用程序将取消 `WM_DESTROY` 消息的处理程序中的任何活动的绘制任务。  
  
### 响应取消操作  
 执行绘制任务的 `CChildView::DrawMandelbrot` 方法必须对取消操作做出响应。  因为运行时使用异常处理来取消任务，所以 `CChildView::DrawMandelbrot` 方法必须使用异常安全机制来保证正确清理所有资源。  此示例使用“获取资源即初始化”\(RAII\) 模式来保证在取消任务时不锁定位图位。  
  
##### 在 Mandelbrot 应用程序中添加取消支持  
  
1.  在 ChildView.h 中，在 `CChildView` 类的 `protected` 部分，为 `OnSize`、`OnSizing` 和 `OnDestroy` 消息映射函数添加声明。  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  在 ChildView.cpp 中，修改消息映射以包含 `WM_SIZE`、`WM_SIZING` 和 `WM_DESTROY` 消息的处理程序。  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  实现 `CChildView::OnSizing` 方法。  此方法取消任何现有绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  实现 `CChildView::OnSize` 方法。  此方法取消任何现有绘制任务，并针对更新后的客户端窗口大小创建一个新的绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  实现 `CChildView::OnDestroy` 方法。  此方法取消任何现有绘制任务。  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  在 ChildView.cpp 中，定义实现 RAII 模式的 `scope_guard` 类。  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  在调用 `Bitmap::LockBits` 之后，将以下代码添加到 `CChildView::DrawMandelbrot` 方法：  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     此代码通过创建 `scope_guard` 对象处理取消操作。  当该对象离开范围时，它将取消锁定位图位。  
  
8.  修改 `CChildView::DrawMandelbrot` 方法的结尾，以便在取消锁定位图位之后、发送任何消息到 UI 线程之前关闭 `scope_guard` 对象。  这样可确保在取消锁定位图位之前不会更新 UI 线程。  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. 通过生成并运行应用程序来验证应用程序是否已成功更新。  
  
 当调整窗口的大小时，仅针对最终窗口大小执行绘制工作。  当窗口销毁时，也将取消任何活动的绘制任务。  
  
 \[[Top](#top)\]  
  
## 请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)