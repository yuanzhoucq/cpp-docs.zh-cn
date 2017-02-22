---
title: "WM_ 消息处理程序：N - O | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_NCHITTEST"
  - "ON_WM_NCLBUTTONDOWN"
  - "ON_WM_NCCALCSIZE"
  - "ON_WM_NCLBUTTONUP"
  - "ON_WM_NCPAINT"
  - "ON_WM_NCMBUTTONUP"
  - "ON_WM_NCCREATE"
  - "ON_WM_NCACTIVATE"
  - "ON_WM_NCMOUSEMOVE"
  - "ON_WM_NCRBUTTONDBLCLK"
  - "ON_WM_NCLBUTTONDBLCLK"
  - "ON_WM_NCDESTROY"
  - "ON_WM_NCMBUTTONDBLCLK"
  - "ON_WM_NCRBUTTONDOWN"
  - "ON_WM_NCRBUTTONUP"
  - "ON_WM_NCMBUTTONDOWN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_NCACTIVATE"
  - "ON_WM_NCCALCSIZE"
  - "ON_WM_NCCREATE"
  - "ON_WM_NCDESTROY"
  - "ON_WM_NCHITTEST"
  - "ON_WM_NCLBUTTONDBLCLK"
  - "ON_WM_NCLBUTTONDOWN"
  - "ON_WM_NCLBUTTONUP"
  - "ON_WM_NCMBUTTONDBLCLK"
  - "ON_WM_NCMBUTTONDOWN"
  - "ON_WM_NCMBUTTONUP"
  - "ON_WM_NCMOUSEMOVE"
  - "ON_WM_NCPAINT"
  - "ON_WM_NCRBUTTONDBLCLK"
  - "ON_WM_NCRBUTTONDOWN"
  - "ON_WM_NCRBUTTONUP"
  - "WM_ 消息"
ms.assetid: 4efd1cda-b642-4e8b-89e8-73255fa70d77
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# WM_ 消息处理程序：N - O
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

左侧下图的映射条目对应于右侧的函数原型：  
  
|映射项|函数原型|  
|---------|----------|  
|ON\_WM\_NCACTIVATE\(\)|afx\_msg BOOL BOOL \( [OnNcActivate](../Topic/CWnd::OnNcActivate.md)\);|  
|ON\_WM\_NCCALCSIZE\(\)|[OnNcCalcSize](../Topic/CWnd::OnNcCalcSize.md)afx\_msg 无效 \(NCCALCSIZE\_PARAMS BOOL，FAR\*\);|  
|ON\_WM\_NCCREATE\(\)|afx\_msg BOOL [OnNcCreate](../Topic/CWnd::OnNcCreate.md)\(LPCREATESTRUCT\);|  
|ON\_WM\_NCDESTROY\(\)|afx\_msg void [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)\(\);|  
|ON\_WM\_NCHITTEST\(\)|afx\_msg LRESULT [OnNcHitTest](../Topic/CWnd::OnNcHitTest.md)\(CPoint\);|  
|ON\_WM\_NCLBUTTONDBLCLK\(\)|[OnNcLButtonDblClk](../Topic/CWnd::OnNcLButtonDblClk.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCLBUTTONDOWN\(\)|[OnNcLButtonDown](../Topic/CWnd::OnNcLButtonDown.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCLBUTTONUP\(\)|[OnNcLButtonUp](../Topic/CWnd::OnNcLButtonUp.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCMBUTTONDBLCLK\(\)|[OnNcLButtonDblClk](../Topic/CWnd::OnNcMButtonDblClk.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCMBUTTONDOWN\(\)|[OnNcLButtonDown](../Topic/CWnd::OnNcMButtonDown.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCMBUTTONUP\(\)|[OnNcLButtonUp](../Topic/CWnd::OnNcMButtonUp.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCMOUSEHOVER\(\)|[OnNcMouseHover](../Topic/CWnd::OnNcMouseHover.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCMOUSELEAVE\(\)|afx\_msg 无效 \(\); [OnNcMouseLeave](../Topic/CWnd::OnNcMouseLeave.md)|  
|ON\_WM\_NCMOUSEMOVE\(\)|[OnNcMouseMove](../Topic/CWnd::OnNcMouseMove.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCPAINT\(\)|afx\_msg 无效 \(\); [OnNcPaint](../Topic/CWnd::OnNcPaint.md)|  
|ON\_WM\_NCRBUTTONDBLCLK\(\)|[OnNcLButtonDblClk](../Topic/CWnd::OnNcRButtonDblClk.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCRBUTTONDOWN\(\)|[OnNcLButtonDown](../Topic/CWnd::OnNcRButtonDown.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCRBUTTONUP\(\)|[OnNcLButtonUp](../Topic/CWnd::OnNcRButtonUp.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_NCLBUTTONDBLCLK\(\)|无效 [OnNcXButtonDblClk](../Topic/CWnd::OnNcXButtonDblClk.md)\(短，UINT，CPoint\);|  
|ON\_WM\_NCLBUTTONDOWN\(\)|无效 afx\_msg [OnNcXButtonDown](../Topic/CWnd::OnNcXButtonDown.md)\(短，UINT，CPoint\);|  
|ON\_WM\_NCLBUTTONUP\(\)|无效 afx\_msg [OnNcXButtonUp](../Topic/CWnd::OnNcXButtonUp.md)\(短，UINT，CPoint\);|  
|ON\_WM\_NEXTMENU\(\)|[OnNextMenu](../Topic/CWnd::OnNextMenu.md)afx\_msg 无效 \(UINT，LPMDINEXTMENU\);|  
|ON\_WM\_NOTIFYFORMAT\(\)|afx\_msg UINT [OnNotifyFormat](../Topic/CWnd::OnNotifyFormat.md)\(CWnd\*，UINT\);|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)