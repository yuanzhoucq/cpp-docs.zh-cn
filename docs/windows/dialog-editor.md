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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370293"
---
# <a name="dialog-editor-c"></a>对话框编辑器（C++）

**对话框编辑器**允许您创建或编辑对话框资源。

- 要打开编辑器，请在 **"资源视图"** 窗口中双击对话框的 .rc 文件，或转到菜单 **"查看** > **其他 Windows** > **资源视图**"。

创建新对话框或对话框模板的第一个步骤是添加控件。 在**对话框编辑器**中，可以排列控件以适合特定大小、形状或对齐方式，也可以将它们移动到对话框中工作。 删除控件也很容易。

可将对话框存储为模板以便重复使用。 也可在设计对话框和编辑实现它的代码之间进行轻松切换。

也可以编辑**对话框编辑器**中单个或多个控件的属性。 您可以更改选项卡顺序，即按下**Tab**键时控件获得焦点的顺序，也可以定义允许用户使用键盘选择控件的访问键或键组合。

**对话框编辑器**还允许您使用自定义控件，包括 ActiveX 控件。 您还可以编辑[窗体视图](../mfc/reference/cformview-class.md)、[记录视图](../data/record-views-mfc-data-access.md)或[对话框栏](../mfc/dialog-bars.md)。

从 Visual Studio 2015 开始，可以使用**对话框编辑器**定义动态布局，其中指定控件在用户调整对话框大小时如何移动和调整大小。 有关详细信息，请参阅 [Dynamic Layout](../mfc/dynamic-layout.md)。

有关资源的详细信息，请参阅如何[创建对话框](../windows/creating-a-new-dialog-box.md)和[对话框控件](../windows/controls-in-dialog-boxes.md)。

> [!TIP]
> 在在许多情况下，使用**对话框编辑器**时，可以使用鼠标右键选择显示常用命令的快捷菜单。

## <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏

**"对话框编辑器**"工具栏包含用于排列对话框上控件布局的按钮，例如大小和对齐方式。 **对话框编辑器**工具栏按钮对应于 **"格式"** 菜单上的命令。

|图标|含义|图标|含义|
|----------|-------------|----------|-------------|
|![“测试对话框”按钮](../mfc/media/vcdialogeditortestdialog.png "vc对话编辑器测试对话")|“测试”对话框|![“横向间隔”按钮](../mfc/media/vcdialogeditoracross.png "vc对话编辑器")|交叉|
|![“左对齐”按钮](../mfc/media/vcdialogeditoralignlefts.png "vc对话编辑器对齐左")|左对齐|![“纵向间隔”按钮](../mfc/media/vcdialogeditordown.png "vc对话编辑器向下")|向下|
|![“右对齐”按钮](../mfc/media/vcdialogeditoralignrights.png "vc对话编辑器对齐权利")|右对齐|![“使宽度相同”按钮](../mfc/media/vcdialogeditorsamewidth.png "vc对话编辑器相同宽度")|使宽度相同|
|![“顶端对齐”按钮](../mfc/media/vcdialogeditoraligntops.png "vc对话编辑器对齐顶部")|顶部对齐|![“使高度相同”按钮](../mfc/media/vcdialogeditormakesameheight.png "vc对话编辑器使同一高度")|使高度相同|
|![“底端对齐”按钮](../mfc/media/vcdialogeditoralignbottoms.png "vc对话编辑器对齐")|底部对齐|![“使大小相同”按钮](../mfc/media/vcdialogeditorsamesize.png "vc对话编辑器相同尺寸")|使大小相同|
|![“垂直居中”按钮](../mfc/media/vcdialogeditorvertical.png "vc对话编辑器垂直")|垂直|![“切换网格”按钮](../mfc/media/vcdialogeditortogglegrid.png "vc对话编辑器切换网格")|切换网格|
|![“水平居中”按钮](../mfc/media/vcdialogeditorhorizontal.png "vc对话编辑器水平")|横向|![“切换辅助线”按钮](../mfc/media/vcdialogeditortoggleguides.png "vc对话编辑器切换指南")|切换参考线|

- 要显示或隐藏**对话框编辑器**工具栏，请访问菜单 **"查看** > **工具栏** > **对话框编辑器**"。

在C++项目中打开**对话框编辑器**时，**对话框编辑器**工具栏会自动显示在解决方案的顶部，但是，如果显式关闭工具栏，则需要在下次打开**对话框编辑器**时调用它。 您可以通过从可用工具栏和窗口列表中选择它来切换其显示。

## <a name="switch-between-dialog-box-controls-and-code"></a>在对话框控件和代码之间切换

在 MFC 应用程序中，可以双击对话框控件以跳转到其处理程序代码或快速创建存根处理程序函数。

选择控件后，选择"[属性"窗口中](/visualstudio/ide/reference/properties-window)的 **"控制事件**"按钮或 **"消息"** 按钮，以查看可用于所选项目的 Windows 消息和事件的完整列表。 从列表中选择以创建或编辑处理程序函数。

- 要从**对话框编辑器**跳转到代码，请双击对话框中的控件，以跳转到声明，使其最近实现的消息处理函数。

   对于基于 ATL 的对话框类，您始终跳转到构造函数定义。

- 要查看控件的事件，选择控件后，请选择"**属性**"窗口中的 **"控制事件**"按钮。

   当单个控件在对话框中具有焦点时，您可以右键单击并选择 **"添加事件处理程序**"。 这使您能够指定向其添加处理程序的类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

   > [!NOTE]
   > 选择 **"控制事件"** 按钮，当对话框具有焦点时，将公开对话框中所有控件的列表，然后可以展开该列表以编辑各个控件的事件。

- 要查看对话框的消息，选择该对话框，请选择"**属性**"窗口中**的"消息"** 按钮。

## <a name="accelerator-keys"></a>快捷键

下面是**对话框编辑器**命令的默认快捷键。  

|Command|键|说明|
|-------------|----------|-----------------|
|格式.底部对齐|**Ctrl** + **向下移** + **位箭头**|将所选控件的底部边缘与主导控件对齐。|
|格式.居中对齐|**换档** + **F9**|将所选控件的垂直中心与主导控件对齐。|
|格式.左对齐|**Ctrl** + **向左** + **箭头**移动|将所选控件的左边缘与主导控件对齐。|
|格式.中间对齐|**F9**|将所选控件的水平中心与主导控件对齐。|
|格式.右对齐|**Ctrl** + 向右**箭头****移位** + |将所选控件的右边缘与主导控件对齐。|
|格式.顶部对齐|**Ctrl** + **向上移位** + **箭头**|将所选控件的上边缘与主导控件对齐。|
|格式.按钮下|**Ctrl** + **B**|沿对话框的底部中心放置所选按钮。|
|格式.按钮右|**Ctrl** + **R**|将所选按钮放在对话框的右上角。|
|格式.水平居中|**Ctrl** + **换档** + **F9**|在对话框中水平居中控件。|
|格式.垂直居中|**Ctrl** + **F9**|控件垂直居中对话框中。|
|格式.检查助记键|**Ctrl** + **M**|检查助记符的独特性。|
|格式.大小到内容|**换档** + **F7**|调整所选控件的大小以适合标题文本。|
|格式.横向间隔|**Alt** + **左箭头**|水平均匀地放置所选控件。|
|格式.纵向间隔|**Alt** + **向下箭头**|垂直均匀地空间所选控件。|
|格式.Tab 键顺序|**Ctrl** + **D**|设置对话框中控件的顺序。|
|格式.测试对话框|**Ctrl** + **T**|运行对话框以测试外观和行为。|
|格式.切换辅助线|**Ctrl** + **G**|在无网格、准则和网格之间循环以进行对话框编辑。|

- 要更改快捷键，请转到菜单 **"工具** > **选项**"，然后选择 **"环境"** 文件夹下的 **"键盘**"。

   有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

- 要更改设置，请转到菜单 **"工具** > **导入和导出设置**"。

   对话框中可用的选项以及您看到的菜单命令的名称和位置可能与 **"帮助"** 中描述的选项不同，具体取决于您的活动设置或版本。  有关详细信息，请参阅[个性化可视化工作室 IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[如何：创建一个对话框](../windows/creating-a-new-dialog-box.md)<br/>
[对话框控件](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
