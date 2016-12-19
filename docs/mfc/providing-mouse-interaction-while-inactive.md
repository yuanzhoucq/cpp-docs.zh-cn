---
title: "不活动时提供鼠标交互 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件, 鼠标交互"
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 不活动时提供鼠标交互
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果控件并未立即激活，您可能仍在处理 `WM_SETCURSOR` 和 `WM_MOUSEMOVE` 消息，即使控件，没有自己的窗口。  可以通过启用 `IPointerInactive` 接口的 `COleControl` 实现来完成，默认情况下将禁用。\(为此接口的说明，请参见 *ActiveX SDK* 。\)若要启用该身份，包含在组的 `pointerInactive` 标志。[COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)返回：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 为包含此标记的代码自动生成，则选择 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页中的 **不活动时有鼠标指针通知 \(M\)** 选项，当创建具有 **MFC ActiveX 控件向导**时控件。  
  
 在 `IPointerInactive` 接口启用时，容器将 `WM_SETCURSOR` 和 `WM_MOUSEMOVE` 消息。它。  `IPointerInactive` 的`COleControl` 实现通过控件的消息映射调度消息。相应调整鼠标坐之后。  可以通过将添加相应的项处理消息像操作普通窗口消息至消息映射。  在这些消息的处理程序，应避免使用 `m_hWnd` 成员变量 \(或使用它\) 的任何成员函数，但其值不是首先检查 **NULL**的。  
  
 也可以为非活动控件一个 OLE 拖放操作的目标。  这需要激活控件，在用户拖动上方时的对象，因此，控制窗口来注册作为放置目标。  在拖动，重写 [COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md)中，导致出现激活并返回 **POINTERINACTIVE\_ACTIVATEONDRAG** 标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 启用 `IPointerInactive` 接口通常意味着要控件能够始终处理鼠标消息。  为了在不支持 `IPointerInactive` 接口的容器的此行为，则需要有一些始终激活的控件，并且在状态，表示控件应包括在其混合标志中 **OLEMISC\_ACTIVATEWHENVISIBLE** 标志。  但是，为了防止此标志仅在支持 `IPointerInactive`的容器，还可以指定 **OLEMISC\_IGNOREACTIVATEWHENVISIBLE** 标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/CPP/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)