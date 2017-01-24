---
title: "从公共控件接收通知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "公共控件 [C++], 通知"
  - "控件 [MFC], 通知"
  - "通知, 公共控件"
  - "ON_NOTIFY 宏"
  - "OnNotify 方法"
  - "从公共控件接收通知"
  - "Windows 公共控件 [C++], 通知"
  - "WM_NOTIFY 消息"
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从公共控件接收通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

公共控件发送通知消息到父窗口的子窗口，当事件在控件时发生，例如，来自用户输入。  
  
 应用程序依赖于这些通知消息确定操作用户希望它采用。  多数普通控制发送通知消息。**WM\_NOTIFY** 消息。  Windows 会路由大多数控件通知消息如**WM\_COMMAND** 消息。  [CWnd::OnNotify](../Topic/CWnd::OnNotify.md) 是 **WM\_NOTIFY** 消息的处理程序。  与 `CWnd::OnCommand`相同，`OnNotify` 的实现将处理 `OnCmdMsg` 消息映射。在通知消息。  处理的控件通知消息映射项为 `ON_NOTIFY`。  有关更多信息，请参见 [技术说明 61:ON\_NOTIFY 和 WM\_NOTIFY 消息](../mfc/tn061-on-notify-and-wm-notify-messages.md)。  
  
 此外，派生类可以处理其自己的控件通知消息使用反映“消息”。有关更多信息，请参见 [技术说明 62:反射消息窗口的控件](../mfc/tn062-message-reflection-for-windows-controls.md)。  
  
## 检索在通知消息的位置光标  
 有时，在某些通知消息由普通控制时，将获得光标的当前位置很有用。  例如，在中，当一个常用控件接收 **NM\_RCLICK** 通知消息时，确定当前光标位置很有用。  
  
 具有单个方法可以调用 `CWnd::GetCurrentMessage`来实现。  但是，在这种情况下，发送消息时，该方法仅检索光标位置。  由于能移动光标，因为信息已发送您必须调用 **CWnd::GetCursorPos** 来获取当前光标位置。  
  
> [!NOTE]
>  应只在消息处理程序中调用`CWnd::GetCurrentMessage`。  
  
 将以下代码添加到消息通知处理程序的主体 \(在此例中，**NM\_RCLICK**\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/CPP/receiving-notification-from-common-controls_1.cpp)]  
  
 此时，鼠标光标位置存储在 `cursorPos` 对象中。  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)