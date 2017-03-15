---
title: "MFC ActiveX 控件：优化 | Microsoft Docs"
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
  - "设备上下文, 对于 MFC ActiveX 控件未剪辑"
  - "无闪烁 ActiveX 控件"
  - "MFC ActiveX 控件, 活动/非活动状态"
  - "MFC ActiveX 控件, 无闪烁"
  - "MFC ActiveX 控件, 鼠标交互"
  - "MFC ActiveX 控件, 优化"
  - "MFC ActiveX 控件, 无窗口"
  - "优化, ActiveX 控件"
  - "优化性能, ActiveX 控件"
  - "性能, ActiveX 控件"
  - "无窗口 MFC ActiveX 控件"
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# MFC ActiveX 控件：优化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明您可以使用微调性能更佳的 ActiveX 控件的技术。  
  
 主题 [关闭活动，如果可见选项](../mfc/turning-off-the-activate-when-visible-option.md) 和 [提供鼠标交互，在不活动状态时](../mfc/providing-mouse-interaction-while-inactive.md) 讨论创建之前不激活的窗口的控件。  主题 [提供未激活的窗口](../mfc/providing-windowless-activation.md) 讨论都创建窗口的控件，即使其激活。  
  
 窗口具有 OLE 对象的两个主要的缺点：，当激活和这些添加一大开销到控件时进行实例化，并显示它们以防止对象透明或矩形。  通常，创建窗口需要 60 的控件的创建时间。  单个共享窗口 \(通常容器的\) 和某调度的代码同样，控件包含 Windows 服务，通常，不会对性能损失。  有窗口的主要对象是不必要的系统开销。  
  
 控件时，在某些容器时，这些优化不必须提高性能。  例如，在 1996 之前释放的容器不支持无窗口激活的，实现，因此此功能不会提供较早的容器的一个优点。  但是，的每个容器支持持久性，应使用，因而优化控件进行保持代码可能会提高其在所有容器的性能。  如果控件容器使用专用于特定类型，您可能希望搞清楚哪些优化由容器支持。  但是，通常，您应当尝试实现许多技术与对应于特定控件确保控件自身运行良好，以便在大多数容器可以。  
  
 您可以通过 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)实现许多优化，在 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页。  
  
### MFC ActiveX 控件向导 OLE 优化选项  
  
|控制在 MFC ActiveX 控件向导的设置|操作|更多信息|  
|-----------------------------|--------|----------|  
|**Activate when visible** 复选框|Clear|[关闭“可见时激活”选项](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**无窗口激活 \(S\)** 复选框|选择|[提供无窗口激活](../mfc/providing-windowless-activation.md)|  
|**未剪辑的设备上下文 \(U\)** 复选框|选择|[使用未剪辑的设备上下文](../mfc/using-an-unclipped-device-context.md)|  
|**无闪烁激活 \(V\)** 复选框|选择|[提供无闪烁激活](../mfc/providing-flicker-free-activation.md)|  
|**不活动时有鼠标指针通知**|选择|[不活动时提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**优化的绘图代码 \(P\)** 复选框|选择|[优化控件绘制](../mfc/optimizing-control-drawing.md)|  
  
 有关成员的详细信息函数实现这些优化，请参见 [COleControl](../mfc/reference/colecontrol-class.md)。  成员函数是使用列表，如 [无窗口操作。](http://msdn.microsoft.com/zh-cn/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) 和 [处理函数指针的非活动状态](http://msdn.microsoft.com/zh-cn/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)。  
  
 有关详细信息，请参阅：  
  
-   [优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [提供无窗口激活](../mfc/providing-windowless-activation.md)  
  
-   [关闭“可见时激活”选项](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [不活动时提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [提供无闪烁激活](../mfc/providing-flicker-free-activation.md)  
  
-   [使用未剪辑的设备上下文](../mfc/using-an-unclipped-device-context.md)  
  
-   [优化控件绘制](../mfc/optimizing-control-drawing.md)  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)