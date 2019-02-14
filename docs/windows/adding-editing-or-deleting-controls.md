---
title: 添加、编辑或删除控件
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
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
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 648ac3329409ba221881f75eaa51e1779091b0f0
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264863"
---
# <a name="adding-editing-or-deleting-controls"></a>添加、编辑或删除控件

使用**对话框**编辑器中，您可以添加、 重设大小、 编辑和删除控件在对话框中的。 此外可以编辑的控件，如其 ID 属性或者它是否最初可见在运行时。

**对话框编辑器**选项卡中将显示[工具箱窗口](/visualstudio/ide/reference/toolbox)工作时**对话框**编辑器。 此外可以自定义**工具箱**窗口以方便使用。 有关详细信息，请参阅[使用工具箱](/visualstudio/ide/using-the-toolbox)并[显示或隐藏工具箱窗口](showing-or-hiding-the-dialog-editor-toolbar.md)。

可以使用中的快捷菜单**对话框中**编辑器来快速添加注册 ActiveX 控件到对话框中，并且可以添加到 ActiveX 控件**工具箱**以便快速访问。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-add-a-control"></a>若要添加控件

若要将控件添加到新的对话框中，将控件从**工具箱**到你要创建的对话框。 然后，可以移动控件或更改其大小和形状。

可以通过选择向对话框添加自定义控件**自定义控件**中的图标**工具箱**并将其拖到您的对话框。 若要添加**Syslink**控制，添加自定义控件，然后更改控件的**类**属性设置为**Syslink**。 此操作将导致属性刷新并显示**Syslink**控件属性。 有关 MFC 包装类的信息，请参阅[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

### <a name="to-add-a-control-to-a-dialog-box"></a>将控件添加到对话框

1. 确保对话框选项卡式窗口是编辑器框架中的当前文档。 如果对话框不是当前文档，不会看到**对话框编辑器选项卡**中**工具箱**。

1. 上**对话框编辑器**选项卡**工具箱**窗口中，选择所需的控件，然后：

   选择在你想要将控件放置的位置的对话框。 其中已选择显示该控件。

   \- 或 -

   拖放到该控件从**工具箱**窗口到您的对话框上的位置。

   \- 或 -

   双击该控件中的**工具箱**窗口 （显示在对话框中），然后重新定位到所需的位置的控件。

### <a name="to-add-multiple-controls"></a>若要添加多个控件

1. 在按下**Ctrl**密钥，请选择中的控件**工具箱**窗口。

1. 发行**Ctrl**键并选择对话框的无数次，你想要添加特定的控件。

1. 按**Esc**停止放置控件。

### <a name="to-size-a-control-while-you-add-it"></a>若要调整控件的大小，而将其添加

1. 选择一个控件中的**工具箱**窗口。

1. 将光标 （它显示为十字线） 想要在对话框中，新的控件的左上角。

1. 选择并按住鼠标按钮，若要定位到对话框的上的控件的左上角，然后拖动光标向右和向下直到控件所需的大小。

   > [!NOTE]
   > 实际上，您可以定位任何要绘制的控件的四个角。 此过程作为示例使用左上角。

1. 释放鼠标按钮。 到你指定的大小在该对话框会使该控件。

   > [!TIP]
   > 您可以通过将调整大小控点移动控件的边框上将其放到该对话框后调整控件的大小。 有关详细信息，请参阅[调整单个控件的](../windows/sizing-individual-controls.md)。

### <a name="to-add-an-activex-control"></a>若要添加的 ActiveX 控件

Visual Studio 使你可以将 ActiveX 控件插入对话框中。 有关详细信息，请参阅[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)并[ActiveX 控件容器](../mfc/activex-control-containers.md)。

**插入 ActiveX 控件**对话框中，您可以使用时将 ActiveX 控件插入到您的对话框[对话框编辑器](../windows/dialog-editor.md)。 此对话框包含以下属性：

|属性|描述|
|---|---|
|**ActiveX 控件**|显示 Active X 控件的列表。 从该对话框中插入控件不会生成一个包装类。 如果您需要一个包装器类，使用[类视图](/visualstudio/ide/viewing-the-structure-of-code)创建一个 (有关详细信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控件未显示在此对话框中，请尝试安装该控件根据供应商的说明。|
|**路径**|显示在其中找到 ActiveX 控件的文件。|

#### <a name="to-see-the-activex-controls-available"></a>若要查看可用的 ActiveX 控件

1. 在对话框编辑器中打开一个对话框。

1. 在对话框中的正文中，右键单击任意位置。

1. 在快捷菜单上，选择**插入 ActiveX 控件**。

   **插入 ActiveX 控件**对话框出现，其中显示你系统上的所有 ActiveX 控件。 在该对话框底部，会显示 ActiveX 控件文件的路径。

#### <a name="to-add-an-activex-control-to-a-dialog-box"></a>将 ActiveX 控件添加到对话框

1. 在中**插入 ActiveX 控件**对话框框中，选择你想要添加到对话框并选择的控件**确定**。

   该控件会出现在对话框中，可以在其中编辑它或为它创建处理程序，就如同处理任何其他控件一样。

   > [!NOTE]
   > 你可以添加到 ActiveX 控件**工具箱**以方便访问的窗口。

   > [!CAUTION]
   > 分发系统上的每个 ActiveX 控件可能并非都是合法的。 请参阅安装了控件的软件的许可协议，或与软件公司联系。

## <a name="to-edit-a-control"></a>若要编辑控件

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>若要编辑的控件或控件属性

1. 在对话框中，选择你想要修改的控件。

   > [!NOTE]
   > 如果选择多个控件，可以编辑仅对所选控件通用的属性。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，更改您的控件的属性。

   > [!NOTE]
   > 当您将设置**位图**按钮、 单选按钮或复选框控件等于属性**True**，BS_BITMAP 实现为您的控件的样式。 有关详细信息，请参阅[按钮样式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 将位图与控件相关联的示例，请参阅[CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 当你处于位图不会出现在您的控件**对话框**资源编辑器。

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>若要撤消对控件的属性的更改

1. 请确保在控件有焦点**对话框**编辑器。

1. 选择**撤消**从**编辑**菜单 (如果焦点在控件中当前不**撤消**命令将不可用)。

### <a name="to-edit-properties-for-an-activex-control"></a>若要编辑的 ActiveX 控件的属性

提供独立供应商的 ActiveX 控件可能都配备有其自己的属性和特征。 ActiveX 控件的属性显示在**属性**窗口。 此外，创建 ActiveX 控件的编写器的任何属性页会显示在**属性页**对话框中 (若要查看**属性页**特定的 ActiveX 控件，请单击**属性页**按钮[属性窗口](/visualstudio/ide/reference/properties-window))。

ActiveX 控件，具体取决于为 ActiveX 控件的一部分的属性表的属性页中显示各个选项卡。

> [!NOTE]
> 以下过程适用于使用属性页编辑 ActiveX 控件。 此外可以浏览，并在新编辑 ActiveX 属性**属性**窗口。

1. 选择**ActiveX**控件。

1. 上**视图**菜单中，选择**属性页**并查看属性。

1. 根据需要在属性页中进行更改。

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定义（非按钮）对话框控件的成员变量

要定义除按钮外的任何对话框控件的成员变量，可以使用以下方法。

> [!NOTE]
> 此过程仅适用于 MFC 项目中的对话框控件。 ATL 项目应使用**新的 Windows 消息和事件处理程序**对话框。 有关详细信息，请参阅[与用户界面对象关联的消息类型](../mfc/reference/message-types-associated-with-user-interface-objects.md)，[编辑消息处理程序](../mfc/reference/editing-a-message-handler.md)，和[为反映消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. 在中[对话框编辑器](../windows/dialog-editor.md)，选择一个控件。

1. 同时按下**Ctrl**密钥，请双击对话框控件。

   [添加成员变量向导](../ide/add-member-variable-wizard.md)出现。

1. 键入在相应的信息**添加成员变量**向导。 有关详细信息，请参阅[对话框数据交换](../mfc/dialog-data-exchange.md)。

1. 选择**确定**回到**对话框**编辑器。

   > [!TIP]
   > 若要从任何对话框控件跳转到其现有的处理程序，请双击该控件。

此外可以使用**成员变量**选项卡[MFC 类向导](../mfc/reference/mfc-class-wizard.md)添加为指定类的新成员变量并查看已定义的成员变量。

## <a name="to-delete-a-control"></a>若要删除控件

在对话框中，选择控件，然后按**删除**密钥。

   \- 或 -

上**编辑**菜单中，选择**删除**。

   > [!TIP]
   > 使用时**对话框**编辑器中的，在许多情况下，您可以单击鼠标右键以显示常用命令的快捷菜单。

## <a name="known-issue"></a>已知问题

将公共控件或 rich edit 控件添加到对话框中之后, 它不会出现时测试对话框的或对话框中本身不会显示。

若要查看问题的一个示例：

1. 创建 Win32 项目，修改应用程序设置，因此创建 Windows 应用程序 （不是一个控制台应用程序）。

1. 在中[资源视图](../windows/resource-view-window.md)，双击.rc 文件。

1. 在下，对话框选项中，双击**有关**框。

1. 添加**IP 地址控件**到对话框。

1. 保存并**全部重新生成**。

1. 执行该程序。

1. 在对话框中**帮助**菜单上，单击**有关**命令; 没有对话框框中显示。

目前，**对话框**编辑器不会自动将代码添加到你的项目时将下列公共控件或 rich edit 控件拖放到对话框。 也不会 Visual Studio 提供的错误或警告时出现此问题。 若要修复，请手动添加控件的代码。

||||
|-|-|-|
|滑块控件|树控件|日期时间选取器|
|数值调节钮控件|选项卡控件|月历|
|进度控件|动画控件|IP 地址控件|
|热键|Rich Edit 控件|扩展的组合框|
|列表控件|Rich Edit 2.0 控件|自定义控件|

若要使用公共控件出现在对话框中，您需要调用[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)或`AFXInitCommonControls`创建对话框的之前。

若要使用 RichEdit 控件，必须调用`LoadLibrary`。 有关详细信息，请参阅[有关 Rich Edit 控件](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中并[的格式文本编辑控件概述](../mfc/overview-of-the-rich-edit-control.md)。

> [!NOTE]
> 若要使用 MFC 使用 RichEdit 控件，必须首先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)加载 RichEdit 2.0 控件 (RICHED20。DLL)，或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)加载较旧的 RichEdit 1.0 控件 (RICHED32。DLL)。
>
> 可以使用当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件，但`CRichEditCtrl`不仅旨在支持 RichEdit 2.0 控件。 RichEdit 1.0 和 RichEdit 2.0 很相似，因为大多数方法起作用。 但请注意有一些差异的 1.0 和 2.0 的控件，因此，某些方法可能工作不正常或根本不起作用。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器](../windows/dialog-editor.md)<br/>
[对话框中的控件](controls-in-dialog-boxes.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->