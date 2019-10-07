---
title: TN014：自定义控件
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: 2960c5b8585519adb535e5611315ec4ececcf53e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511181"
---
# <a name="tn014-custom-controls"></a>TN014：自定义控件

此说明描述 MFC 对自定义和自我绘制控件的支持。 它还介绍动态子类化，并描述了[CWnd](../mfc/reference/cwnd-class.md)对象和`HWND`之间的关系。

MFC 示例应用程序 CTRLTEST 演示了如何使用许多自定义控件。 请参阅 MFC 常规示例[CTRLTEST](../overview/visual-cpp-samples.md)和联机帮助中的源代码。

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

MFC 为标准的所有者描述消息提供`CWnd`默认实现（在和[CMenu](../mfc/reference/cmenu-class.md)类中）。 此默认实现将解码所有者描述参数，并将所有者描述消息委派给控件或菜单。 这称为“自我描述”，因为描述代码位于控件或菜单的类中，而不是所有者窗口中。

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

有关所有者描述结构（[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)、 [MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)、 [COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)和[DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)）的详细信息`CWnd::OnDrawItem`， `CWnd::OnMeasureItem` `CWnd::OnCompareItem`请参阅、、和的MFC文档`CWnd::OnDeleteItem`分别。

## <a name="using-self-draw-controls-and-menus"></a>使用自我描述控件和菜单

对于自我描述菜单，您必须重写 `OnMeasureItem` 和 `OnDrawItem` 方法。

对于自我描述列表框和组合框，您必须重写 `OnMeasureItem` 和 `OnDrawItem`。 您必须为对话框模板中的组合框指定列表框或 CBS_OWNERDRAWVARIABLE 样式的 LBS_OWNERDRAWVARIABLE 样式。 OWNERDRAWFIXED 样式不能用于自绘制项，因为在自绘制控件附加到列表框之前确定了固定项的高度。 （可以使用方法[CListBox：： SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight)和[CComboBox：： SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight)来克服此限制。）

切换到 OWNERDRAWVARIABLE 样式会强制系统将 NOINTEGRALHEIGHT 样式应用于控件。 由于控件无法计算大小可变的项的整体高度，因此 INTEGRALHEIGHT 的默认样式将被忽略，并且控件始终为 NOINTEGRALHEIGHT。 如果项目的高度是固定的，则可通过指定控件大小为项目大小的整数倍数来防止描述部分项目。

对于具有 LBS_SORT 或 CBS_SORT 样式的自绘制列表框和组合框，您必须重写`OnCompareItem`方法。

对于自我描述列表框和组合框，一般不会重写 `OnDeleteItem`。 如果要执行任何特殊处理，您可重写 `OnDeleteItem`。 此操作可能适用的一种情况是，每个列表框或组合框项目与其他内存或其他资源一起存储。

## <a name="examples-of-self-drawing-controls-and-menus"></a>自我描述控件和菜单的示例

MFC 常规示例[CTRLTEST](../overview/visual-cpp-samples.md)提供自绘制菜单和自绘制列表框的示例。

自我描述按钮最典型的示例是位图按钮。 位图按钮是显示了不同状态的一个、两个或三个位图图像的按钮。 MFC 类[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)中提供了一个示例。

## <a name="dynamic-subclassing"></a>动态子类化

您偶尔需要更改已存在对象的功能。 之前的示例需要您在创建控件之前自定义控件。 利用动态子类化，您可自定义已经创建的控件。

子类化是 Windows 术语，用于将<xref:System.Windows.Forms.Control.WndProc%2A>窗口替换为自定义`WndProc`的，并为默认`WndProc`功能调用旧的。

这不应与 C++ 类派生混淆。 为了进行说明， C++术语 *"基类*" 和 "*派生类*" 类似于 Windows 对象模型中的*超类*和*子类*。 使用 MFC 的 C++ 派生和 Windows 子类化在功能上是相同的，只不过 C++ 不支持动态子类化。

`CWnd` 类提供了 C++ 对象（派生自 `CWnd`）与 Windows 窗口对象（称为 `HWND`）之间的连接。

它们有 3 种常见的相关方式：

- `CWnd` 将创建 `HWND`。 您可通过创建派生自 `CWnd` 的类来修改派生类的行为。 当`HWND`应用程序调用[CWnd：： Create](../mfc/reference/cwnd-class.md#create)时，创建。

- 应用程序会将 `CWnd` 附加到现有 `HWND`。 未修改现有窗口的行为。 这是委托的一种情况，并且可以通过调用[CWnd：：附加](../mfc/reference/cwnd-class.md#attach)来使现有`HWND` `CWnd`的成为对象的别名。

- `CWnd` 将附加到现有 `HWND`，并且您可修改派生类的行为。 这称为动态子类化，因为我们在运行时更改 Windows 对象的行为，并进而更改类。

可以通过使用[CWnd：： SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow)和[Cwnd：： SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)方法来实现动态子类化。

这两个例程均会将一个 `CWnd` 对象附加到现有 `HWND`。 `SubclassWindow` 将直接采用 `HWND`。 `SubclassDlgItem` 是采用控件 ID 和父窗口的帮助器函数。 `SubclassDlgItem` 旨在将 C++ 对象附加到通过对话框模板创建的对话控件。

有关何时使用`SubclassWindow`和`SubclassDlgItem`的几个示例，请参阅 [CTRLTEST 示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
