---
title: 对话框编辑器 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: 827a7610aa919d5349313346ac0bfa80bd0647b0
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264889"
---
# <a name="dialog-editor-c"></a>对话框编辑器 （c + +）

**对话框**编辑器允许您创建或编辑对话框资源。 通过双击对话框的.rc 文件中打开对话框编辑器**资源视图**窗口 (**视图** > **资源视图**)。 请注意，**资源视图**在 Express 版本中不可用。

制作新对话框（或对话框模板）的前期步骤之一就是将控件添加到对话框。 在中**对话框**编辑器中，您可以排列控件以适应特定的大小、 形状或对齐方式，也可以移动它们大约在对话框中正常运行。 删除控件也很容易。

可将对话框存储为模板以便重复使用。 也可在设计对话框和编辑实现它的代码之间进行轻松切换。

还可在对话框编辑器中编辑单个或多个控件的属性。 您可以更改 tab 键顺序，即，的顺序控件获得焦点**选项卡**按下键，也可以定义允许用户选择使用键盘控制的访问键 （组合键）。 有关预设的访问键列表，请参阅 [对话框编辑器的快捷键](../windows/accelerator-keys-for-the-dialog-editor.md)。

**对话框**编辑器还允许你使用自定义控件，包括 ActiveX 控件。 此外，可以编辑 [窗体视图](../mfc/reference/cformview-class.md)、 [记录视图](../data/record-views-mfc-data-access.md)或 [对话栏](../mfc/dialog-bars.md)。

从 Visual Studio 2015 开始，你可以使用对话框编辑器定义动态布局，指定控件如何移动和调整用户调整对话框大小时。 有关详细信息，请参阅 [Dynamic Layout](../mfc/dynamic-layout.md)。

- [创建新对话框](../windows/creating-a-new-dialog-box.md)

- [创建用户在运行时无法退出的对话框](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [对话框中的控件](../windows/controls-in-dialog-boxes.md)

- [添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [测试对话框](../windows/testing-a-dialog-box.md)

- [对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > 使用时**对话框**编辑器中的，在许多情况下，您可以单击鼠标右键以显示常用命令的快捷菜单。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏

当打开**对话框中**在 c + + 项目中，编辑器**对话框编辑器**工具栏将自动显示在你的解决方案的顶部。

|图标|含义|图标|含义|
|----------|-------------|----------|-------------|
|![测试对话框按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|“测试”对话框|![横向间隔按钮](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|交叉|
|![对齐左对齐按钮](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|左对齐|![纵向间隔按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|
|![对齐权限按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|![使宽度相同按钮](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|使宽度相同|
|![您顶部的按钮对齐](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|顶部对齐|![使高度相同按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|使高度相同|
|![对齐底部按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底部对齐|![使大小相同按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|使大小相同|
|![垂直居中按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切换网格按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|
|![水平居中按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切换参考线按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换参考线|

**对话框编辑器**工具栏包含用于安排上的对话框中，例如大小和对齐方式的控件布局的按钮。 **对话框编辑器**上的工具栏按钮对应于命令**格式**菜单。

当你处于**对话框中**编辑器中，您可以切换显示**对话框编辑器**可用工具栏和窗口的列表中选择的工具栏。

- 若要显示或隐藏对话框编辑器工具栏上**视图**菜单中，选择**工具栏**，然后选择**对话框编辑器**子菜单中。

   > [!NOTE]
   > **对话框编辑器**在对话框编辑器中打开对话框资源时，默认情况下显示的工具栏; 但是，如果您显式关闭工具栏，您将需要调用它在下一次打开对话框资源。

## <a name="switch-between-dialog-box-controls-and-code"></a>对话框控件和代码之间切换

在 MFC 应用程序，你可以双击对话框控件跳转到其处理程序代码或快速创建存根 （stub） 的处理程序函数。

选择控件后，单击**控件事件**按钮或**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)若要查看 Windows 消息和事件的完整列表可用于所选的项。 选择要创建或编辑处理程序函数的列表。

- 若要从对话框编辑器跳转到代码，请双击对话框中要跳转到其最近实现消息处理函数的声明内的控件。 （对于基于 ATL 的对话框类，您总是跳转到构造函数定义。）

- 若要查看其事件的控件，控件后，选择**控件事件**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。

   > [!NOTE]
   > 选择**控件事件**按钮时*对话框的*在对话框中，你可以展开它以编辑单个控件的事件具有焦点公开所有控件的列表。

   单个控件有焦点在对话框中，您可以右键单击它并选择**添加事件处理程序**从快捷菜单。 这使您可以指定要向其添加处理程序的类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

- 若要查看消息的对话框中，使用选择，对话框中选择**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。

## <a name="accelerator-keys"></a>快捷键

下面是默认值对话框编辑器命令的快捷键。 若要更改键盘快捷方式，请选择**选项**上**工具**菜单中，然后选择**键盘**下**环境**文件夹。 有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

> [!NOTE]
> 对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

|命令|键|描述|
|-------------|----------|-----------------|
|格式.底部对齐|**Ctrl** + **Shift** + **向下箭头**|将主导控件将所选控件的底部边缘对齐|
|格式.居中对齐|**Shift** + **F9**|将选定控件与主导控件垂直中心对齐|
|格式.左对齐|**Ctrl** + **Shift** + **向左箭头**|将主导控件将所选控件的左侧的边缘对齐|
|格式.中间对齐|**F9**|将选定控件与主导控件水平中心对齐|
|格式.右对齐|**Ctrl** + **Shift** + **右箭头**|将主导控件将所选控件的右边缘对齐|
|格式.顶部对齐|**Ctrl** + **Shift** + **向上键**|将主导控件将所选控件上的边缘对齐|
|格式.按钮下|**Ctrl** + **B**|沿对话框的底部中心将所选的按钮置于|
|格式.按钮右|**Ctrl** + **R**|将所选的按钮放置在对话框中右上角|
|格式.水平居中|**Ctrl** + **Shift** + **F9**|使控件在对话框中的水平居中|
|格式.垂直居中|Ctrl + F9|使控件在对话框中的垂直居中|
|格式.检查助记键|**Ctrl** + **M**|检查助记键的唯一性|
|Format.SizeToContent|**Shift** + **F7**|调整所选的控件以适应标题文本的大小|
|格式.横向间隔|Alt  +  向左键|水平均匀分布选定的控件|
|格式.纵向间隔|**Alt** + **向下箭头**|垂直方向均匀的所选的控件|
|格式.Tab 键顺序|**Ctrl** + **D**|设置控件在对话框中的顺序|
|格式.测试对话框|Ctrl  +  T|在运行对话框中，若要测试的外观和行为|
|格式.切换辅助线|Ctrl + G|周期之间没有网格、 准则和网格编辑对话框|

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource.md)<br/>
[控件](../mfc/controls-mfc.md)<br/>
[控件类](../mfc/control-classes.md)<br/>
[对话框类](../mfc/dialog-box-classes.md)<br/>
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)