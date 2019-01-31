---
title: 将控件添加到对话框 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293619"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>将控件添加到对话框 （c + +）

**对话框编辑器**选项卡中将显示[工具箱窗口](/visualstudio/ide/reference/toolbox)工作时**对话框**编辑器。 若要将控件添加到新的对话框中，将控件从**工具箱**到你要创建的对话框。 然后，可以移动控件或更改其大小和形状。

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

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-add-a-control-to-a-dialog-box"></a>将控件添加到对话框

1. 确保对话框选项卡式窗口是编辑器框架中的当前文档。 如果对话框不是当前文档，不会看到**对话框编辑器选项卡**中**工具箱**。

1. 上**对话框编辑器**选项卡[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择所需的控件，然后：

   - 选择在你想要将控件放置的位置的对话框。 其中已选择显示该控件。

       \- 或 -

   - 拖放到该控件从**工具箱**窗口到您的对话框上的位置。

       \- 或 -

   - 双击该控件中的**工具箱**窗口 （显示在对话框中），然后重新定位到所需的位置的控件。

## <a name="to-add-multiple-controls"></a>若要添加多个控件

1. 在按下**Ctrl**密钥，请选择中的控件[工具箱窗口](/visualstudio/ide/reference/toolbox)。

1. 发行**Ctrl**键并选择对话框的无数次，你想要添加特定的控件。

1. 按**Esc**停止放置控件。

## <a name="to-size-a-control-while-you-add-it"></a>若要调整控件的大小，而将其添加

1. 选择一个控件中的[工具箱窗口](/visualstudio/ide/reference/toolbox)。

1. 将光标 （它显示为十字线） 想要在对话框中，新的控件的左上角。

1. 选择并按住鼠标按钮，若要定位到对话框的上的控件的左上角，然后拖动光标向右和向下直到控件所需的大小。

   > [!NOTE]
   > 实际上，您可以定位任何要绘制的控件的四个角。 此过程作为示例使用左上角。

1. 释放鼠标按钮。 到你指定的大小在该对话框会使该控件。

   > [!TIP]
   > 您可以通过将调整大小控点移动控件的边框上将其放到该对话框后调整控件的大小。 有关详细信息，请参阅[调整单个控件的](../windows/sizing-individual-controls.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[控件](../mfc/controls-mfc.md)<br/>
[控件类](../mfc/control-classes.md)<br/>
[对话框类](../mfc/dialog-box-classes.md)<br/>
[滚动条样式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Rich Edit 控件示例](../mfc/rich-edit-control-examples.md)<br/>
