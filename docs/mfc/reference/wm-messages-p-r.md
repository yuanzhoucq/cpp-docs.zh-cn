---
title: "WM_ 消息：P - R | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_RBUTTONUP"
  - "ON_WM_PALETTECHANGED"
  - "ON_WM_RBUTTONDBLCLK"
  - "ON_WM_QUERYENDSESSION"
  - "ON_WM_PARENTNOTIFY"
  - "ON_WM_PALETTEISCHANGING"
  - "ON_WM_QUERYOPEN"
  - "ON_WM_PAINT"
  - "ON_WM_QUERYNEWPALETTE"
  - "ON_WM_RBUTTONDOWN"
  - "ON_WM_RENDERALLFORMATS"
  - "ON_WM_PAINTCLIPBOARD"
  - "ON_WM_RENDERFORMAT"
  - "ON_WM_QUERYDRAGICON"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_PAINT"
  - "ON_WM_PAINTCLIPBOARD"
  - "ON_WM_PALETTECHANGED"
  - "ON_WM_PALETTEISCHANGING"
  - "ON_WM_PARENTNOTIFY"
  - "ON_WM_QUERYDRAGICON"
  - "ON_WM_QUERYENDSESSION"
  - "ON_WM_QUERYNEWPALETTE"
  - "ON_WM_QUERYOPEN"
  - "ON_WM_RBUTTONDBLCLK"
  - "ON_WM_RBUTTONDOWN"
  - "ON_WM_RBUTTONUP"
  - "ON_WM_RENDERALLFORMATS"
  - "ON_WM_RENDERFORMAT"
  - "WM_ 消息"
ms.assetid: f46962e5-8329-4f1f-9b4d-fdad2a5ce1f8
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# WM_ 消息：P - R
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以下图像输入对应于函数原型：  
  
|映射项|函数原型|  
|---------|----------|  
|ON\_WM\_PAINT\(\)|afx\_msg 无效 \(\); [OnPaint](../Topic/CWnd::OnPaint.md)|  
|ON\_WM\_PAINTCLIPBOARD\(\)|[OnPaintClipboard](../Topic/CWnd::OnPaintClipboard.md)afx\_msg 无效 \(CWnd\*，处理\);|  
|ON\_WM\_PALETTECHANGED\(\)|afx\_msg 无效 \(CWnd\*\); [OnPaletteChanged](../Topic/CWnd::OnPaletteChanged.md)|  
|ON\_WM\_PALETTEISCHANGING\(\)|afx\_msg 无效 \(CWnd\*\); [OnPaletteIsChanging](../Topic/CWnd::OnPaletteIsChanging.md)|  
|ON\_WM\_PARENTNOTIFY\(\)|[OnParentNotify](../Topic/CWnd::OnParentNotify.md)afx\_msg 无效 \(UINT，长\);|  
|ON\_WM\_POWERBROADCAST\(\)|afx\_msg UINT [OnPowerBroadcast](../Topic/CWnd::OnPowerBroadcast.md)\(UINT，UINT\);|  
|ON\_WM\_QUERYDRAGICON\(\)|afx\_msg HCURSOR [OnQueryDragIcon](../Topic/CWnd::OnQueryDragIcon.md)\(\);|  
|ON\_WM\_QUERYENDSESSION\(\)|afx\_msg BOOL [OnQueryEndSession](../Topic/CWnd::OnQueryEndSession.md)\(\);|  
|ON\_WM\_QUERYNEWPALETTE\(\)|afx\_msg BOOL [OnQueryNewPalette](../Topic/CWnd::OnQueryNewPalette.md)\(\);|  
|ON\_WM\_QUERYOPEN\(\)|afx\_msg BOOL [OnQueryOpen](../Topic/CWnd::OnQueryOpen.md)\(\);|  
|ON\_WM\_RBUTTONDBLCLK\(\)|[OnRButtonDblClk](../Topic/CWnd::OnRButtonDblClk.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_RBUTTONDOWN\(\)|[OnRButtonDown](../Topic/CWnd::OnRButtonDown.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_RBUTTONUP\(\)|[OnRButtonUp](../Topic/CWnd::OnRButtonUp.md)afx\_msg 无效 \(UINT，CPoint\);|  
|ON\_WM\_RENDERALLFORMATS\(\)|afx\_msg 无效 \(\); [OnRenderAllFormats](../Topic/CWnd::OnRenderAllFormats.md)|  
|ON\_WM\_RENDERFORMAT\(\)|afx\_msg 无效 \(UINT\); [OnRenderFormat](../Topic/CWnd::OnRenderFormat.md)|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)