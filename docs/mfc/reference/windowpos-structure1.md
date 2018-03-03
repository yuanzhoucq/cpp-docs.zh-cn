---
title: "WINDOWPOS 结构 1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7db3991a6767e33c73857daf40a977ac5f6f0b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windowpos-structure1"></a>WINDOWPOS 结构 1
`WINDOWPOS`结构包含有关的大小和窗口的位置的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>参数  
 *hwnd*  
 标识窗口。  
  
 *hwndInsertAfter*  
 标识其后放置此窗口的窗口。  
  
 *x*  
 指定窗口的左边缘的位置。  
  
 *y*  
 指定窗口的右边缘的位置。  
  
 `cx`  
 指定的窗口宽度，以像素为单位。  
  
 `cy`  
 指定以像素为单位的窗口高度。  
  
 `flags`  
 指定窗口定位选项。 此成员可以是以下值之一：  
  
- **SWP_DRAWFRAME**窗口周围绘制 （在窗口的类描述中定义） 的帧。 该窗口才接收`WM_NCCALCSIZE`消息。  
  
- **SWP_FRAMECHANGED**发送`WM_NCCALCSIZE`消息到窗口中，即使未发生更改窗口的大小。 如果未指定此标志，`WM_NCCALCSIZE`仅更改窗口的大小时发送。  
  
- **SWP_HIDEWINDOW**隐藏窗口。  
  
- `SWP_NOACTIVATE`不会激活窗口。  
  
- **SWP_NOCOPYBITS**放弃的工作区的全部内容。 如果未指定此标志，客户端区域的有效内容会保存，并且之后的窗口在大小或重新定位复制回的工作区。  
  
- `SWP_NOMOVE`保留当前的位置 (将忽略**x**和**y**成员)。  
  
- **SWP_NOOWNERZORDER**不会更改中的 Z 顺序的所有者窗口的位置。  
  
- `SWP_NOSIZE`保留当前大小 (忽略**cx**和**cy**成员)。  
  
- **SWP_NOREDRAW**不重绘更改。  
  
- **SWP_NOREPOSITION**相同**SWP_NOOWNERZORDER**。  
  
- **SWP_NOSENDCHANGING**窗口防止接收`WM_WINDOWPOSCHANGING`消息。  
  
- `SWP_NOZORDER`保留当前排序 (忽略**hwndInsertAfter**成员)。  
  
- **SWP_SHOWWINDOW**显示窗口。  
  
## <a name="requirements"></a>惠?  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

