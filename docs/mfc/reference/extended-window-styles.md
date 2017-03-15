---
title: "扩展的窗口样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WS_EX_TOOLWINDOW"
  - "WS_EX_LEFTSCROLLBAR"
  - "WS_EX_RTLREADING"
  - "WS_EX_WINDOWEDGE"
  - "WS_EX_CLIENTEDGE"
  - "WS_EX_STATICEDGE"
  - "WS_EX_LTRREADING"
  - "WS_EX_DLGMODALFRAME"
  - "WS_EX_RIGHTSCROLLBAR"
  - "WS_EX_CONTROLPARENT"
  - "WS_EX_ACCEPTFILES"
  - "WS_EX_TRANSPARENT"
  - "WS_EX_RIGHT"
  - "WS_EX_APPWINDOW"
  - "WS_EX_TOPMOST"
  - "WS_EX_CONTEXTHELP"
  - "WS_EX_MDICHILD"
  - "WS_EX_LEFT"
  - "WS_EX_OVERLAPPEDWINDOW"
  - "WS_EX_PALETTEWINDOW"
  - "WS_EX_NOPARENTNOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "扩展的窗口样式"
  - "样式, 窗口"
  - "WS_EX_ACCEPTFILES 常量"
  - "WS_EX_APPWINDOW 常量"
  - "WS_EX_CLIENTEDGE 常量"
  - "WS_EX_CONTEXTHELP 常量"
  - "WS_EX_CONTROLPARENT 常量"
  - "WS_EX_DLGMODALFRAME 常量"
  - "WS_EX_LEFT 常量"
  - "WS_EX_LEFTSCROLLBAR 常量"
  - "WS_EX_LTRREADING 常量"
  - "WS_EX_MDICHILD 常量"
  - "WS_EX_NOPARENTNOTIFY 常量"
  - "WS_EX_OVERLAPPEDWINDOW 常量"
  - "WS_EX_PALETTEWINDOW 常量"
  - "WS_EX_RIGHT 常量"
  - "WS_EX_RIGHTSCROLLBAR 常量"
  - "WS_EX_RTLREADING 常量"
  - "WS_EX_STATICEDGE 常量"
  - "WS_EX_TOOLWINDOW 常量"
  - "WS_EX_TOPMOST 常量"
  - "WS_EX_TRANSPARENT 常量"
  - "WS_EX_WINDOWEDGE 常量"
ms.assetid: d18e6c69-0a01-49ed-b58a-55b3802b47c1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 扩展的窗口样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **WS\_EX\_ACCEPTFILES** 指定用此样式创建的窗口接收拖放文件。  
  
-   当窗口可见时，**WS\_EX\_APPWINDOW** 强制在任务栏上的一个顶级窗口。  
  
-   **WS\_EX\_CLIENTEDGE** 指定指定一个窗口具有3D外观 \- 也就是说，一个带下沉式边缘的边框。  
  
-   **WS\_EX\_CONTEXTHELP** 在窗口的标题栏包含一个问号标记。  用户单击问号时，光标变为一个带有指针的问号。  这时，如果用户单击子窗口，子窗口将收到 **WM\_HELP** 消息。  
  
-   **WS\_EX\_CONTROLPARENT** 允许用户通过使用 TAB 键在窗口的子窗口之间导航。  
  
-   当您在 `dwStyle` 参数中指定 **WS\_CAPTION** 样式标志时，**WS\_EX\_DLGMODALFRAME** 指定一个双边框的窗口，这窗口 \(可选\)可在标题栏中创建 。  
  
-   **WS\_EX\_LAYERED** 窗口是一个 [分层窗口](http://msdn.microsoft.com/library/ms632599\(v=vs.85\).aspx#layered") 如果窗口具有 **CS\_OWNDC** 或 **CS\_CLASSDC**任意一个的[class style](http://msdn.microsoft.com/library/ms633574\(v=vs.85\).aspx#class_styles") ，则此样式不被使用。  但是，[!INCLUDE[win8_first](../../mfc/reference/includes/win8_first_md.md)] 支持子窗口的 **WS\_EX\_LAYERED** 样式，之前的 Windows 版本仅对顶级窗口支持。  
  
-   **WS\_EX\_LEFT** 设置窗口泛型左对齐的属性。  这是默认设置。  
  
-   **WS\_EX\_LEFTSCROLLBAR** 在客户端区域左边设置垂直滚动条。  
  
-   **WS\_EX\_LTRREADING** 使用从左向右读取顺序的属性显示窗口文本。  这是默认设置。  
  
-   **WS\_EX\_MDICHILD** 创建 MDI 子窗口。  
  
-   在子窗口被创建或销毁时，**WS\_EX\_NOPARENTNOTIFY** 指定用此样式创建的子窗口不会发送 `WM_PARENTNOTIFY` 信息到其父窗口。  
  
-   **WS\_EX\_OVERLAPPEDWINDOW** 合并 **WS\_EX\_CLIENTEDGE** 和 **WS\_EX\_WINDOWEDGE** 样式  
  
-   **WS\_EX\_PALETTEWINDOW** 合并**WS\_EX\_WINDOWEDGE**  和**WS\_EX\_TOPMOST** 样式。  
  
-   **WS\_EX\_RIGHT** 设置窗口泛型右对齐的属性。  这取决于窗口类。  
  
-   **WS\_EX\_RIGHTSCROLLBAR** 在客户端区右边设置垂直滚动条 \(如果有\)。  这是默认设置。  
  
-   **WS\_EX\_RTLREADING** 使用从右向左读取顺序的属性显示窗口文本。  
  
-   **WS\_EX\_STATICEDGE** 创建一个三维边框样式的窗口，旨在用于那些不接受用户输入的项目。  
  
-   **WS\_EX\_TOOLWINDOW** 创建一个工具窗口，该窗口旨在用作浮动工具栏。  工具窗口包括标题栏，其比正常的标题栏短并且窗口标题使用较小的字体。  工具窗口不会显示在任务栏中也不会显示在当用户按 Alt\+Tab 时出现的窗口中。  
  
-   **WS\_EX\_TOPMOST** 指定用此样式创建的窗口应是放置在所有的 nontopmost 窗口之上，并且即使当停用窗口也得保持在其之上。  应用程序可以使用 `SetWindowPos` 成员函数添加或删除此特性。  
  
-   **WS\_EX\_TRANSPARENT** 指定用此样式创建的窗口是透明的。  即在窗口下的任何窗口不能被窗口遮盖。  用此样式创建的窗口接收 `WM_PAINT` 消息只有在其下方的所有同级窗口更新后。  
  
-   **WS\_EX\_WINDOWEDGE** 指定窗口有一个凸出边缘的边框。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)