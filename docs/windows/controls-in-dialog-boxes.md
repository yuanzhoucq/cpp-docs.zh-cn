---
title: 对话框控件（C++） |Microsoft Docs
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
ms.openlocfilehash: c79021387de2c8bc8f7f106a93797b7efb07d6df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160406"
---
# <a name="dialog-box-controls-c"></a>对话框控件（C++）

您可以使用 "[工具箱" 窗口](/visualstudio/ide/reference/toolbox)中的 "**对话框编辑器**" 选项卡将控件添加到对话框中，该选项卡允许您选择所需的控件并将其拖到对话框中。 默认情况下，"**工具箱**" 窗口设置为 "自动隐藏"。 当**对话框编辑器**处于打开状态时，它将显示为解决方案左边距上的一个选项卡。 不过，您可以通过选择窗口右上角的 "**自动隐藏**" 按钮，将 "**工具箱**" 窗口固定到位置。 有关如何控制此窗口的行为的详细信息，请参阅[窗口管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要将控件添加到对话框、重定位现有控件或将控件从一个对话框移到另一个对话框，最快的方法是使用拖放方法。 控件的位置以点线轮廓，直到将其放入对话框中。 当使用拖放方法将控件添加到对话框中时，将为控件提供适合该类型控件的标准高度。

向对话框添加控件或将其重定位时，其最终位置可能由参考线或边距确定，或是否打开了布局网格。

将控件添加到对话框后，可以在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中更改属性，例如其标题。 还可以选择多个控件，并同时更改它们的属性。

有关**对话框编辑器**的详细信息，请参阅如何[添加、编辑或删除控件](adding-editing-or-deleting-controls.md)、[布局控件](../windows/arrangement-of-controls-on-dialog-boxes.md)以及[定义控件访问和值](../windows/defining-mnemonics-access-keys.md)。

有关控件和对话框的详细信息，请参阅[控件类](../mfc/control-classes.md)、[对话框类](../mfc/dialog-box-classes.md)和[滚动条样式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)。

带有默认事件的**工具箱**中可用的标准控件如下：

|控件名称|默认事件|
|---|---|
|[Button 控件](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[复选框控件](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[组合框控件](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[编辑控件](../mfc/reference/cedit-class.md)|EN_CHANGE|
|分组框|（不适用）|
|[列表框控件](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[单选按钮控件](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[静态文本控件](../mfc/reference/cstatic-class.md)|（不适用）|
|[图片控件](../mfc/reference/cpictureholder-class.md)|（不适用）|
|[Rich Edit 2.0 控件](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[滚动条控件](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> 有关将**RichEdit 1.0**控件与 mfc 一起使用的详细信息，请参阅[将 RichEdit 1.0 控件与 Mfc](../windows/using-the-richedit-1-0-control-with-mfc.md)和[Rich Edit 控件](../mfc/rich-edit-control-examples.md)结合使用。

"**工具箱**" 中提供的[Windows 公共控件](../mfc/controls-mfc.md)可提供更多功能：

|控件名称|默认事件|
|---|---|
|[滑块控件](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[陀螺旋控件](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[进度控件](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[热键控件](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[列表控件](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[树控件](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[选项卡控件](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[动画控件](../mfc/using-an-animation-control.md)|ACN_START|
|[日期时间选取器控件](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[月历控件](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP 地址控制](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[扩展组合框控件](../mfc/creating-an-extended-combo-box-control.md)||
|自定义控件|TTN_GETDISPINFO|

## <a name="custom-controls"></a>自定义控件

通过**对话框编辑器**，您可以在对话框模板中使用现有的自定义控件或用户控件。

> [!NOTE]
> 此意义上的自定义控件不会与 ActiveX 控件混淆。 ActiveX 控件有时称为 OLE 自定义控件。 此外，请不要将这些控件与 Windows 中的所有者描述的控件混淆。

此功能旨在允许使用除 Windows 提供的控件之外的控件。 在运行时，控件与窗口类（与C++类不同）相关联。 完成相同任务的一种更常见的方法是在对话框中安装任何控件，如静态控件。 然后在运行时，在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数中删除该控件，并将其替换为你自己的自定义控件。

> [!NOTE]
> 这是一种旧技术。 现在，在大多数情况下，建议编写 ActiveX 控件或将 Windows 公共控件划分为子类。

对于这些自定义控件，限制为：

- 设置对话框中的位置。

- 键入标题。

- 标识控件的 Windows 类的名称，因为应用程序代码必须按照此名称注册控件。

- 键入设置控件样式的32位十六进制值。

- 设置扩展样式。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[对话框编辑器](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
