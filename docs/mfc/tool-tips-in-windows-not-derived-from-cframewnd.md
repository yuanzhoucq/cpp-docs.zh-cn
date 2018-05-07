---
title: 不是从 CFrameWnd 派生的 Windows 中的工具提示 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34eb8f0b7394828782a3d0f9ed1ca44fb5731af6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Windows 中不是从 CFrameWnd 派生的工具提示
本文章系列介绍的不派生自的窗口中包含的控件启用工具提示[CFrameWnd](../mfc/reference/cframewnd-class.md)。 文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)提供有关工具提示的信息中的控件`CFrameWnd`。  
  
 本文章系列中涉及的主题包括：  
  
-   [启用工具提示](../mfc/enabling-tool-tips.md)  
  
-   [处理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)  
  
 为按钮自动显示工具提示，并包含在父窗口中的其他控件派生自`CFrameWnd`。 这是因为`CFrameWnd`具有默认处理程序[TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269)通知，它处理**TTN_NEEDTEXT**通知从工具提示与控件关联的控件。  
  
 但是，此默认处理程序不调用时**TTN_NEEDTEXT**从与不是一个窗口中的控件关联的工具提示控件发送通知`CFrameWnd`，如对话框中或窗体视图上的控件。 因此，它是你提供的处理程序函数所必需的**TTN_NEEDTEXT**为了显示子控件的工具提示的通知消息。  
  
 为通过 windows 提供的默认工具提示[CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)不具有与之关联的文本。 检索文本的工具提示显示， **TTN_NEEDTEXT**显示工具提示窗口之前，会向工具提示控件的父窗口发送通知。 如果没有此消息将某些值赋给处理程序**pszText**的成员**TOOLTIPTEXT**结构，不将为工具提示显示任何文本。  
  
## <a name="see-also"></a>请参阅  
 [工具提示](../mfc/tool-tips.md)

