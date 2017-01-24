---
title: "静态样式 | Microsoft Docs"
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
  - "SS_SUNKEN"
  - "SS_CENTER"
  - "SS_ENHMETAFILE"
  - "SS_RIGHT"
  - "SS_BLACKRECT"
  - "SS_LEFTNOWORDWRAP"
  - "SS_GRAYFRAME"
  - "SS_USERITEM"
  - "SS_GRAYRECT"
  - "SS_WHITEFRAME"
  - "SS_ETCHEDFRAME"
  - "SS_ETCHEDVERT"
  - "SS_WHITERECT"
  - "SS_PATHELLIPSIS"
  - "SS_WORDELLIPSIS"
  - "SS_NOPREFIX"
  - "SS_BITMAP"
  - "SS_SIMPLE"
  - "SS_CENTERIMAGE"
  - "SS_BLACKFRAME"
  - "SS_OWNERDRAW"
  - "SS_REALSIZEIMAGE"
  - "SS_RIGHTJUST"
  - "SS_ICON"
  - "SS_NOTIFY"
  - "SS_ETCHEDHORZ"
  - "SS_LEFT"
  - "SS_ENDELLIPSIS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SS_BITMAP 常量"
  - "SS_BLACKFRAME 常量"
  - "SS_BLACKRECT 常量"
  - "SS_CENTER 常量"
  - "SS_CENTERIMAGE 常量"
  - "SS_ENDELLIPSIS 常量"
  - "SS_ENHMETAFILE 常量"
  - "SS_ETCHEDFRAME 常量"
  - "SS_ETCHEDHORZ 常量"
  - "SS_ETCHEDVERT 常量"
  - "SS_GRAYFRAME 常量"
  - "SS_GRAYRECT 常量"
  - "SS_ICON 常量"
  - "SS_LEFT 常量"
  - "SS_LEFTNOWORDWRAP 常量"
  - "SS_NOPREFIX 常量"
  - "SS_NOTIFY 常量"
  - "SS_OWNERDRAW 常量"
  - "SS_PATHELLIPSIS 常量"
  - "SS_REALSIZEIMAGE 常量"
  - "SS_RIGHT 常量"
  - "SS_RIGHTJUST 常量"
  - "SS_SIMPLE 常量"
  - "SS_SUNKEN 常量"
  - "SS_USERITEM 常量"
  - "SS_WHITEFRAME 常量"
  - "SS_WHITERECT 常量"
  - "SS_WORDELLIPSIS 常量"
  - "静态样式"
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 静态样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SS\_BITMAP** 中的静态控件指定位图将显示。  特定文本是在资源文件 \(而不是文件名\) 的其他地方定义的名称的。  样式和 nHeight 参数；忽略 nWidth 控件自动调整大小位图。  
  
-   **SS\_BLACKFRAME** 指定使用框架的一个框绘制了颜色和框架窗口相同。  默认为黑色。  
  
-   **SS\_BLACKRECT** 指定矩形的颜色填充用于绘制窗口框架。  默认为黑色。  
  
-   **SS\_CENTER** 指定简单的外接矩形并显示在矩形中央的特定文本。  在显示之前，文本格式。  将扩展超出行尾的 Word 自动换到下居中的行的开头。  
  
-   **SS\_CENTERIMAGE** 指定，因此，如果位图或图标小于静态控件的工作区，该工作区的其余部分用像素的颜色。图标或位图的左上角。的。  如果静态控件包含单行文本，文本垂直居中在控件的工作区。  
  
-   **SS\_ENDELLIPSIS** 或 **SS\_PATHELLIPSIS** 将 \(如果需要，替换部分特定字符串，因此结果，适合指定的矩形。  
  
     还可以指定 **SS\_END\_ELLIPSIS** 替换字符在字符串的末尾或 **SS\_PATHELLIPSIS** 的字符串中间替换字符。  如果字符串包含反斜杠 \(\\\)，该反斜杠之后的许多相同 **SS\_PATHELLIPSIS** 的最后一个文本。  
  
-   **SS\_ENHMETAFILE** 中的静态控件指定一增强型图元文件中显示。  特定文本是元文件的名称。  增强的图元文件静态控件具有固定大小；图元文件以适应静态控件的工作区。  
  
-   使用 **EDGE\_ETCHED** 边缘绘制静态样式，**SS\_ETCHEDFRAME** 控件的框架。  
  
-   使用 **EDGE\_ETCHED** 边缘绘制静态样式，**SS\_ETCHEDHORZ** 控件的上边缘和下边缘。  
  
-   使用 EDGE\_ETCHED 边缘绘制静态样式，**SS\_ETCHEDVERT** 控件的左右边缘。  
  
-   **SS\_GRAYFRAME** 指定使用框架的一个框绘制了颜色和屏幕背静 \(桌面\) 相同。  默认为灰色。  
  
-   **SS\_GRAYRECT** 指定要用于填充矩形的颜色填充背静屏幕。  默认为灰色。  
  
-   **SS\_ICON** 指定对话框中显示的图标。  特定文本是在资源图标 \(而不是文件名\) 的其他地方定义的名称的。  `nWidth` 和 `nHeight` 参数将被忽略；图标自动大小。  
  
-   **SS\_LEFT** 指定简单的外接矩形并显示特定文本刷新左在矩形。  在显示之前，文本格式。  将扩展超出行尾的 Word 自动换到下左对齐的行的开头。  
  
-   **SS\_LEFTNOWORDWRAP** 指定简单的外接矩形并显示特定文本刷新左在矩形。  选项卡，展开，但 Word 不包装。  文本扩展超过行的末尾部分剪辑。  
  
-   **SS\_NOPREFIX**，除非指定此样式，则窗口将解释控件中的文本的所有" and "符 \(&\) 字符是个前缀字符。  在这种情况下，" &移除，然后将字符串中下字符下划线。  如果静态控件是包含该功能不需要的文本，**SS\_NOPREFIX** 可能添加。  此静态控件样式可能随任何定义的静态控件。  可以使用或运算符，则可以按位组合 **SS\_NOPREFIX** 与其他样式。  这是最常用，则在对话框的静态控件可能包含" &需要显示的文件名或其他字符串。  
  
-   当用户单击或双击控件时，父窗口发送**SS\_NOTIFY STN\_CLICKED**、**STN\_DBLCLK**、**STN\_DISABLE**和 **STN\_ENABLE** 则通知消息。  
  
-   **SS\_OWNERDRAW** 指定静态控件中的所有者负责绘制控件。  所有者窗口接收 `WM_DRAWITEM` 消息，只要控件需要绘制。  
  
-   **SS\_REALSIZEIMAGE** 可防止有 **SS\_ICON** 或 **SS\_BITMAP** \) 的静态样式的图标或位图 \(即控件静态控件的大小，以便在加载或绘制。  如果图标或位图比目标区域大，则图像将被剪切。  
  
-   **SS\_RIGHT** 指定简单的外接矩形并显示特定文本右对齐在矩形。  在显示之前，文本格式。  将扩展超出行尾的 Word 自动换到下右对齐的行的开头。  
  
-   **SS\_RIGHTJUST** 指定静态控件的右下角。**SS\_BITMAP** 或 **SS\_ICON** 将保持固定样式的是，当控件的大小时。  仅调整顶部和左侧满足新的位图或图标。  
  
-   **SS\_SIMPLE** 指定简单的矩形并显示单行文本刷新左在矩形。  文本行不能使用缩写或修改。\(控件的父窗口或对话框无法处理 `WM_CTLCOLOR` 消息。\)  
  
-   **SS\_SUNKEN** 在静态控件周围绘制了一个半凹下转到的边界。  
  
-   **SS\_USERITEM** 指定用户定义的项。  
  
-   **SS\_WHITEFRAME** 指定使用框架的一个框与和颜色绘制窗口背景相同。  默认值为白色。  
  
-   **SS\_WHITERECT** 指定要用于填充矩形的颜色填充背静屏幕。  默认值为白色。  
  
-   **SS\_WORDELLIPSIS** 被截断不适合的文本并添加省略号。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../Topic/CStatic::Create.md)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [Static Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb760773)