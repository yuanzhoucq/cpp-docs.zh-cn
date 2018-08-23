---
title: 对话框编辑器选项卡，工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a528ece23301f707b267ed7cefd30649b34c5e60
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613507"
---
# <a name="dialog-editor-tab-toolbox"></a>“对话框编辑器”选项卡，工具箱

**对话框编辑器**选项卡中将显示[工具箱窗口](/visualstudio/ide/reference/toolbox)工作时**对话框**编辑器。 若要将控件添加到新的对话框中，将控件从**工具箱**到要创建的对话框 (有关详细信息，请参阅[将控件添加到对话框](adding-a-control-to-a-dialog-box.md))。 然后，可以移动控件或更改其大小和形状。

提供的标准控件**工具箱**是：

- [按钮控件](../mfc/reference/cbutton-class.md)

- [复选框控件](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [组合框控件](../mfc/reference/ccombobox-class.md)

- [编辑控件](../mfc/reference/cedit-class.md)

- 分组框

- [列表框控件](../mfc/reference/clistbox-class.md)

- [单选按钮控件](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [静态文本控件](../mfc/reference/cstatic-class.md)

- [图片控件](../mfc/reference/cpictureholder-class.md)

- [Rich Edit 2.0 控件](../mfc/using-cricheditctrl.md)

- [滚动条控件](../mfc/reference/cscrollbar-class.md)

[Windows 公共控件](../mfc/controls-mfc.md)推出**工具箱**提供应用程序中的增强的功能。 它们包括：

- [滑块控件](../mfc/slider-control-styles.md)

- [数值调节钮控件](../mfc/using-cspinbuttonctrl.md)

- [进度控件](../mfc/styles-for-the-progress-control.md)

- [热键控件](../mfc/using-a-hot-key-control.md)

- [列表控件](../mfc/list-control-and-list-view.md)

- [树控件](../mfc/tree-control-styles.md)

- [选项卡控件](../mfc/tab-controls-and-property-sheets.md)

- [动画控件](../mfc/using-an-animation-control.md)

- [日期时间选取器控件](../mfc/creating-the-date-and-time-picker-control.md)

- [月历控件](../mfc/month-calendar-control-examples.md)

- [IP 地址控件](../mfc/reference/cipaddressctrl-class.md)

- [扩展的组合框控件](../mfc/creating-an-extended-combo-box-control.md)

- [自定义控件](custom-controls-in-the-dialog-editor.md)

可以通过选择向对话框添加自定义控件**自定义控件**中的图标**工具箱**并将其拖到您的对话框。 若要添加**Syslink**控制，添加自定义控件，然后更改控件的**类**属性设置为**Syslink**。 这将导致属性刷新并显示**Syslink**控件属性。 有关 MFC 包装类的信息，请参阅[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

你也可以[将 ActiveX 控件添加到对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

此外可以自定义**工具箱**窗口以方便使用。 有关详细信息，请参阅[使用工具箱](/visualstudio/ide/using-the-toolbox)。

有关使用的详细信息**RichEdit 1.0**控件使用 MFC，请参阅[RichEdit 1.0 控件使用 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)  
[控件类](../mfc/control-classes.md)  
[对话框类](../mfc/dialog-box-classes.md)  
[滚动条样式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)  
[Rich Edit 控件示例](../mfc/rich-edit-control-examples.md)  
[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)