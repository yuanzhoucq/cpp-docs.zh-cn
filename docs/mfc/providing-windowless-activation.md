---
title: "提供无窗口激活 | Microsoft Docs"
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
  - "激活 [C++], MFC ActiveX 控件"
  - "激活 [C++], 无窗口"
  - "MFC ActiveX 控件 [C++], 激活选项"
  - "MFC ActiveX 控件的无窗口激活"
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 提供无窗口激活
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

窗口发生的代码创建 \(即内容，当您调用 **CreateWindow**\) 需要不少开销的执行。  维护一屏上的窗口控件必须管理窗口的消息。  由于无窗口控件比使用 Windows 的控件快。  
  
 无窗口控件的一个好处是后期，不同个控件，无窗口控件支持透明和绘制矩形屏幕区域。  一个透明控件的一个常见示例是具有背景透明的文本控件。  控件绘制文本，但是不是后台，因此，内容将在文本查看下。  更通常利用新的窗体控件，例如矩形和圆箭头按钮。  
  
 通常，容器支持无窗口的对象，然后编写条件下，控件不需要自己的窗口，并且，相反，不能使用其容器 Windows 服务。  无窗口控件与的早期容器向后兼容。  在编写的旧容器支持无窗口控件，无窗口控件激活。创建窗口，  
  
 由于无窗口控件没有其窗口，因此具有一个窗口 \(\) 的容器。提供控件的窗口原本提供的服务负责。  例如，在中，如果控件要求查询键盘焦点，捕获鼠标或获取设备上下文，这些操作。管理容器。  容器将用户输入发送到它对相应的无窗口控件中，`IOleInPlaceObjectWindowless` 接口使用。\(为此接口的说明，请参见 *ActiveX SDK* 。\) `COleControl` 成员函数调用从容器的这些服务。  
  
 若要使控件使用无窗口激活的，包括 **windowlessActivate** 标志。标志集由 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)返回。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/CPP/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-windowless-activation_3.cpp)]  
  
 如果您在 MFC ActiveX 控件向导的 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页，**无窗口激活 \(S\)** 选项可将此标记的代码自动生成。  
  
 当无窗口激活的启用，容器将输入委托消息给控件的 `IOleInPlaceObjectWindowless` 接口。   的`COleControl` 实现通过控件的消息映射调度消息。相应调整鼠标坐之后。  可以通过将添加相应的项处理消息像操作普通窗口消息至消息映射。  在这些消息的处理程序，应避免使用 `m_hWnd` 成员变量 \(或使用它\) 的任何成员函数，但其值不是首先检查 **NULL**的。  
  
 提供调用`COleControl` 获取键盘、鼠标、焦点和滚动其他 Windows 服务从容器为适当的成员函数，包括：  
  
-   [GetFocus](../Topic/COleControl::GetFocus.md)，[SetFocus](../Topic/COleControl::SetFocus.md)  
  
-   [GetCapture](../Topic/COleControl::GetCapture.md)，[SetCapture](../Topic/COleControl::SetCapture.md)，[ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)  
  
-   [GetDC](../Topic/COleControl::GetDC.md)，[ReleaseDC](../Topic/COleControl::ReleaseDC.md)  
  
-   [InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)  
  
-   [ScrollWindow](../Topic/COleControl::ScrollWindow.md)  
  
-   [GetClientRect](../Topic/COleControl::GetClientRect.md)  
  
 在无窗口控件，则应该总是使用 `COleControl` 成员函数代替对应的 `CWnd` 成员函数或相关的 Win32 API 函数。  
  
 可以无窗口控件是一个 OLE 拖放操作的目标。  通常，这需要控制 Windows 注册，放置目标。  因为控件具有自己中，容器使用自己的窗口，如果放置目标。  控件提供容器可以在委托调用 `IDropTarget` 接口的实现。  公开此接口。容器，将 [COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md)。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/CPP/providing-windowless-activation_4.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)