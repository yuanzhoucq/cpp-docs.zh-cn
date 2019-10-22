---
title: 对话框编辑器（C++）
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
ms.openlocfilehash: 40b5d8c8390c638b70bc2c0860ccf3c17872719c
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445027"
---
# <a name="dialog-editor-c"></a>对话框编辑器（C++）

可以通过**对话框编辑器**创建或编辑对话框资源。

- 若要打开该编辑器，请在 "**资源视图**" 窗口中双击该对话框的 .rc 文件，或在 "@no__t **@no__t"** 菜单中选择 "**资源视图**"。

创建新的对话框或对话框模板的第一步是添加控件。 在**对话框编辑器**中，可以排列控件以适应特定的大小、形状或对齐方式，也可以在对话框中移动控件以使其工作。 删除控件也很容易。

可将对话框存储为模板以便重复使用。 也可在设计对话框和编辑实现它的代码之间进行轻松切换。

还可以在**对话框编辑器**中编辑单个或多个控件的属性。 您可以更改 tab 键顺序，即按下**tab**键时控件获得焦点的顺序，也可以定义允许用户使用键盘来选择控件的访问键或键组合。

使用**对话框编辑器**，还可以使用自定义控件，包括 ActiveX 控件。 您还可以编辑[窗体视图](../mfc/reference/cformview-class.md)、[记录视图](../data/record-views-mfc-data-access.md)或[对话栏](../mfc/dialog-bars.md)。

从 Visual Studio 2015 开始，可以使用**对话框编辑器**定义动态布局，这指定了用户调整对话框大小时控件如何移动和调整大小。 有关详细信息，请参阅 [Dynamic Layout](../mfc/dynamic-layout.md)。

有关资源的详细信息，请参阅如何[创建对话框](../windows/creating-a-new-dialog-box.md)和[对话框控件](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 使用**对话框编辑器**时，在许多情况下，您可以选择使用鼠标右键来显示常用命令的快捷菜单。

## <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏

**对话框编辑器**工具栏包含用于排列对话框上的控件布局的按钮，例如大小和对齐方式。 **对话框编辑器**工具栏按钮对应于 "**格式**" 菜单上的命令。

|图标|含义|图标|含义|
|----------|-------------|----------|-------------|
|![测试对话框按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|“测试”对话框|![跨按钮间距](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|交叉|
|!["左对齐" 按钮](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|左对齐|![空间减小按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|
|![对齐权限按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|!["设置相同宽度" 按钮](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|使宽度相同|
|![顶部对齐按钮](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|顶部对齐|![设为相同高度按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|使高度相同|
|!["底端对齐" 按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底部对齐|!["设置相同大小" 按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|使大小相同|
|!["垂直居中" 按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切换网格按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|
|![居中水平按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切换辅助线按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换参考线|

- 若要显示或隐藏 "**对话框编辑器**" 工具栏，请  > **工具栏** >  "**对话框编辑器**中转到" 菜单**视图**"。

当你在C++项目中打开**对话框编辑器**时，**对话框编辑器**工具栏会自动显示在你的解决方案顶部，但是，如果你显式关闭工具栏，则下次打开**对话框编辑器时需要调用它**. 您可以通过在可用工具栏和窗口列表中选择它来切换其显示。

## <a name="switch-between-dialog-box-controls-and-code"></a>在对话框控件和代码之间切换

在 MFC 应用程序中，可以双击对话框控件跳转到其处理程序代码，或快速创建存根处理程序函数。

选中控件后，在 "[属性窗口](/visualstudio/ide/reference/properties-window)中选择"**事件**控制 "按钮或"**消息**"按钮，查看所选项目的可用 Windows 消息和事件的完整列表。 从列表中进行选择以创建或编辑处理程序函数。

- 若要跳转到 "**对话框编辑器**" 中的代码，请双击对话框中的控件，跳转到其最近实现的消息处理函数的声明。

   对于基于 ATL 的对话框类，您始终跳到构造函数定义。

- 若要查看控件的事件，并选中控件，请在 "**属性**" 窗口中选择 "**事件**" 按钮。

   当单个控件在对话框中具有焦点时，您可以右键单击并选择 "**添加事件处理程序**"。 这使你可以指定要向其添加处理程序的类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 当对话框具有焦点时，选择 "**事件**" 按钮将公开对话框中的所有控件的列表，然后您可以展开该对话框以编辑各个控件的事件。

- 若要查看对话框的消息，并选中对话框，请在 "**属性**" 窗口中选择 "**消息**" 按钮。

## <a name="accelerator-keys"></a>快捷键

下面是**对话框编辑器**命令的默认快捷键。  

|命令|键|描述|
|-------------|----------|-----------------|
|格式.底部对齐|**Ctrl** + **Shift** + **向下键**|将所选控件的下边缘与主导控件对齐。|
|格式.居中对齐|**Shift** + **F9**|将所选控件的垂直中心与主导控件对齐。|
|格式.左对齐|**Ctrl** + **Shift** + **左箭头**|将所选控件的左边缘与主导控件对齐。|
|格式.中间对齐|**F9**|将所选控件的水平中心与主导控件对齐。|
|格式.右对齐|**Ctrl** + **Shift** + **右箭头**|将所选控件的右边缘与主导控件对齐。|
|格式.顶部对齐|**Ctrl** + **Shift** + **向上键**|将所选控件的上边缘与主导控件对齐。|
|格式.按钮下|**Ctrl** + **B**|将所选按钮置于对话框的底部。|
|格式.按钮右|**Ctrl** + **R**|将所选按钮置于对话框的右上角。|
|格式.水平居中|**Ctrl** + **Shift** + **F9**|使控件在对话框中水平居中。|
|格式.垂直居中|Ctrl + F9|使控件在对话框内垂直居中。|
|格式.检查助记键|**Ctrl** + **M**|检查助记键的唯一性。|
|格式。 System.windows.window.sizetocontent|**轮班** + **F7**|调整所选控件的大小，使其适合标题文本。|
|格式.横向间隔|Alt  +  向左键|水平均匀地将选定控件隔开。|
|格式.纵向间隔|**Alt** + **向下箭头**|垂直地将选定控件均匀隔开。|
|格式.Tab 键顺序|**Ctrl** + **D**|设置对话框内的控件顺序。|
|格式.测试对话框|Ctrl  +  T|运行对话框以测试外观和行为。|
|格式.切换辅助线|Ctrl + G|在无网格、准则和网格间循环，以便进行对话框编辑。|

- 若要更改快捷键，请转到菜单**工具** > **选项**，然后选择 "**环境**" 文件夹下的 "**键盘**"。

   有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 若要更改设置，请转到菜单**工具** > **导入和导出设置**。

   对话框中的可用选项以及显示的菜单命令的名称和位置可能与 "**帮助**" 中的描述不同，具体取决于你的当前设置或版本。  有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

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