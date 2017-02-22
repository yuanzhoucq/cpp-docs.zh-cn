---
title: "窗口样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WS_MINIMIZEBOX"
  - "WS_SIZEBOX"
  - "WS_CLIPCHILDREN"
  - "WS_TILED"
  - "WS_GROUP"
  - "WS_VSCROLL"
  - "WS_CHILD"
  - "WS_TABSTOP"
  - "WS_HSCROLL"
  - "WS_THICKFRAME"
  - "WS_DISABLED"
  - "WS_POPUP"
  - "WS_ICONIC"
  - "WS_MAXIMIZE"
  - "WS_VISIBLE"
  - "WS_POPUPWINDOW"
  - "WS_TILEDWINDOW"
  - "WS_DLGFRAME"
  - "WS_MINIMIZE"
  - "WS_CAPTION"
  - "WS_OVERLAPPED"
  - "WS_BORDER"
  - "WS_MAXIMIZEBOX"
  - "WS_OVERLAPPEDWINDOW"
  - "WS_SYSMENU"
  - "WS_CHILDWINDOW"
  - "WS_CLIPSIBLINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "样式, 窗口"
  - "窗口样式"
  - "窗口样式, 在 MFC 中"
  - "WS_BORDER 常量"
  - "WS_CAPTION 常量"
  - "WS_CHILD 常量"
  - "WS_CHILDWINDOW 常量"
  - "WS_CLIPCHILDREN 常量"
  - "WS_CLIPSIBLINGS 常量"
  - "WS_DISABLED 常量"
  - "WS_DLGFRAME 常量"
  - "WS_GROUP 常量"
  - "WS_HSCROLL 常量"
  - "WS_ICONIC 常量"
  - "WS_MAXIMIZE 常量"
  - "WS_MAXIMIZEBOX 常量"
  - "WS_MINIMIZE 常量"
  - "WS_MINIMIZEBOX 常量"
  - "WS_OVERLAPPED 常量"
  - "WS_OVERLAPPEDWINDOW 常量"
  - "WS_POPUP 常量"
  - "WS_POPUPWINDOW 常量"
  - "WS_SIZEBOX 常量"
  - "WS_SYSMENU 常量"
  - "WS_TABSTOP 常量"
  - "WS_THICKFRAME 常量"
  - "WS_TILED 常量"
  - "WS_TILEDWINDOW 常量"
  - "WS_VISIBLE 常量"
  - "WS_VSCROLL 常量"
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 窗口样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   `WS_BORDER`创建具有边框的窗口。  
  
-   **WS\_CAPTION** 用于创建具有标题栏的窗口（即表示 `WS_BORDER` 样式）。  不能与 **WS\_DLGFRAME** 样式一起使用。  
  
-   **WS\_CHILD** 用于创建子窗口。  不能与 `WS_POPUP` 样式一起使用。  
  
-   **WS\_CHILDWINDOW** 和 **WS\_CHILD** 样式相同。  
  
-   在父窗口中绘图时，**WS\_CLIPCHILDREN** 会排除子窗口占用的区域。  在创建父窗口时使用。  
  
-   **WS\_CLIPSIBLINGS** 用于裁剪各子窗口；也就是说，在特定子窗口接收绘制消息时，**WS\_CLIPSIBLINGS** 样式会剪裁要更新的子窗口之外的区域内所有重叠的其他子窗口。（如果未指定 **WS\_CLIPSIBLINGS** 且子级窗口重叠，那么，当您在子级窗口的客户端区域内绘制时，还可以在相邻子级窗口的客户端区域中绘制。）仅限用于 **WS\_CHILD** 样式。  
  
-   **WS\_DISABLED** 用于创建初始禁用的窗口。  
  
-   **WS\_DLGFRAME** 用于创建没有标题的双边框窗口。  
  
-   **WS\_GROUP** 用于指定一组控件的第一个控件，用户可以使用箭头键从一个控件移动到下一个控件。  第一个控件后面用 **WS\_GROUP** 样式 **FALSE** 定义的所有控件都属于同一组。  **WS\_GROUP** 样式的下一个控件启动下一组（即，在一组结束的地方开始下一组）。  
  
-   **WS\_HSCROLL** 用于创建具有水平滚动条的窗口。  
  
-   **WS\_ICONIC** 用于创建初始最小化的窗口。  与 **WS\_MINIMIZE** 样式相同。  
  
-   **WS\_MAXIMIZE** 用于创建最大的窗口。  
  
-   **WS\_MAXIMIZEBOX** 用于创建具有最大按钮的窗口。  
  
-   **WS\_MINIMIZE** 用于创建初始最小化的窗口。  仅限用于 **WS\_OVERLAPPED** 样式。  
  
-   **WS\_MINIMIZEBOX** 用于创建具有最小化按钮的窗口。  
  
-   **WS\_OVERLAPPED** 用于创建重叠的窗口。  重叠窗口通常包含一个标题和一个边框。  
  
-   **WS\_OVERLAPPEDWINDOW** 用于创建 **WS\_OVERLAPPED**、**WS\_CAPTION**、**WS\_SYSMENU**、**WS\_THICKFRAME**、**WS\_MINIMIZEBOX** 和 **WS\_MAXIMIZEBOX** 样式的重叠窗口。  
  
-   `WS_POPUP` 创建弹出窗口。  不能与 **WS\_CHILD** 样式一起使用。  
  
-   **WS\_POPUPWINDOW** 用于创建 `WS_BORDER`、`WS_POPUP` 和 **WS\_SYSMENU** 样式的弹出窗口。  必须将 **WS\_CAPTION** 样式与 **WS\_POPUPWINDOW** 样式结合，以使控制菜单可见。  
  
-   **WS\_SIZEBOX** 创建有可调整边框的窗口。  与 **WS\_THICKFRAME** 样式相同。  
  
-   **WS\_SYSMENU** 用于创建标题栏中具有控件菜单框的窗口。  仅用于带有标题栏的窗口。  
  
-   **WS\_TABSTOP** 用于指定任意数量控件中的某个，用户可以使用 TAB 键在这些控件中移动。  TAB 键将用户移动到 **WS\_TABSTOP** 样式指定的下一个控件。  
  
-   **WS\_THICKFRAME** 用于通过可用于调整窗口大小的粗框架创建窗口。  
  
-   **WS\_TILED** 用于创建重叠的窗口。  重叠窗口具有一个标题栏和一个边框。  与 **WS\_OVERLAPPED** 样式相同。  
  
-   **WS\_TILEDWINDOW** 用于创建 **WS\_OVERLAPPED**、**WS\_CAPTION**、**WS\_SYSMENU**、**WS\_THICKFRAME**、**WS\_MINIMIZEBOX** 和 **WS\_MAXIMIZEBOX** 样式的重叠窗口。  与 **WS\_OVERLAPPEDWINDOW** 样式相同。  
  
-   **WS\_VISIBLE** 用于创建初始可见的窗口。  
  
-   **WS\_VSCROLL** 用于创建具有垂直滚动条的窗口。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)