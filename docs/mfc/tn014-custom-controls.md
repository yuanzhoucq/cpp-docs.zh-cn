---
title: "TN014：自定义控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义控件 [MFC]"
  - "TN014"
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# TN014：自定义控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明自定义和自绘图控件的 MFC 支持。  它还描述动态的 subclassing，并描述[CWnd](../mfc/reference/cwnd-class.md)对象和`HWND`之间的关系。  
  
 MFC 示例应用程序CTRLTEST 阐释如何使用许多自定义控件。  提供 MFC 泛型示例 [CTRLTEST](../top/visual-cpp-samples.md) 和联机帮助查看源代码。  
  
## 所有者描述菜单\/控件  
 通过使用 Windows 消息，窗口为所有者描述和菜单提供支持。  父窗口的任何控件或菜单接收这些消息并响应调用的函数。  您可以重写这些函数以自定义所有者描述控件或菜单的可视外观和行为。  
  
 MFC 直接支持使用下列函数的所有者描述：  
  
-   [CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)  
  
-   [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)  
  
-   [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)  
  
-   [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)  
  
 您可以在`CWnd` 派生类中重写这些函数以实现自定义绘制行为。  
  
 此方法不会产生可重用的代码。  如果有两个相同的控件在两个不同的 `CWnd` 类，则必须在两个位置实现自定义控件行为。  MFC 支持的自我绘制控件结构解决此问题。  
  
## 自绘制控件和菜单  
 MFC 为所有者描述标准消息提供默认实现 \(在 `CWnd` 和[CMenu](../mfc/reference/cmenu-class.md)类\)。  此实现将默认解码对控件或菜单的所有者描述参数和委托所有者描述信息。  这称为自我绘制，因为绘制代码在控件或菜单类中，不在所有者窗口。  
  
 通过使用自绘制控件可生成可重用控件类，该类为显示控件使用所有者描述语义。  绘制控件的代码在控件类，而不是它的父级。  这是一种面向对象的方法对自定义控件编程。  将函数添加下面列表到自绘制类：  
  
-   对于自绘制按钮：  
  
    ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw this button  
    ```  
  
-   对于自绘制菜单：  
  
    ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this menu  
    ```  
  
-   对于自绘制列表框：  
  
    ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this list box  
  
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this list box  
    ```  
  
-   对于自绘制组合框：  
  
    ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this combo box  
  
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this combo box  
    ```  
  
 有关所有者结构的详细信息 \([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md), [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md), [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md)和 [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)\) ，请分别参见  `CWnd::OnDrawItem`、`CWnd::OnMeasureItem`、`CWnd::OnCompareItem`和 `CWnd::OnDeleteItem`的 MFC文档。  
  
## 使用自绘制控件和菜单  
 对于自绘制菜单，您必须重写 `OnMeasureItem` 和 `OnDrawItem` 方法。  
  
 对于自描述列表框和组合框，必须重写 `OnMeasureItem` 和 `OnDrawItem`。  必须为列表框指定 `LBS_OWNERDRAWVARIABLE` 样式或为对话框模板中的组合框指定 `CBS_OWNERDRAWVARIABLE` 样式。  `OWNERDRAWFIXED` 样式在自绘制项中无效，因为固定项高度在自绘制控件附加到列表框之前以及确定。\(可以使用方法 [CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md) 和[CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md) 解决此限制。\)  
  
 切换到 `OWNERDRAWVARIABLE` 将强制系统样式应用于 `NOINTEGRALHEIGHT` 控件。  因为控件不能使用可变大小的项计算一个不可或缺高度，`INTEGRALHEIGHT` 忽略默认样式，控件始终为 `NOINTEGRALHEIGHT`。  如果项是固定的高度，可以防止部分项绘制通过指定控件的大小为项大小的整数倍数。  
  
 对于`LBS_SORT` 或 `CBS_SORT` 样式的自描述列表框和组合框，必须重写 `OnCompareItem` 方法。  
  
 对于自描述列表框和组合框，`OnDeleteItem` 通常不重写。  如果您想做任何特殊处理，您可以重写 `OnDeleteItem`。  这对应的一个例子是附加内存或其他资源存储在每个列表框或组合框项。  
  
## 自我绘制控件和菜单的示例  
 MFC 泛型示例 [CTRLTEST](../top/visual-cpp-samples.md) 提供自绘制菜单和自绘制列表框的示例。  
  
 自我绘制按钮的最典型示例是一位图按钮。  位图按钮显示为不同状态：一个、两个或三个位图图像的按钮。  在MFC类[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)中提供一个示例。  
  
## 动态的 Subclassing  
 有时您需要更改已存在对象的功能。  在创建之前，之前的例子要求您自定义控件。  动态的 subclassing 用于自定义已创建的控件。  
  
 Subclassing is replacement 窗口中 [WndProc](http://msdn.microsoft.com/zh-cn/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) 使用自定义 `WndProc` 并调用旧的 `WndProc` Windows 术语默认功能。  
  
 使用 C\+\+ 类派生不会混淆。  为了说明，在窗口对象模型中， C\+\+ 把*基类* 和 *派生类* 叫做相似的 *超类* 和 *子类*。  使用 MFC 和 Windows subclassing， C\+\+ 派生在功能上是等效的，只不过 C\+\+不支持动态的 subclassing。  
  
 `CWnd` 类提供在 C\+\+ 对象 \(派生自`CWnd`\) 和Windows 窗口对象\(`HWND`\)之间的连接 。  
  
 具有这些相关的三种常见方式：  
  
-   `CWnd` 创建`HWND`。  您可以通过创建从 `CWnd`派生的类之后修改派生类中的行为。  当应用程序调用[CWnd::Create](../Topic/CWnd::Create.md)时，将创建 `HWND`。  
  
-   应用程序 附加一个`CWnd` 到现有的 `HWND`。  不修改现有窗口的行为。  这是一种委托情况，可能通过调用 [CWnd::Attach](../Topic/CWnd::Attach.md)，将现有`HWND`化名为 `CWnd` 对象。  
  
-   `CWnd` 附加到现有的 `HWND`，并且您可以修改类中的行为。  这称为动态的 subclassing，因为更改行为，和类一样，窗口在运行时对象。  
  
 使用方法 [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md)和 `` ，您可实现 动态subclassing 。  
  
 两例程附加`CWnd` 对象到现有的`HWND`。  `SubclassWindow` 直接使用 `HWND`。  `SubclassDlgItem` 是采用控件 ID和父窗口的帮助程序函数。  `SubclassDlgItem` 是为了附加 C\+\+ 对象到对话框控件而设计的，该控件创建自对话框模板。  
  
 有关何时使用 `SubclassWindow` 和 `SubclassDlgItem`的几个示例， 请参见[CTRLTEST](../top/visual-cpp-samples.md) 示例。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)