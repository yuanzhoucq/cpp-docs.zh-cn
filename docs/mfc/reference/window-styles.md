---
title: "窗口样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WS_MINIMIZEBOX
- WS_SIZEBOX
- WS_CLIPCHILDREN
- WS_TILED
- WS_GROUP
- WS_VSCROLL
- WS_CHILD
- WS_TABSTOP
- WS_HSCROLL
- WS_THICKFRAME
- WS_DISABLED
- WS_POPUP
- WS_ICONIC
- WS_MAXIMIZE
- WS_VISIBLE
- WS_POPUPWINDOW
- WS_TILEDWINDOW
- WS_DLGFRAME
- WS_MINIMIZE
- WS_CAPTION
- WS_OVERLAPPED
- WS_BORDER
- WS_MAXIMIZEBOX
- WS_OVERLAPPEDWINDOW
- WS_SYSMENU
- WS_CHILDWINDOW
- WS_CLIPSIBLINGS
dev_langs:
- C++
helpviewer_keywords:
- WS_THICKFRAME constant
- WS_TILEDWINDOW constant
- WS_MAXIMIZEBOX constant
- WS_DLGFRAME constant
- WS_CHILDWINDOW constant
- window styles, in MFC
- WS_CHILD constant
- WS_GROUP constant
- WS_MINIMIZE constant
- WS_CAPTION constant
- WS_MAXIMIZE constant
- WS_POPUP constant
- WS_SYSMENU constant
- WS_TILED constant
- window styles
- WS_POPUPWINDOW constant
- WS_CLIPSIBLINGS constant
- WS_BORDER constant
- WS_DISABLED constant
- WS_VSCROLL constant
- WS_OVERLAPPED constant
- WS_MINIMIZEBOX constant
- WS_VISIBLE constant
- WS_OVERLAPPEDWINDOW constant
- WS_TABSTOP constant
- WS_ICONIC constant
- WS_SIZEBOX constant
- WS_HSCROLL constant
- WS_CLIPCHILDREN constant
- styles, windows
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d814e3a10132fb3fe88969ce434f8286b02afba5
ms.lasthandoff: 02/24/2017

---
# <a name="window-styles"></a>窗口样式
-   `WS_BORDER`创建具有边框的窗口。  
  
-   **WS_CAPTION**创建该窗口具有标题栏 (意味着`WS_BORDER`样式)。 不能与使用**WS_DLGFRAME**样式。  
  
-   **WS_CHILD**创建一个子窗口。 不能与使用`WS_POPUP`样式。  
  
-   **WS_CHILDWINDOW**相同**WS_CHILD**样式。  
  
-   **WS_CLIPCHILDREN**排除在父窗口中绘制时，子窗口占用的区域。 在您创建的父窗口时使用。  
  
-   **WS_CLIPSIBLINGS**剪辑子窗口相对于彼此; 即，当特定子窗口收到一条绘制消息， **WS_CLIPSIBLINGS**样式裁剪子窗口要更新的区域外其他所有重叠的子窗口。 (如果**WS_CLIPSIBLINGS**不给出，并且子窗口重叠，子窗口的工作区中绘制时，可能要绘制的相邻的子窗口的工作区内。)适用于**WS_CHILD**仅设置样式。  
  
-   **WS_DISABLED**创建最初处于禁用状态的窗口。  
  
-   **WS_DLGFRAME**带双边框但没有标题创建一个窗口。  
  
-   **WS_GROUP**指定一组控件在其中用户可以从一个控件移到下的箭头键的第一个控件。 使用定义的所有控件**WS_GROUP**样式**FALSE**的第一个控件属于同一个组之后。 使用下一个控件**WS_GROUP**样式启动下一个组 （即，开始下的一个组结尾）。  
  
-   **WS_HSCROLL**创建该窗口具有水平滚动条。  
  
-   **WS_ICONIC**创建开始最小化窗口。 与相同**WS_MINIMIZE**样式。  
  
-   **WS_MAXIMIZE**创建一个最大大小的窗口。  
  
-   **WS_MAXIMIZEBOX**创建一个窗口，都有一个最大化按钮。  
  
-   **WS_MINIMIZE**创建开始最小化窗口。 适用于**WS_OVERLAPPED**仅设置样式。  
  
-   **WS_MINIMIZEBOX**创建具有最小化按钮的窗口。  
  
-   **WS_OVERLAPPED**创建重叠的窗口。 重叠的窗口通常具有标题和边框。  
  
-   **WS_OVERLAPPEDWINDOW**创建一个具有重叠的窗口**WS_OVERLAPPED**， **WS_CAPTION**， **WS_SYSMENU**， **WS_THICKFRAME**， **WS_MINIMIZEBOX**，和**WS_MAXIMIZEBOX**样式。  
  
-   `WS_POPUP`创建一个弹出窗口。 不能与使用**WS_CHILD**样式。  
  
-   **WS_POPUPWINDOW**创建与一个弹出窗口`WS_BORDER`， `WS_POPUP`，和**WS_SYSMENU**样式。 **WS_CAPTION**样式必须结合**WS_POPUPWINDOW**样式，即可使控件菜单上可见。  
  
-   **WS_SIZEBOX**创建具有大小调整边框的窗口。 与相同**WS_THICKFRAME**样式。  
  
-   **WS_SYSMENU**创建该窗口具有标题栏中的控件菜单框。 使用仅为带有标题栏的窗口。  
  
-   **WS_TABSTOP**控件通过其用户可以通过使用 TAB 键移动的任意数量之一指定。 TAB 键将用户移至指定的下一个控件**WS_TABSTOP**样式。  
  
-   **WS_THICKFRAME**用较粗的框架，可用来调整窗口的大小创建一个窗口。  
  
-   **WS_TILED**创建重叠的窗口。 重叠的窗口具有标题栏和边框。 与相同**WS_OVERLAPPED**样式。  
  
-   **WS_TILEDWINDOW**创建一个具有重叠的窗口**WS_OVERLAPPED**， **WS_CAPTION**， **WS_SYSMENU**， **WS_THICKFRAME**， **WS_MINIMIZEBOX**，和**WS_MAXIMIZEBOX**样式。 与相同**WS_OVERLAPPEDWINDOW**样式。  
  
-   **WS_VISIBLE**创建初始可见的窗口。  
  
-   **WS_VSCROLL**创建该窗口具有一个垂直滚动条。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)   
 [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)   
 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)


