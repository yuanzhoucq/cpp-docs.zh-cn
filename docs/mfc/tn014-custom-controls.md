---
title: TN014： 自定义控件 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls
dev_langs:
- C++
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bacba9ea15598e4c722682a081b64b80db34e00b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430561"
---
# <a name="tn014-custom-controls"></a>TN014：自定义控件

此说明描述 MFC 对自定义和自我绘制控件的支持。 它还介绍了动态子类化，并描述了之间的关系[CWnd](../mfc/reference/cwnd-class.md)对象和`HWND`s。

MFC 示例应用程序 CTRLTEST 演示了如何使用许多自定义控件。 请参阅 MFC 常规示例的源代码[CTRLTEST](../visual-cpp-samples.md)和联机帮助。

## <a name="owner-draw-controlsmenus"></a>所有者描述控件/菜单

Windows 通过使用 Windows 消息为所有者描述控件和菜单提供支持。 任何控件或菜单的父窗口都将接收这些消息并调用函数作为响应。 您可重写这些函数来自定义所有者描述控件或菜单的可视外观和行为。

MFC 通过下列函数直接支持所有者描述：

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

您可在 `CWnd` 派生类中重写这些函数来实现自定义描述行为。

此方法不会产生可重用的代码。 如果您在两个不同的 `CWnd` 类中具有两个相似的控件，则必须在这两个位置实现自定义控件行为。 MFC 支持的自我描述控件体系结构解决了此问题。

## <a name="self-draw-controls-and-menus"></a>自我描述控件和菜单

MFC 提供的默认实现 (在`CWnd`并[CMenu](../mfc/reference/cmenu-class.md)类) 为标准所有者描述消息。 此默认实现将解码所有者描述参数，并将所有者描述消息委派给控件或菜单。 这称为“自我描述”，因为描述代码位于控件或菜单的类中，而不是所有者窗口中。

通过使用自我描述控件，您可生成使用所有者描述语义显示控件的可重用控件类。 描述控件的代码位于控件类而不是其父级中。 这是面向对象来自定义控件编程的方式。 将下面的函数列表添加到自我描述类：

- 对于自我描述按钮：

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- 对于自我描述菜单：

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- 对于自我描述列表框：

    ```cpp
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this list box
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this list box

    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this list box if LBS_SORT
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this list box
    ```

- 对于自我描述组合框：

    ```cpp
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this combo box
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this combo box

    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this combo box if CBS_SORT
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this combo box
    ```

有关所有者描述结构的详细信息 ([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md)， [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md)， [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md)，和[DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md))，请参阅 MFC 文档`CWnd::OnDrawItem`， `CWnd::OnMeasureItem`， `CWnd::OnCompareItem`，并`CWnd::OnDeleteItem`分别。

## <a name="using-self-draw-controls-and-menus"></a>使用自我描述控件和菜单

对于自我描述菜单，您必须重写 `OnMeasureItem` 和 `OnDrawItem` 方法。

对于自我描述列表框和组合框，您必须重写 `OnMeasureItem` 和 `OnDrawItem`。 必须在对话框模板中指定的列表框的 LBS_OWNERDRAWVARIABLE 样式或组合框的 CBS_OWNERDRAWVARIABLE 样式。 OWNERDRAWFIXED 样式不会使用自我描述项目因为固定的项目高度确定之前自我描述控件附加到列表框。 (您可以使用的方法[CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight)并[CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight)来克服此限制。)

切换到可变样式将强制系统 NOINTEGRALHEIGHT 样式应用于该控件。 因为该控件无法计算使用可变大小的项目的整体高度，忽略 INTEGRALHEIGHT 的默认样式和控件始终是 NOINTEGRALHEIGHT。 如果项目的高度是固定的，则可通过指定控件大小为项目大小的整数倍数来防止描述部分项目。

对于自我描述列表框和组合框使用 LBS_SORT 或 CBS_SORT 样式，您必须重写`OnCompareItem`方法。

对于自我描述列表框和组合框，一般不会重写 `OnDeleteItem`。 如果要执行任何特殊处理，您可重写 `OnDeleteItem`。 此操作可能适用的一种情况是，每个列表框或组合框项目与其他内存或其他资源一起存储。

## <a name="examples-of-self-drawing-controls-and-menus"></a>自我描述控件和菜单的示例

MFC 常规示例[CTRLTEST](../visual-cpp-samples.md)提供自我描述菜单和自我描述列表框的示例。

自我描述按钮最典型的示例是位图按钮。 位图按钮是显示了不同状态的一个、两个或三个位图图像的按钮。 MFC 类中提供的此示例[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)。

## <a name="dynamic-subclassing"></a>动态子类化

您偶尔需要更改已存在对象的功能。 之前的示例需要您在创建控件之前自定义控件。 利用动态子类化，您可自定义已经创建的控件。

子类化是 Windows 术语，用于替换<xref:System.Windows.Forms.Control.WndProc%2A>为自定义窗口的`WndProc`并调用旧`WndProc`为默认功能。

这不应与 C++ 类派生混淆。 有关说明，c + + 术语*基类*和*派生的类*类似于*超类*并*子类*在 Windows 中对象模型。 使用 MFC 的 C++ 派生和 Windows 子类化在功能上是相同的，只不过 C++ 不支持动态子类化。

`CWnd` 类提供了 C++ 对象（派生自 `CWnd`）与 Windows 窗口对象（称为 `HWND`）之间的连接。

它们有 3 种常见的相关方式：

- `CWnd` 将创建 `HWND`。 您可通过创建派生自 `CWnd` 的类来修改派生类的行为。 `HWND`应用程序调用时，会创建[cwnd:: Create](../mfc/reference/cwnd-class.md#create)。

- 应用程序会将 `CWnd` 附加到现有 `HWND`。 未修改现有窗口的行为。 这是一种委托，可通过调用[CWnd::Attach](../mfc/reference/cwnd-class.md#attach)到别名的现有`HWND`到`CWnd`对象。

- `CWnd` 将附加到现有 `HWND`，并且您可修改派生类的行为。 这称为动态子类化，因为我们在运行时更改 Windows 对象的行为，并进而更改类。

可以通过使用方法来实现动态子类化[CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow)并[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)。

这两个例程均会将一个 `CWnd` 对象附加到现有 `HWND`。 `SubclassWindow` 将直接采用 `HWND`。 `SubclassDlgItem` 是采用控件 ID 和父窗口的帮助器函数。 `SubclassDlgItem` 旨在将 C++ 对象附加到通过对话框模板创建的对话控件。

请参阅[CTRLTEST](../visual-cpp-samples.md)何时使用的几个示例的示例`SubclassWindow`和`SubclassDlgItem`。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
