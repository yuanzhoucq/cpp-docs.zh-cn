---
title: 对话框编辑器 （c + +）
ms.date: 02/15/2019
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
ms.openlocfilehash: dc5a823951e07af96efceec52d2aa23552c2d002
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029481"
---
# <a name="dialog-editor-c"></a>对话框编辑器 （c + +）

**对话框编辑器**允许您创建或编辑对话框资源。

- 若要打开编辑器中，双击对话框的.rc 文件中**资源视图**窗口中或转到菜单**视图** > **资源视图**。

一个使新建对话框或对话框模板中的第一个步骤将控件添加。 在中**对话框编辑器**、 可以排列控件以适应特定的大小、 形状或对齐方式，或可以移动它们大约在对话框中正常运行。 删除控件也很容易。

可将对话框存储为模板以便重复使用。 也可在设计对话框和编辑实现它的代码之间进行轻松切换。

还有可能要编辑的单个属性或多个控件中**对话框编辑器**。 您可以更改 tab 键顺序，即，的顺序控件获得焦点**选项卡**按下键，或者，可以定义的访问密钥或允许用户选择使用键盘的控件的键组合。

**对话框编辑器**还可以使用自定义控件，包括 ActiveX 控件。 此外可以编辑[窗体视图](../mfc/reference/cformview-class.md)，[记录视图](../data/record-views-mfc-data-access.md)，或[对话栏](../mfc/dialog-bars.md)。

从 Visual Studio 2015 开始，你可以使用**对话框编辑器**时在用户调整对话框定义动态布局，指定控件如何移动和调整其大小。 有关详细信息，请参阅 [Dynamic Layout](../mfc/dynamic-layout.md)。

有关资源的详细信息，请参阅如何[创建一个对话框](../windows/creating-a-new-dialog-box.md)并[对话框控件](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 使用时**对话框编辑器**，在许多情况下，您可以选择用鼠标右键以显示常用命令的快捷菜单。

## <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏

**对话框编辑器**工具栏包含用于安排上的对话框中，例如大小和对齐方式的控件布局的按钮。 **对话框编辑器**上的工具栏按钮对应于命令**格式**菜单。

|图标|含义|图标|含义|
|----------|-------------|----------|-------------|
|![测试对话框按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|“测试”对话框|![横向间隔按钮](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|交叉|
|![对齐左对齐按钮](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|左对齐|![纵向间隔按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|
|![对齐权限按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|![使宽度相同按钮](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|使宽度相同|
|![您顶部的按钮对齐](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|顶部对齐|![使高度相同按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|使高度相同|
|![对齐底部按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底部对齐|![使大小相同按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|使大小相同|
|![垂直居中按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切换网格按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|
|![水平居中按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切换参考线按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换参考线|

- 若要显示或隐藏**对话框编辑器**工具栏上，转到菜单**视图** > **工具栏** > **对话框编辑器**。

当打开**对话框编辑器**在 c + + 项目中，**对话框编辑器**工具栏会自动显示在顶部的您的解决方案，但是，如果您显式关闭工具栏，你将需要调用它下次打开**对话框编辑器**。 通过从可用的工具栏和窗口的列表中选择它，可以切换其显示。

## <a name="switch-between-dialog-box-controls-and-code"></a>对话框控件和代码之间切换

在 MFC 应用程序，你可以双击对话框控件跳转到其处理程序代码或快速创建存根 （stub） 的处理程序函数。

使用选定控件后，选择**控件事件**按钮或**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)若要查看 Windows 消息和事件的完整列表可用于所选的项。 选择要创建或编辑处理程序函数的列表。

- 若要跳转到代码从**对话框编辑器**，双击对话框中要跳转到其最近实现消息处理函数的声明内的控件。

   对于基于 ATL 的对话框类，您总是跳转到构造函数定义。

- 若要查看其事件的控件，控件后，选择**控件事件**按钮**属性**窗口。

   单个控件有焦点在对话框中，您可以右键单击并选择**添加事件处理程序**。 这使您可以指定要向其添加处理程序的类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 选择**控件事件**按钮的对话框中有焦点时显示在对话框中，你可以展开它以编辑单个控件的事件的所有控件的列表。

- 若要查看消息的对话框中，使用选择，对话框中选择**消息**按钮**属性**窗口。

## <a name="accelerator-keys"></a>快捷键

以下是默认值为快捷键**对话框编辑器**命令。  

|命令|键|描述|
|-------------|----------|-----------------|
|格式.底部对齐|**Ctrl** + **Shift** + **向下箭头**|将主导控件将所选控件的底部边缘对齐。|
|格式.居中对齐|**Shift** + **F9**|对齐主导控件将所选控件的垂直中心。|
|格式.左对齐|**Ctrl** + **Shift** + **向左箭头**|将主导控件将所选控件的左边的缘对齐。|
|格式.中间对齐|**F9**|将选定控件与主导控件水平中心对齐。|
|格式.右对齐|**Ctrl** + **Shift** + **右箭头**|将主导控件将所选控件的右边缘对齐。|
|格式.顶部对齐|**Ctrl** + **Shift** + **向上键**|将主导控件将所选控件上的边缘对齐。|
|格式.按钮下|**Ctrl** + **B**|沿对话框的底部中心的所选按钮的位置。|
|格式.按钮右|**Ctrl** + **R**|将所选的按钮放在对话框中右上角中。|
|格式.水平居中|**Ctrl** + **Shift** + **F9**|使控件在对话框中的水平居中。|
|格式.垂直居中|Ctrl + F9|使控件在对话框中的垂直居中。|
|格式.检查助记键|**Ctrl** + **M**|检查助记键的唯一性。|
|Format.SizeToContent|**Shift** + **F7**|调整大小以适应标题文本的选定的控件。|
|格式.横向间隔|Alt  +  向左键|所选的控件在水平方向均匀分布。|
|格式.纵向间隔|**Alt** + **向下箭头**|所选的控件在垂直方向均匀分布。|
|格式.Tab 键顺序|**Ctrl** + **D**|设置控件在对话框中的顺序。|
|格式.测试对话框|Ctrl  +  T|在运行对话框中，若要测试的外观和行为。|
|格式.切换辅助线|Ctrl + G|用于对话框编辑之间没有网格、 准则和网格循环移动。|

- 若要更改键盘快捷方式，请转到菜单**工具** > **选项**，然后选择**键盘**下**环境**文件夹。

   有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 若要更改设置，请转到菜单**工具** > **导入和导出设置**。

   在对话框的名称和位置的菜单命令，您看到的可用的选项可能不同于中的描述**帮助**具体取决于您现用的设置或版本。  有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[如何：创建对话框](../windows/creating-a-new-dialog-box.md)<br/>
[对话框控件](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->