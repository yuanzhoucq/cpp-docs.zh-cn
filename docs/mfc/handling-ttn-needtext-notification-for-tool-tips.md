---
title: "处理工具提示的 TTN_NEEDTEXT 通知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TTN_NEEDTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通知, 工具提示"
  - "工具提示 [C++], 通知"
  - "TTN_NEEDTEXT 消息"
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 处理工具提示的 TTN_NEEDTEXT 通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 [启用工具提示](../mfc/enabling-tool-tips.md)一部分，通过添加下面输入处理 **TTN\_NEEDTEXT** 消息至所有者窗口的消息映射：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 要调用的，当文本用于此按钮所需的成员函数。  
  
 请注意工具提示的 ID 始终为 0。  
  
 声明类中定义的函数处理程序如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 在斜体的参数：  
  
 `id`  
 发送通知控件的标识符。  未使用。  控件 ID 从 **NMHDR** 结构的操作。  
  
 `pNMHDR`  
 到 [NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258) 结构的指针。  此结构中还进一步讨论。[TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)  
  
 `pResult`  
 结果指针可以设置的代码，在返回之前。  **TTN\_NEEDTEXT** 处理程序可以忽略 `pResult` 参数。  
  
 作为窗体视图通知处理程序：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 调用 `EnableToolTips` \(从 `OnInitDialog`采取的此段\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## 请参阅  
 [Windows 中不是从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)