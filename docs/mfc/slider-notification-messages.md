---
title: "滑块通知消息 | Microsoft Docs"
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
  - "CSliderCtrl 类, 通知"
  - "消息, 通知"
  - "通知, CSliderCtrl"
  - "滑块控件, 通知消息"
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 滑块通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

滑块控件通过发送父 `WM_HSCROLL` 或 `WM_VSCROLL` 消息通知其父窗口用户操作，具体取决于滑块控件的方向。  若要处理这些消息，请添加 `WM_HSCROLL` 和 `WM_VSCROLL` 消息的处理程序。父窗口。  [OnHScroll](../Topic/CWnd::OnHScroll.md)[OnVScroll](../Topic/CWnd::OnVScroll.md) 和成员函数将通知代码传递、滑块的位置及其指向 [CSliderCtrl](../mfc/reference/csliderctrl-class.md) 对象。  您会注意到指针是 **CScrollBar \*** 类型，即使它指向 `CSliderCtrl` 对象。  如果需要，操作滑块控件，则可能需要将角色分配该指针。  
  
 使用滚动条通知代码，而不是，滑块控件发送的不同通知代码组。  滑块控件发送 **TB\_BOTTOM**，**TB\_LINEDOWN**，**TB\_LINEUP**，而且，**TB\_TOP** 通知代码使用键盘时，只有在用户使用滑块控件交互。  它在用户使用鼠标时，**TB\_THUMBPOSITION** 和 **TB\_THUMBTRACK** 只发送通知消息。  **TB\_ENDTRACK**、**TB\_PAGEDOWN**和 **TB\_PAGEUP** 代码通知在这两种情况下发送。  
  
 下表列出滑块控件通知消息和事件 \(虚拟键代码或鼠标事件\) 会导致将发送的通知。\(对于标准虚拟键代码列表，请参见 Winuser.h。\)  
  
|通知消息|使发送通知的事件|  
|----------|--------------|  
|**TB\_BOTTOM**|**VK\_END**|  
|**TB\_ENDTRACK**|`WM_KEYUP` \(用户松开发送相关虚拟键代码\) 的密钥|  
|**TB\_LINEDOWN**|**VK\_RIGHT** 或 **VK\_DOWN**|  
|**TB\_LINEUP**|**VK\_LEFT** 或 **VK\_UP**|  
|**TB\_PAGEDOWN**|**VK\_NEXT** \(用户单击通道的下方或单击滑块右侧下\)|  
|**TB\_PAGEUP**|**VK\_PRIOR** \(在或通道滑块在左侧\) 中用户单击|  
|**TB\_THUMBPOSITION**|`WM_LBUTTONUP` 在 **TB\_THUMBTRACK** 通知消息之后|  
|**TB\_THUMBTRACK**|滑块移动 \(用户拖动滑块\)|  
|**TB\_TOP**|**VK\_HOME**|  
  
## 请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)