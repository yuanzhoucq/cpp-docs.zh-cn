---
title: "列表框样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LBS_STANDARD
- LBS_NODATA
- LBS_OWNERDRAWVARIABLE
- LBS_EXTENDEDSEL
- LBS_USETABSTOPS
- LBS_WANTKEYBOARDINPUT
- LBS_NOTIFY
- LBS_DISABLENOSCROLL
- LBS_HASSTRINGS
- LBS_NOREDRAW
- LBS_NOSEL
- LBS_NOINTEGRALHEIGHT
- LBS_MULTICOLUMN
- LBS_SORT
- LBS_MULTIPLESEL
- LBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- LBS_NOSEL constant
- LBS_NOREDRAW constant
- LBS_HASSTRINGS constant
- LBS_OWNERDRAWFIXED constant
- LBS_WANTKEYBOARDINPUT constant
- LBS_STANDARD constant
- LBS_MULTIPLESEL constant
- LBS_OWNERDRAWVARIABLE constant
- LBS_DISABLENOSCROLL constant
- LBS_NODATA constant
- list boxes, styles
- LBS_EXTENDEDSEL constant
- LBS_MULTICOLUMN constant
- LBS_NOTIFY constant
- LBS_USETABSTOPS constant
- LBS_NOINTEGRALHEIGHT constant
- LBS_SORT constant
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8e038e5cef50bd15df85c9d7f8b213b54ed03825
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="list-box-styles"></a>列表框样式
-   **LBS_DISABLENOSCROLL**列表框中显示一个禁用的垂直滚动条列表框中不包含足够的项，以向下滚动。 如果不使用此样式，则当列表框未包含足够的项时，将会隐藏滚动条。  
  
-   **LBS_EXTENDEDSEL**用户可以选择多个项目使用 SHIFT 键和鼠标或特定组合键。  
  
-   **LBS_HASSTRINGS**指定一个所有者描述列表框，其中包含由字符串构成的项。 列表框保留字符串的内存和指针，以便应用程序可使用 `GetText` 成员函数检索特定项的文本。  
  
-   **LBS_MULTICOLUMN**指定水平滚动的多列的列表框。 `SetColumnWidth` 成员函数将设置列的宽度。  
  
-   **LBS_MULTIPLESEL**每次用户单击或双击字符串时，将切换字符串选择。 可以选择任意数量的字符串。  
  
-   **LBS_NODATA**指定无数据列表框。 当列表框中的项数超出一千时，请指定此样式。 无数据列表框还必须具有**LBS_OWNERDRAWFIXED**样式，但不是能有**LBS_SORT**或**LBS_HASSTRINGS**样式。  
  
     无数据列表框类似于所有者描述的列表框，但它不包含项的字符串或位图数据。 用于添加、插入或删除项的命令始终会忽略任何给定的项数据；在列表框内查找字符串的请求始终会失败。 必须绘制某个项时，系统会向所有者窗口发送 `WM_DRAWITEM` 消息。 随 `DRAWITEMSTRUCT` 消息传递的 `WM_DRAWITEM` 结构的 itemID 成员将指定要绘制的项的行号。 无数据列表框不发送 `WM_DELETEITEM` 消息。  
  
-   **LBS_NOINTEGRALHEIGHT**列表框的大小是完全创建列表框时，应用程序所指定的大小。 通常，Windows 会调整列表框的大小，以使列表框不会只显示部分项。  
  
-   **LBS_NOREDRAW**进行更改时，不会更新列表框中显示。 通过发送，可以随时更改此样式**WM_SETREDRAW**消息。  
  
-   **LBS_NOSEL**指定列表框包含可查看但未选中的项。  
  
-   **LBS_NOTIFY**每当用户单击或双击某个字符串时，父窗口接收到输入的消息。  
  
-   **LBS_OWNERDRAWFIXED**列表框的所有者负责绘制其内容; 列表框中的项的高度相同。  
  
-   **LBS_OWNERDRAWVARIABLE**列表框的所有者负责绘制其内容; 列表框中的项高度。  
  
-   **LBS_SORT**列表框中的字符串按字母顺序排序。  
  
-   **LBS_STANDARD**列表框中的字符串按字母顺序排列，并且每当用户单击或双击某个字符串时，父窗口接收到输入的消息。 列表框包含各边的边框。  
  
-   **LBS_USETABSTOPS**允许列表框来识别并展开制表符，在绘制其字符串时。 默认制表符位置是 32 个对话框单位。 （对话框单位是一个水平或垂直的距离。 一个水平对话框单位等于当前对话框基本宽度单位的四分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 **GetDialogBaseUnits** Windows 函数以像素为单位返回当前对话框基本单位。)此样式不应使用与**LBS_OWNERDRAWFIXED**。  
  
-   **LBS_WANTKEYBOARDINPUT**列表框的所有者将会收到`WM_VKEYTOITEM`或`WM_CHARTOITEM`消息时，只要用户按键当列表框具有输入焦点。 这允许应用程序对键盘输入执行特殊处理。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../../mfc/reference/clistbox-class.md#create)   
 [列表框样式](http://msdn.microsoft.com/library/windows/desktop/bb775149)


