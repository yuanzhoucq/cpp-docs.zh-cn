---
title: "列表框样式 | Microsoft Docs"
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
  - "LBS_STANDARD"
  - "LBS_NODATA"
  - "LBS_OWNERDRAWVARIABLE"
  - "LBS_EXTENDEDSEL"
  - "LBS_USETABSTOPS"
  - "LBS_WANTKEYBOARDINPUT"
  - "LBS_NOTIFY"
  - "LBS_DISABLENOSCROLL"
  - "LBS_HASSTRINGS"
  - "LBS_NOREDRAW"
  - "LBS_NOSEL"
  - "LBS_NOINTEGRALHEIGHT"
  - "LBS_MULTICOLUMN"
  - "LBS_SORT"
  - "LBS_MULTIPLESEL"
  - "LBS_OWNERDRAWFIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LBS_DISABLENOSCROLL 常量"
  - "LBS_EXTENDEDSEL 常量"
  - "LBS_HASSTRINGS 常量"
  - "LBS_MULTICOLUMN 常量"
  - "LBS_MULTIPLESEL 常量"
  - "LBS_NODATA 常量"
  - "LBS_NOINTEGRALHEIGHT 常量"
  - "LBS_NOREDRAW 常量"
  - "LBS_NOSEL 常量"
  - "LBS_NOTIFY 常量"
  - "LBS_OWNERDRAWFIXED 常量"
  - "LBS_OWNERDRAWVARIABLE 常量"
  - "LBS_SORT 常量"
  - "LBS_STANDARD 常量"
  - "LBS_USETABSTOPS 常量"
  - "LBS_WANTKEYBOARDINPUT 常量"
  - "列表框, 样式"
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 列表框样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   当列表框不包含足够的项滚动时，**LBS\_DISABLENOSCROLL** 列表框显示一个禁用的垂直滚动条。  若无此样式，当列表框不包含足够的项时，滚动条将隐藏。  
  
-   使用 Shift 键和鼠标或特定组合键**LBS\_EXTENDEDSEL**，用户可以选择多个项。  
  
-   **LBS\_HASSTRINGS** 指定包含字符串的项所有者描述列表框。  列表框保留内存和字符串的指针，该应用程序可使用 `GetText` 成员函数检索文本特定项的。  
  
-   **LBS\_MULTICOLUMN** 指定水平滚动的多列列表框。  `SetColumnWidth` 成员函数将列的宽度。  
  
-   每次用户单击或双击字符串，选择**LBS\_MULTIPLESEL** 字符串之间切换。  任意数量的字符串进行选择。  
  
-   **LBS\_NODATA** 指定无数据列表框。  当计数，列表中将多项一次，指定此样式。  无数据列表框还必须具有 **LBS\_OWNERDRAWFIXED** ，样式，但无法具有 **LBS\_SORT** 或 **LBS\_HASSTRINGS** 样式。  
  
     由数据类似于列表框的所有者描述列表框，但不包含字符串或位图数据的项。  命令添加，插入或删除项始终忽略任何指定项数据；请求始终失败查找在列表框内的字符串。  当必须绘制时，系统发送 `WM_DRAWITEM` 消息。项所有者窗口。  `DRAWITEMSTRUCT` 结构的 itemID 成员将用 `WM_DRAWITEM` 消息指定要绘制项的行号。  无数据列表框不发送 `WM_DELETEITEM` 消息。  
  
-   在创建列表框，**LBS\_NOINTEGRALHEIGHT** 列表框的尺寸正确应用程序指定的范围。  通常，窗口大小列表框，使列表框部分不显示项。  
  
-   当更改时，**LBS\_NOREDRAW** 列表框显示未更新。  此样式可通过发送 **WM\_SETREDRAW** 消息随时更改。  
  
-   **LBS\_NOSEL** 指定列表框包含中查看，但不会选择的项。  
  
-   **LBS\_NOTIFY** 父窗口接收输入消息，每当用户单击或双击字符串。  
  
-   **LBS\_OWNERDRAWFIXED** 列表框的所有者负责绘制其内容运行；在列表框项的是同一高度。  
  
-   **LBS\_OWNERDRAWVARIABLE** 列表框的所有者负责绘制其内容运行；在列表框项的高度是可变的。  
  
-   在列表框的**LBS\_SORT**字符串按字母顺序排序。  
  
-   在列表框的**LBS\_STANDARD** 字符串按字母顺序排序，并且，父窗口接收输入消息，每当用户单击或双击字符串。  列表框中包含在任何范围。  
  
-   当绘制制表符字符串时，使能识别并展开制表符。**LBS\_USETABSTOPS** 列表框  默认选项卡位置 32 是对话框单位。对话框单位 \(A 是一个水平或垂直距离。  水平的对话框单位相等到当前基本宽度对话框单位的四分之一。  对话框单位计算基于当前基础系统字体的高度和宽度。  **GetDialogBaseUnits** Windows 函数返回在像素的当前基本单元对话框。）不应使用此样式与 **LBS\_OWNERDRAWFIXED**。  
  
-   **LBS\_WANTKEYBOARDINPUT** 列表框的所有者接收 `WM_VKEYTOITEM` 或 `WM_CHARTOITEM` 消息，只要用户按键，当列表框具有输入焦点时。  这允许您的应用程序处理在执行特定类型。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../Topic/CListBox::Create.md)   
 [List Box Styles](http://msdn.microsoft.com/library/windows/desktop/bb775149)