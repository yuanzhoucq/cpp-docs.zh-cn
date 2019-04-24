---
title: 对话框控件 (C++) |Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 563cf73299c00413889ada2520b1bf4fcd86f2be
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023693"
---
# <a name="dialog-box-controls-c"></a>对话框控件 (C++)

可以将控件添加到对话框框中使用**对话框编辑器**选项卡[工具箱窗口](/visualstudio/ide/reference/toolbox)，使您可以选择所需控件并将其拖到对话框的。 默认情况下**工具箱**窗口设置为自动隐藏。 它将显示为你的解决方案的左边距上的选项卡时**对话框编辑器**处于打开状态。 但是，您可以将固定**工具箱**到相应位置通过选择窗口**自动隐藏**窗口右上角的按钮。 有关如何控制此窗口的行为的详细信息，请参阅[窗口管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要将控件添加到对话框、 重新定位现有控件，或将控件从一个对话框中移动到另一个的最快方法是使用拖放方法。 直到放入对话框的点线中概述了控件的位置。 当您在使用拖放方法向对话框添加控件时，该控件提供适合于该类型的控件的标准高度。

当向对话框添加控件或重新定位时，其最终位置可能由参考线或边距，还是您拥有开启的布局网格。

向对话框添加控件后，可以更改属性，例如其标题[属性窗口](/visualstudio/ide/reference/properties-window)。 此外可以选择多个控件，并一次性更改它们的属性。

有关详细信息**对话框编辑器**，请参阅如何[添加、 编辑或删除控件](adding-editing-or-deleting-controls.md)，[布局控件](../windows/arrangement-of-controls-on-dialog-boxes.md)，和[定义控制访问权限和值](../windows/defining-mnemonics-access-keys.md).

控件和对话框的详细信息，请参阅[控件类](../mfc/control-classes.md)，[对话框类](../mfc/dialog-box-classes.md)，并[滚动条样式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

提供的标准控件**工具箱**事件是默认值：

|控件名称|默认事件|
|---|---|
|[按钮控件](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[复选框控件](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[组合框控件](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[编辑控件](../mfc/reference/cedit-class.md)|EN_CHANGE|
|分组框|（不适用于）|
|[列表框控件](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[单选按钮控件](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[静态文本控件](../mfc/reference/cstatic-class.md)|（不适用于）|
|[图片控件](../mfc/reference/cpictureholder-class.md)|（不适用于）|
|[Rich Edit 2.0 控件](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[滚动条控件](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> 有关使用的详细信息**RichEdit 1.0**控件使用 MFC，请参阅[RichEdit 1.0 控件使用 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)并[丰富编辑控件示例](../mfc/rich-edit-control-examples.md)。

[Windows 公共控件](../mfc/controls-mfc.md)推出**工具箱**以提供更多的功能是：

|控件名称|默认事件|
|---|---|
|[滑块控件](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[数值调节钮控件](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[进度控件](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[热键控件](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[列表控件](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[树控件](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[选项卡控件](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[动画控件](../mfc/using-an-animation-control.md)|ACN_START|
|[日期时间选取器控件](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[月历控件](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP 地址控件](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[扩展的组合框控件](../mfc/creating-an-extended-combo-box-control.md)||
|自定义控件|TTN_GETDISPINFO|

## <a name="custom-controls"></a>自定义控件

**对话框编辑器**使您可以使用现有的自定义或对话框模板中的用户控件。

> [!NOTE]
> 在这个意义上的自定义控件将不使用 ActiveX 控件相混淆。 ActiveX 控件有时被称为 OLE 自定义控件。 此外，不要混淆 Windows 在所有者绘制的控件与这些控件。

此功能旨在使您可以用而非由 Windows 提供的控件。 在运行时，控件所关联的窗口类 (不完全相同C++类)。 相同的任务是更常见的方法是安装任何控件，如静态控件在对话框中。 然后在在运行时， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数中，删除该控件并将其自己的自定义控件替换为。

> [!NOTE]
> 这是旧技术。 今天被建议在大多数情况下编写的 ActiveX 控件或 Windows 公共控件的子类。

对于这些自定义控件，仅限于：

- 在对话框中设置的位置。

- 键入一个标题。

- 由于应用程序代码必须通过此名称来注册该控件，用于标识控件的 Windows 类的名称。

- 键入一个 32 位十六进制值，该值设置控件的样式。

- 设置扩展的样式。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器](../windows/dialog-editor.md)<br/>

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->