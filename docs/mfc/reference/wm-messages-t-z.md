---
title: "WM_ 消息：T - Z | Microsoft Docs"
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
  - "ON_WM_TCARD"
  - "ON_WM_WININICHANGE"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_VSCROLL"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_WINDOWPOSCHANGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_TCARD"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_VSCROLL"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_WINDOWPOSCHANGING"
  - "ON_WM_WININICHANGE"
  - "WM_ 消息"
ms.assetid: c528bb2e-ddb5-4da6-b652-432a387408b8
caps.latest.revision: 16
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WM_ 消息：T - Z
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以下图像输入对应于函数原型：  
  
|映射项|函数原型|  
|---------|----------|  
|ON\_WM\_TCARD\(\)|[OnTCard](../Topic/CWnd::OnTCard.md)afx\_msg 无效 \(UINT，DWORD\);|  
|ON\_WM\_TIMECHANGE\(\)|afx\_msg 无效 \(\); [OnTimeChange](../Topic/CWnd::OnTimeChange.md)|  
|ON\_WM\_TIMER\(\)|afx\_msg 无效 \(UINT\_PTR\); [OnTimer](../Topic/CWnd::OnTimer.md)|  
|ON\_WM\_UNICHAR\(\)|[OnUniChar](../Topic/CWnd::OnUniChar.md)afx\_msg 无效 \(UINT、UINT，UINT\);|  
|ON\_WM\_UNINITMENUPOPUP\(\)|[OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)afx\_msg 无效 \(CMenu\*，UINT\);|  
|ON\_WM\_USERCHANGED\(\)|afx\_msg 无效 \(\); [OnUserChanged](../Topic/CWnd::OnUserChanged.md)|  
|ON\_WM\_VKEYTOITEM\(\)|afx\_msg int [OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)\(UINT，CWnd\*，UINT\);|  
|ON\_WM\_VSCROLL\(\)|[OnVScroll](../Topic/CWnd::OnVScroll.md)afx\_msg 无效 \(UINT，UINT，CWnd\*\);|  
|ON\_WM\_VSCROLLCLIPBOARD\(\)|[OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)afx\_msg 无效 \(CWnd\*，UINT，UINT\);|  
|ON\_WM\_WINDOWPOSCHANGED\(\)|afx\_msg 无效 \(WINDOWPOS\*\); [OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)|  
|ON\_WM\_WINDOWPOSCHANGING\(\)|afx\_msg 无效 \(WINDOWPOS\*\); [OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)|  
|ON\_WM\_WININICHANGE\(\)|afx\_msg 无效 \(\); [OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)LPSTR|  
|ON\_WM\_WTSSESSION\_CHANGE\(\)|[OnSessionChange](../Topic/CWnd::OnSessionChange.md)afx\_msg 无效 \(UINT，UINT\);|  
|ON\_WM\_XBUTTONDBLCLK\(\)|[OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)afx\_msg 无效 \(UINT，UINT，CPoint\);|  
|ON\_WM\_XBUTTONDOWN\(\)|[OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)afx\_msg 无效 \(UINT，UINT，CPoint\);|  
|ON\_WM\_XBUTTONUP\(\)|[OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)afx\_msg 无效 \(UINT，UINT，CPoint\);|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)