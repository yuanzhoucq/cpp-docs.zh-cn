---
title: 如何：添加、编辑或删除控件（C++）
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: a42a64f93d334c0b5c63b0eca1567e6964d0a3ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447217"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>如何：添加、编辑或删除控件（C++）

使用**对话框编辑器**，可以在对话框中添加、调整大小、编辑和删除控件。 你还可以编辑控件的属性（例如它的 ID），或在运行时其最初是否可见。

在**对话框编辑器**中工作时，"[工具箱" 窗口](/visualstudio/ide/reference/toolbox)中将显示 "**对话框编辑器**" 选项卡。 还可以自定义 "**工具箱**" 窗口，以便更轻松地使用。 有关详细信息，请参阅[使用工具箱](/visualstudio/ide/using-the-toolbox)和[显示或隐藏 "工具箱" 窗口](showing-or-hiding-the-dialog-editor-toolbar.md)。

> [!TIP]
> 使用**对话框编辑器**时，在许多情况下，您可以选择鼠标右键以显示常用命令的快捷菜单。

## <a name="add-controls"></a>添加控件

### <a name="to-add-a-control"></a>添加控件

1. 确保对话框选项卡式窗口是编辑器框架中的当前文档。 如果对话框不是当前文档，则不会在**工具箱**中看到 "**对话框编辑器" 选项卡**。

1. 在 "**工具箱**" 窗口的 "**对话框编辑器**" 选项卡上，选择所需的控件，然后执行以下任一操作：

   - 选择要在其中放置控件的位置的对话框，并在选择的位置显示控件。

   - 将控件从 "**工具箱**" 窗口拖放到对话框上的位置。 然后，您可以四处移动控件，或更改其大小和形状。

   - 双击 "**工具箱**" 窗口中的控件，该控件将显示在对话框中。 将该控件重新定位到所需的位置。

### <a name="to-add-multiple-controls"></a>添加多个控件

1. 按住**Ctrl**键的同时，在 "**工具箱**" 窗口中选择一个控件。

1. 松开**Ctrl**键并选择要添加特定控件的对话框多次。

1. 按**Esc**停止放置控件。

### <a name="to-size-a-control-while-you-add-it"></a>添加控件时调整其大小

1. 在 "**工具箱**" 窗口中选择一个控件。

1. 将光标显示为十字线，您希望新控件的左上角位于对话框中。

1. 选择并按住鼠标按钮，将控件的左上角定位在对话框上。 然后将光标向右和向下拖动，直到控件达到您所需的大小。

   > [!NOTE]
   > 您可以定位您要绘制的控件的四个角中的任意一个。 此过程使用左上角作为示例。

1. 释放鼠标按钮。 控件以您指定的大小在对话框上进行延伸。

> [!TIP]
> 可以通过移动控件边框上的调整大小控点，将控件放置到对话框上，然后调整控件的大小。 有关详细信息，请参阅[调整各个控件的大小](../windows/sizing-individual-controls.md)。

### <a name="to-add-a-custom-control"></a>添加自定义控件

您可以将自定义控件添加到对话框中。 在 "**工具箱**" 中选择 "**自定义控件**" 图标，并将其拖动到对话框中。 若要添加 `Syslink` 控件，请添加自定义控件，然后将控件的**Class**属性更改为 `Syslink`。 此操作将导致属性刷新并显示 `Syslink` 控件属性。 有关 MFC 包装类的信息，请参阅[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

## <a name="edit-controls"></a>编辑控件

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>编辑控件或控件的属性

1. 在对话框中，选择要修改的控件。

   > [!NOTE]
   > 如果选择多个控件，则只能编辑所选控件的通用属性。

1. 在[属性窗口](/visualstudio/ide/reference/properties-window)中，更改控件的属性。

   > [!NOTE]
   > 当您为按钮、单选按钮或复选框控件设置的**位图**属性等于**True**时，将为您的控件实现样式 BS_BITMAP。 有关详细信息，请参阅[按钮样式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 有关将位图与控件相关联的示例，请参阅[CButton：： SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 在**对话框编辑器**中时，不会在控件上显示位图。

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>撤消对控件的属性所做的更改

1. 请确保控件在**对话框编辑器**中具有焦点。

1. "切换到菜单"**编辑** > **撤消**。 如果焦点不在控件上，则 "**撤消**" 命令将不可用。

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定义（非按钮）对话框控件的成员变量

> [!NOTE]
> 此过程仅适用于 MFC 项目中的对话框控件。 ATL 项目应使用 "**新建 Windows 消息和事件处理程序**" 对话框。 有关详细信息，请参阅[与用户界面对象关联的消息类型](../mfc/reference/message-types-associated-with-user-interface-objects.md)、[编辑消息处理程序](../mfc/reference/editing-a-message-handler.md)和[为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。

1. 在[对话框编辑器](../windows/dialog-editor.md)中，选择一个控件。

1. 按住**Ctrl**键的同时双击对话框控件。

   此时将显示 "[添加成员变量向导](../ide/add-member-variable-wizard.md)"。

1. 在**添加成员变量**向导中键入适当的信息。 有关详细信息，请参阅[对话框数据交换](../mfc/dialog-data-exchange.md)。

1. 选择 **"确定"** 以返回到**对话框编辑器**。

> [!TIP]
> 若要从任何对话框控件跳转到其现有的处理程序，请双击该控件。

您还可以使用[MFC 类向导](../mfc/reference/mfc-class-wizard.md)中的 "**成员变量**" 选项卡来为指定的类添加新的成员变量，以及查看已定义的成员变量。

## <a name="delete-controls"></a>删除控件

在对话框中，选择控件，然后按**Delete**键，或单击 "浏览" "**编辑** > "**删除**"。

## <a name="other-issues"></a>其他问题

### <a name="troubleshooting"></a>故障排除

向对话框添加公共控件或超文本编辑控件后，在测试对话框时不会显示该控件。 或者，对话框本身不会出现。 例如：

1. 创建 Win32 项目，修改应用程序设置，以便创建 Windows 应用程序（而不是控制台应用）。

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中，双击 *.rc*文件。

1. 在对话框选项下，双击 "**关于**" 框。

1. 将**IP 地址控件**添加到对话框。

1. 保存并**全部重新生成**。

1. 执行程序。

1. 在对话框的 "**帮助**" 菜单上，选择 "**关于**" 命令并显示 "不显示" 对话框。

目前，当你将以下公共控件或丰富编辑控件拖放到对话框上时，**对话框编辑器**不会自动将代码添加到你的项目中。 出现此问题时，Visual Studio 也不会提供错误或警告。 若要解决此问题，请手动添加控件的代码。

||||
|-|-|-|
|滑块控件|树控件|日期时间选择器|
|陀螺旋控件|选项卡控件|Month Calendar|
|进度控件|动画控件|IP 地址控件|
|热键|Rich Edit 控件|扩展组合框|
|列表控件|Rich Edit 2.0 控件|自定义控件|

若要在对话框中使用公共控件，需要在创建对话框之前调用[nativemethods.initcommoncontrolsex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)或 `AFXInitCommonControls`。

若要使用 RichEdit 控件，必须调用 `LoadLibrary`。 有关详细信息，请参阅 "Windows SDK 中的[丰富编辑控件](/windows/win32/Controls/about-rich-edit-controls)和[丰富的编辑控件概述](../mfc/overview-of-the-rich-edit-control.md)。

> [!NOTE]
> 若要将 RichEdit 控件与 MFC 一起使用，必须先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)以加载 RichEdit 2.0 控件（riched20.dll。DLL），或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)以加载较早的 RichEdit 1.0 控件（RICHED32。DLL）。
>
> 你可以将当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件一起使用，但 `CRichEditCtrl` 仅设计为支持 RichEdit 2.0 控件。 由于 RichEdit 1.0 和 RichEdit 2.0 相似，因此大多数方法都适用。 但是，1.0 和2.0 控件之间有一些差异，因此某些方法可能不会正常运行或根本不工作。

### <a name="activex-controls"></a>ActiveX 控件

Visual Studio 使你可以将 ActiveX 控件插入对话框中。 有关详细信息，请参阅[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)和[ActiveX 控件容器](../mfc/activex-control-containers.md)。

使用 "**插入 Activex 控件**" 对话框，可以在使用[对话框编辑器](../windows/dialog-editor.md)时将 ActiveX 控件插入对话框中。 此对话框包含以下属性：

|属性|说明|
|---|---|
|**ActiveX 控件**|显示 ActiveX 控件的列表。<br/><br/>从此对话框插入控件不会生成包装类。 如果需要包装类，请使用[类视图](/visualstudio/ide/viewing-the-structure-of-code)来创建一个，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。<br/><br/>如果 ActiveX 控件未出现在此对话框中，请尝试根据供应商的说明安装控件。|
|**Path**|显示在其中找到 ActiveX 控件的文件。|

> [!CAUTION]
> 分发系统上的每个 ActiveX 控件可能并非都是合法的。 请参阅安装了控件的软件的许可协议，或与软件公司联系。

#### <a name="to-add-an-activex-control"></a>添加 ActiveX 控件

1. 在**对话框编辑器**中打开一个对话框。

1. 右键单击对话框正文中的任意位置，然后选择 "**插入 ActiveX 控件**"。

   此时将显示 "**插入 ActiveX 控件**" 对话框，其中显示了系统上的所有 ActiveX 控件。 在该对话框底部，会显示 ActiveX 控件文件的路径。

1. 选择要添加到对话框中的控件，然后选择 **"确定"** 。

   该控件会出现在对话框中，可以在其中编辑它或为它创建处理程序，就如同处理任何其他控件一样。

> [!TIP]
> 您可以使用**对话框编辑器**中的快捷菜单快速将已注册的 ActiveX 控件添加到对话框，或者尝试将 activex 控件添加到 "**工具箱**" 窗口以方便访问。

#### <a name="to-edit-properties-for-an-activex-control"></a>编辑 ActiveX 控件的属性

独立供应商提供的 ActiveX 控件可以具有其自己的属性和特性。 这些属性将显示在 "**属性**" 窗口中。 由 ActiveX 控件的编写器创建的所有属性页都显示在 "**属性页**" 对话框中。 （若要查看特定 ActiveX 控件的**属性页**，请选择 "[属性窗口](/visualstudio/ide/reference/properties-window)中的"**属性页**"按钮。

- 选择**ActiveX**控件，然后单击 " > 属性"**页**上的 "菜单" **"查看属性**"。 根据需要在属性页中进行更改。

   ActiveX 控件的属性页中显示了各种选项卡，具体取决于作为 ActiveX 控件一部分的属性表。

> [!NOTE]
> 此过程适用于使用属性页编辑 ActiveX 控件。 你还可以在新的 "**属性**" 窗口中浏览和编辑 ActiveX 属性。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[管理对话框控件](controls-in-dialog-boxes.md)<br/>
[如何：布局控件](arrangement-of-controls-on-dialog-boxes.md)<br/>
[如何：定义控件访问和值](defining-mnemonics-access-keys.md)

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