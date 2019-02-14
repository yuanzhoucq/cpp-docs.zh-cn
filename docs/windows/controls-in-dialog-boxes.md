---
title: 控件在对话框 （c + +） |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f231a376b335d7fb711ef2039c13f49624e6bfb
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264837"
---
# <a name="controls-in-dialog-boxes-c"></a>控件在对话框 （c + +）

可以将控件添加到对话框框中使用[对话框编辑器选项卡](../windows/dialog-editor-tab-toolbox.md)中[工具箱窗口](/visualstudio/ide/reference/toolbox)，这样您就可以选择所需控件并将其拖到对话框的。 默认情况下，工具箱窗口设置为自动隐藏。 它为你的解决方案在左边距上的选项卡时显示对话框编辑器处于打开状态。 但是，您可以将固定**工具箱**通过单击位置到窗口**自动隐藏**窗口右上角的按钮。 有关如何控制此窗口的行为的详细信息，请参阅[窗口管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要将控件添加到对话框、 重新定位现有控件，或将控件从一个对话框中移动到另一个的最快方法是使用拖放方法。 直到放入对话框的点线中概述了控件的位置。 当您在使用拖放方法向对话框添加控件时，该控件提供适合于该类型的控件的标准高度。

当向对话框添加控件或重新定位时，其最终位置可能由参考线或边距，还是您拥有开启的布局网格。

向对话框添加控件后，可以更改属性，例如其标题[属性窗口](/visualstudio/ide/reference/properties-window)。 可以选择多个控件，并一次性更改它们的属性。

- [添加、编辑或删除控件](adding-editing-or-deleting-controls.md)

- [“选择”控件](../windows/selecting-controls.md)

- [调整单个控件的大小](../windows/sizing-individual-controls.md)

- [使控件具有相同的宽度、高度或大小](../windows/making-controls-the-same-width-height-or-size.md)

- [设置组合框及其下拉列表的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [向组合框控件添加值](../windows/adding-values-to-a-combo-box-control.md)

- [设置水平滚动条的宽度](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [定义助记键（访问键）](../windows/defining-mnemonics-access-keys.md)

- [指定对话框的位置和大小](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

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

有关使用的详细信息**RichEdit 1.0**控件使用 MFC，请参阅[RichEdit 1.0 控件使用 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)并[丰富编辑控件示例](../mfc/rich-edit-control-examples.md)。

[Windows 公共控件](../mfc/controls-mfc.md)推出**工具箱**提供应用程序中的增强的功能。 它们包括：

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

有关详细信息，请参阅[控件类](../mfc/control-classes.md)，[对话框类](../mfc/dialog-box-classes.md)，并[滚动条样式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

## <a name="custom-controls"></a>自定义控件

对话框编辑器使您可以使用现有的"自定义"或"user"控件在对话框模板中。

> [!NOTE]
> 在这个意义上的自定义控件将不使用 ActiveX 控件相混淆。 ActiveX 控件有时被称为 OLE 自定义控件。 此外，不要混淆 Windows 在所有者绘制的控件与这些控件。

此功能旨在使您可以用而非由 Windows 提供的控件。 在运行时，该控件是一个窗口类 （不完全相同的 c + + 类） 与相关联。 相同的任务是更常见的方法是安装任何控件，如静态控件在对话框中。 然后在在运行时， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数中，删除该控件并将其自己的自定义控件替换为。

这是旧技术。 今天被建议在大多数情况下编写的 ActiveX 控件或 Windows 公共控件的子类。

对于这些自定义控件，仅限于：

- 在对话框中设置的位置。

- 键入一个标题。

- 用于标识控件的 Windows 类 （应用程序代码必须使用此名称注册控件） 的名称。

- 键入一个 32 位十六进制值，该值设置控件的样式。

- 设置扩展的样式。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[控件](../mfc/controls-mfc.md)<br/>