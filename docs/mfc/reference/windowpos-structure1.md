---
title: "WINDOWPOS 结构&1; |Microsoft 文档"
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
- WINDOWPOS structure
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 522b15d630c3a5a3593010250db0491601493c69
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="windowpos-structure1"></a>WINDOWPOS 结构&1;
`WINDOWPOS`结构包含有关的大小和窗口的位置信息。  
  
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
 标识窗口中。  
  
 *hwndInsertAfter*  
 标识背后的放置此窗口的窗口。  
  
 *x*  
 指定窗口的左边缘的位置。  
  
 *y*  
 指定窗口的右边缘的位置。  
  
 `cx`  
 指定窗口的宽度，以像素为单位。  
  
 `cy`  
 指定以像素为单位的窗口高度。  
  
 `flags`  
 指定窗口中定位的选项。 此成员可以是下列值之一︰  
  
- **SWP_DRAWFRAME**在窗口上四处绘制 （窗口中的类说明中定义） 的框架。 该窗口才接收`WM_NCCALCSIZE`消息。  
  
- **SWP_FRAMECHANGED**发送`WM_NCCALCSIZE`消息到窗口中，即使该窗口的大小不会被更改。 如果未指定此标志，`WM_NCCALCSIZE`只有在窗口的大小正在更改时发送。  
  
- **SWP_HIDEWINDOW**隐藏的窗口。  
  
- `SWP_NOACTIVATE`不会激活窗口中。  
  
- **SWP_NOCOPYBITS**放弃的工作区的全部内容。 如果未指定此标志，客户端区域中的有效内容保存和复制回的工作区后的窗口在大小或重新定位。  
  
- `SWP_NOMOVE`保留当前的位置 (将忽略**x**和**y**成员)。  
  
- **SWP_NOOWNERZORDER**不会更改的 Z 顺序的所有者窗口的位置。  
  
- `SWP_NOSIZE`保留当前大小 (将忽略**cx**和**cy**成员)。  
  
- **SWP_NOREDRAW**不重绘的更改。  
  
- **SWP_NOREPOSITION**相同**SWP_NOOWNERZORDER**。  
  
- **SWP_NOSENDCHANGING**禁止接收窗口`WM_WINDOWPOSCHANGING`消息。  
  
- `SWP_NOZORDER`保留当前排序 (将忽略**hwndInsertAfter**成员)。  
  
- **SWP_SHOWWINDOW**显示窗口。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)


