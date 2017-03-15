---
title: "Windows 中不是从 CFrameWnd 派生的工具提示 | Microsoft Docs"
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
  - "控件 [MFC], 工具提示"
  - "启用工具提示"
  - "处理函数, 工具提示"
  - "帮助, 控件的工具提示"
  - "TOOLTIPTEXT 结构"
  - "TTN_NEEDTEXT 消息"
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Windows 中不是从 CFrameWnd 派生的工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文系列包括以从 [CFrameWnd](../mfc/reference/cframewnd-class.md)未派生的窗口包含的控件的工具提示。  文章 [工具栏工具提示](../mfc/toolbar-tool-tips.md) 为 `CFrameWnd`控件提供有关工具提示的信息。  
  
 本文系列包括的主题包括：  
  
-   [启用工具提示](../mfc/enabling-tool-tips.md)  
  
-   [处理工具提示的 TTN\_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)  
  
 工具提示用于在父窗口及其他控件自动显示包含的按钮从 `CFrameWnd`派生。  这是因为，`CFrameWnd` 已将 [TTN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) 通知的默认处理程序，处理与工具提示控件的 **TTN\_NEEDTEXT** 通知与控件关联。  
  
 但是，该默认处理程序不调用，当 **TTN\_NEEDTEXT** 通知从工具提示控件发送与不是 `CFrameWnd`时将窗口的控件，例如或在对话框窗体视图的控件。  因此，对于 **TTN\_NEEDTEXT** 通知消息提供处理程序函数来显示子控件的工具提示。是必需的。  
  
 为窗口的默认提供工具提示。[CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md) 没有文本与它们关联。  在工具提示窗口显示之前，若要检索工具提示的文本查看，**TTN\_NEEDTEXT** 通知发送到工具提示控件的父窗口。  如果未出现此消息的处理程序可以将某些值为 **TOOLTIPTEXT** 结构的 **pszText** 成员中，都没有为工具提示显示的文本。  
  
## 请参阅  
 [工具提示](../mfc/tool-tips.md)