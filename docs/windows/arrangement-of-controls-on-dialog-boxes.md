---
title: 对话框 （c + +） 上的控件排列 |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 210fbf8e062b4dd8c469f9c40a015bbc19bc2843
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152737"
---
# <a name="arrangement-of-controls-on-dialog-boxes-c"></a>对话框 （c + +） 上的控件排列

**对话框**编辑器提供了布局工具一致，并自动调整控件的大小。 对于大多数任务，你可以使用[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**对话框编辑器**工具栏命令还位于**格式**菜单中和大多数具有[键盘快捷方式](../windows/accelerator-keys-for-the-dialog-editor.md)。

仅当选择多个控件提供了为对话框的许多布局命令。 你可以选择单个控件或多个控件，并选中多个控件后，你选择的第一个是默认情况下的"基准"控件。 选择控件和主导控件的信息，请参阅[选择控件](../windows/selecting-controls.md)。

位置、 高度和宽度的当前控件的右下角的状态栏显示。 选中整个对话框后，状态栏将显示作为一个整体，其高度和宽度的对话框中的位置。

## <a name="dialog-editor-states-guides-and-grids"></a>对话框编辑器状态 （参考线和网格）

你可以排列控件上使用对话框**对话框**编辑器在以下三种不同状态：

- 参考线和边距上 （默认设置）

- 与上的布局网格

- 不包含任何对齐或对齐方式功能

[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制的状态的按钮。 若要更改状态，请选择相应的图标。 此外可以通过更改状态**参考线设置**命令**格式**菜单。

**参考线设置**对话框具有以下属性：

|属性|描述|
|---|---|
|**版式参考线**|显示布局参考线设置。|
|**无**|隐藏布局工具。|
|**标尺和参考线**|启用时，将标尺添加到布局工具中;参考线可放在标尺。 默认指南将边距，可以通过拖动移动。 选择要放置参考线标尺。 控件指南时控件的上方或旁边它们移到"管理单元"。 后向其附加这些控件还移动用指南。 当控件所附加到每一侧的指南和参考线移动时，该控件调整大小。|
|**网格**|创建布局网格。 新控件将自动对齐到网格中。|
|**网格间距**|对话框框单元 (Dlu) 中显示的网格间距的设置。|
|**宽度：Dlu**|Dlu 中设置布局网格的宽度。 水平 DLU 是由 4 个划分对话框字体平均宽度。|
|**高：Dlu**|Dlu 中设置的布局网格的高度。 垂直 DLU 是平均划分的八个对话框字体的高度。|

### <a name="create-and-set-guides-and-margins"></a>创建并设置参考线和边距

是否正在移动控件，添加控件，或重新排列当前布局，指南可帮助您对齐控件在对话框中精确地。 参考线显示为蓝色点线横跨编辑器，然后在顶部和左侧和右侧的标尺中的相应箭头显示的对话框**对话框**编辑器。

当创建一个对话框时，将提供四个边距。 边距是修改后的参考线，以蓝色点线显示。

|进程|步骤|
|----------------|----------------|
|若要创建参考线|在标尺，请选择一次来创建参考线。 (单击一次创建一个新指南; 双击启动**参考线设置**可以在其中指定参考线设置对话框。)|
|若要设置参考线|在对话框中，单击该指南并将其拖动到新位置。 （您可以单击标尺拖动相关联的指南中的箭头）。<br/><br/>本指南的坐标被显示在窗口底部的状态栏和标尺中。 将指针移动标尺以显示该指南的准确位置中的箭头。|
|删除参考线|将指南拖出对话框的。<br/><br/>\- 或 -<br/><br/>将拖离标尺相应的箭头。|
|若要移动边距|拖动到新位置的边距。<br/><br/>若要使边距消失，移动到零位置的边距。 若要使重新边距，将鼠标指针放在边距的零位置并将边距移至相应位置。|

### <a name="align-controls-on-a-guide"></a>在参考线上对齐控件

当移动控件，并参考线对齐控件是否存在任何控件之前对齐到指南时，控件的大小调整句柄对齐参考线。 一条参考线移动时，会对齐到它的控件也同时移动。 参考指南之一移动时调整大小将与多个指南对齐的控件。

由对话框单元 (Dlu) 定义中确定的指南和控件的间距标尺刻度。 DLU 基于对话框字体，通常的 8 磅 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体平均宽度。 垂直 DLU 是字体的平均除以 8 的高度。

#### <a name="to-size-a-group-of-controls-with-guides"></a>若要通过指南大小的一组控件

1. 与参考线对齐控件 （或控件） 的一侧。

1. 拖动控件 （或控件） 的另一端的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

1. 将移动任一调整大小的控件 （或控件） 的指南。

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要更改的时间刻度线的间隔

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中**网格间距**字段中，指定新的宽度和高度 Dlu。

### <a name="disable-guides"></a>禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

#### <a name="to-disable-the-snapping-effect-of-the-guides"></a>若要禁用参考线的对齐效果

此时，一直向下拖动控件**Alt**密钥。

#### <a name="to-move-guides-without-moving-the-snapped-controls"></a>若要移动的参考线，而无需移动对齐的控件

此时，一直向下拖动参考线**Shift**密钥。

#### <a name="to-turn-off-the-guides"></a>若要关闭这些指南

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中的**版式参考线**，选择**None**。

   > [!NOTE]
   > 此外可以双击标尺栏以便访问**参考线设置**对话框。

\- 或 -

上**格式**菜单中，选择**切换辅助线**。

### <a name="modify-the-layout-grid"></a>修改布局网格

当要放置或排列控件在对话框中的时，可用于更精确地定位布局网格。 打开网格时，将显示控件与"对齐"网格的虚线像磁化。 您可以打开和关闭此"对齐网格"功能和更改布局网格单元格的大小。

#### <a name="to-turn-the-layout-grid-on-or-off"></a>若要打开或关闭的布局网格

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中，选中或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框中**使用的编辑器窗口**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

#### <a name="to-change-the-size-of-the-layout-grid"></a>若要更改布局网格的大小

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框框中，在网格中的单元格 Dlu 中键入的高度和宽度。 最小高度或宽度为 4 个 Dlu。

## <a name="group-radio-buttons-on-a-dialog-box"></a>出现在对话框中的组单选按钮

当向对话框添加单选按钮时，将它们视为一组通过设置**组**属性中的**属性**组中的第一个按钮的窗口。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。

一个对话框中可以有多组单选按钮，每个组都应使用以下过程添加。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>向对话框添加一组单选按钮

1. 选择单选按钮控件中的[工具箱窗口](/visualstudio/ide/reference/toolbox)并想要放置控件的对话框中选择的位置。

1. 重复执行第一步以根据需要添加多个单选按钮。 请确保组中的单选按钮是连续的 tab 键顺序。

1. 在 [属性窗口](/visualstudio/ide/reference/properties-window)中，请将按照 Tab 键顺序排列的第一个单选按钮的 **组** 属性  设置为 **True**。

   将 **组** 属性更改为 **True** 可将 WS_GROUP 样式添加到资源脚本的对话框对象的按钮条目中，并确保用户一次只能选择按钮组中的一个单选按钮（当用户单击一个单选按钮时，组中其他按钮都被清除）。

   > [!NOTE]
   > 只有组中第一个单选按钮的 **组** 属性应设置为 **True**。 如果你的不是按钮组的一部分的其他控件，设置**组**的第一个控件的属性 *，则将组外*到**True**以及。 您可以快速确定组外的第一个控件，通过按**Ctrl**+**D**若要查看的 tab 键顺序。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>添加单选按钮组的成员变量

1. 按 Tab 键顺序右键单击第一个单选按钮控件（主导控件和 **组** 属性设置为 True 的控件）。

1. 从快捷菜单中选择 **“添加变量”**  。

1. 在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择 **“控制变量”** 复选框，然后选择 **“值”** 单选按钮。

1. 在 **“变量名称”** 框中键入新成员变量的名称。

1. 在中**变量类型**列表框中，选择**int**或类型`int`。

1. 现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，`m_radioBox1 = 0;`选择第一个单选按钮组中。

## <a name="align-groups-of-controls"></a>对齐控件组

以下过程显示如何对齐控件：

### <a name="to-align-groups-of-controls"></a>若要对齐控件组

1. [选择的控件](../windows/selecting-multiple-controls.md)你想要保持一致。 请务必选择你想要首先将主导控件的控件或将其设置为主导控件之前执行对齐方式或大小调整命令。

   最后一个控件组的位置取决于主导控件的位置。 选择主导控件的详细信息，请参阅[指定主导控件](../windows/specifying-the-dominant-control.md)。

1. 从**格式**菜单中，选择**对齐**，然后选择以下的对齐方式之一：

   - `Lefts`： 将所选的控件沿它们的左边对齐。

   - `Centers`： 将所选的控件水平沿其中心点。

   - `Rights`： 将所选的控件沿其右侧。

   - `Tops`： 将所选的控件沿上边缘。

   - `Middles`： 将所选的控件它们的中心点沿垂直方向对齐。

   - `Bottoms`： 将所选的控件沿其下边缘对齐。

### <a name="to-even-the-spacing-between-controls"></a>若要在控件之间的间距相等

**对话框**编辑器使您能够选择最外层控件之间均匀分配的空间控件。

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**均匀隔开**，然后选择以下间距对齐方式之一：

   - `Across`： 空间之间均匀分配和选择最右边的控件的控件。

   - `Down`： 空间之间均匀分配最上面和最底部所选控件的控件。

### <a name="to-center-controls-in-a-dialog-box"></a>若要使控件在对话框内居中

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**在对话框内居中**，然后选择以下的排列方式之一：

   - `Vertical`： 使控件在对话框中垂直居中。

   - `Horizontal`： 使控件在对话框中水平居中。

### <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>若要排列普通按钮沿右侧或底部的对话框

1. 选择一个或多个推送按钮。

1. 从**格式**菜单中，选择**排列按钮**，然后选择以下的排列方式之一：

   - `Right`： 对齐普通按钮的对话框中的右边缘。

   - `Bottom`: 对话框中的下边缘沿对齐普通按钮。

       如果选择不是普通按钮控件，其位置不受影响。

## <a name="change-the-tab-order-of-controls"></a>更改控件的 tab 键顺序

Tab 键顺序为依据的顺序**选项卡**键将输入的焦点从一个控件移到下一个对话框中。 通常从左到右、 从上到下一个对话框中，将继续 tab 键顺序。 每个控件都**Tabstop**属性，用于确定控件是否接收输入的焦点。

### <a name="to-set-input-focus-for-a-control"></a>若要设置输入的焦点的控件

在中[属性窗口](/visualstudio/ide/reference/properties-window)，选择**True**或**False**中**Tabstop**属性。

即便是那些没有**Tabstop**属性设置为**True**需要是 tab 键顺序的一部分。 Tab 键顺序很重要，例如，当您[定义的访问键 （助记键）](../windows/defining-mnemonics-access-keys.md)没有标题的控件。 包含相关控件的访问键的静态文本注释后面必须紧跟相关的控件的 tab 键顺序。

> [!NOTE]
> 如果对话框包含重叠的控件，则更改 tab 键顺序可能会更改控件的显示的方式。 基于任何重叠的控件的 tab 键顺序将它们之前始终显示控件的更高版本中的 tab 键顺序。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要在对话框中查看当前的所有控件的 tab 键顺序

上**格式**菜单中，选择**tab 键顺序**。

\- 或 -

- 按**Ctrl** + **D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要更改的对话框中的所有控件的 tab 键顺序

1. 上**格式**菜单中，选择**tab 键顺序**。

   每个控件的左上角的数字的当前选项卡顺序显示其位置。

1. 通过单击所需的顺序在每个控件设置 tab 键顺序**选项卡**键遵循。

1. 按**Enter**退出**tab 键顺序**模式。

   > [!TIP]
   > 一旦您进入**tab 键顺序**模式下，可以按**Esc**或**Enter**可禁止更改 tab 键顺序。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要更改两个或多个控件的 tab 键顺序

1. 从**格式**菜单中，选择**tab 键顺序**。

1. 指定将开始按顺序更改的位置。 第一次按下**Ctrl**键并选择控件，然后选择的要更改其顺序开始。

   例如，如果你想要更改控件的顺序`7`通过`9`，按住**Ctrl**，然后选择的控件`6`第一个。

   > [!NOTE]
   > 若要将特定控件设置为数字`1`（首先在 tab 键顺序），双击该控件。

1. 发行**Ctrl**键，然后选择所需的顺序中的控件**选项卡**键遵循从该点。

1. 按**Enter**退出**tab 键顺序**模式。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)