---
title: 对话框 （c + +） 上的控件排列 |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
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
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 99667898428fe9532d59277bfedafd24927304dc
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264876"
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

若要通过指南缓存大小的一组控件：

1. 与参考线对齐控件 （或控件） 的一侧。

1. 拖动控件 （或控件） 的另一端的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

1. 将移动任一调整大小的控件 （或控件） 的指南。

若要更改刻度线的间隔：

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中**网格间距**字段中，指定新的宽度和高度 Dlu。

### <a name="disable-guides"></a>禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

- 若要禁用参考线对齐效果，同时持有向下拖动控件**Alt**密钥。

- 若要移动而无需移动对齐的控件的指南，此时，一直向下拖动参考线**Shift**密钥。

- 若要关闭这些指南，从**格式**菜单中，选择**参考线设置**。 然后在**参考线设置**对话框中的**版式参考线**，选择**None**。

   > [!NOTE]
   > 此外可以双击标尺栏以便访问**参考线设置**对话框。

> [!TIP]
> 若要关闭指南的快捷方式位于**格式**菜单中，选择**切换辅助线**。

### <a name="modify-the-layout-grid"></a>修改布局网格

当要放置或排列控件在对话框中的时，可用于更精确地定位布局网格。 打开网格时，将显示控件与"对齐"网格的虚线像磁化。 您可以打开和关闭此"对齐网格"功能和更改布局网格单元格的大小。

若要打开或关闭的布局网格：

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中，选中或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框中**使用的编辑器窗口**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

若要更改布局网格的大小：

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框框中，在网格中的单元格 Dlu 中键入的高度和宽度。 最小高度或宽度为 4 个 Dlu。

## <a name="selecting-controls"></a>“选择”控件

选择控件以调整大小、 对齐、 移动、 复制，或删除它们，，然后完成所需的操作。 在大多数情况下，您需要选择要使用的大小和对齐方式的工具上的多个控件[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

当控件被选定时，它有带实心 （活动） 在其周围的阴影的边框或空心 （非活动）"大小调整控点，"小方块，显示在选择边框。 当选择多个控件时，主导控件具有坚实的调整大小控点和所有其他所选的控件具有空心调整大小控点。

调整大小或对齐多个控件时**对话框**编辑器使用"主导控件"来确定如何调整大小或对齐其他控件。 默认情况下，主导控件为所选的第一个控件。

### <a name="to-select-multiple-controls"></a>若要选择多个控件

1. 在中[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择**指针**工具。

1. 使用以下步骤之一进行选择：

   - 拖动指针以绘制你想要在对话框中选择的控件周围的选择框。 当释放鼠标按钮时内, 和相交所选内容框中选择所有控件。

   - 按住**Shift**键并选择你想要在所选内容中包含的控件。

   - 按住**Ctrl**键并选择你想要在所选内容中包含的控件。

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要从所选控件的组中删除控件或控件添加到所选控件的组

与所选控件的组，按住**Shift**键并选择你想要添加到现有的选定内容或从其中移除的控件。

   > [!NOTE]
   > 按住**Ctrl**键并选择所选内容内的控件将使该控件中所选内容的主要控件。

### <a name="to-specify-the-dominant-control"></a>若要指定主导控件

按住**Ctrl**键并选择你想要使用影响大小或位置的其他控件的控件*第一个*。

> [!NOTE]
> 主导控件的大小调整句柄是纯色，而下级控件的句柄是空心。 所有进一步调整大小或对齐方式取决于主导控件。

### <a name="to-change-the-dominant-control"></a>若要更改主导控件

1. 清除所有当前所选控件的外部单击当前所选内容。

1. 重复上一过程，首先选择一个不同的控件。

## <a name="sizing-controls"></a>调整控件的大小

使用大小调整句柄来调整控件的大小。 仅当鼠标指针置于调整大小控点时，它将改变形状以指示可以在其中调整控件的说明操作。 活动的调整大小控点都是可靠;如果大小调整句柄是空心，控件不能沿该轴的大小调整。

此外可以通过将控件与参考线或边距，对齐更改控件的大小，或通过将移动一个对齐控件和参考线彼此。

### <a name="to-size-an-individual-control"></a>调整单个控件的大小

1. 选择的控件。

1. 拖动调整大小控点，若要更改控件的大小：

   - 在顶部和边的调整大小控点更改水平或垂直大小。

   - 角的调整大小控点更改水平和垂直大小。

   > [!TIP]
   > 可以通过按下一次调整控件一个对话框单元 （dlu） 地**Shift**密钥和使用**向右箭头**并**向下箭头**密钥。

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自动调整大小以适应其中的文本的控件

选择**内容调整大小**从**格式**菜单或右键单击该控件，然后选择**内容调整大小**从快捷菜单。

### <a name="to-make-controls-the-same-width-height-or-size"></a>若要使控件相同的宽度、 高度或大小

您可以调整大小一的组基于主导控件大小的控件。

1. 选择要重设大小的控件。

   所选序列中的第一次控件是主导控件。 主导控件的大小取决于组中控件的最终大小。

1. 从**格式**菜单中，选择**使大小相同**，然后选择**同时**，**高度**，或**宽度**。

### <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>若要设置的组合大小框和下拉列表

时将其添加到对话框中，可以调整组合框的大小。 此外可以指定下拉列表框的大小。 有关详细信息，请参阅[添加到组合框控件的值](../windows/adding-values-to-a-combo-box-control.md)。

#### <a name="to-size-a-combo-box"></a>若要组合框的大小

1. 在对话框中选择的组合框控件。

   最初，仅左侧和右侧的调整大小控点处于活动状态。

1. 使用大小调整句柄设置组合框的宽度。

此外可以设置组合框的下拉部分的垂直大小。

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>若要设置的组合大小框下拉列表

1. 选择组合框右侧的下拉箭头按钮。

   ![在 MFC 项目组合框上的箭头](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   此控件改为使用扩展的下拉列表区域显示组合框的大小的轮廓。

1. 使用较低的调整大小控点更改下拉列表区域的初始大小。

   ![组合&#45;MFC 项目中的框大小调整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 选择下拉箭头以关闭组合框的下拉列表部分。

### <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>若要将水平滚动条的宽度设置，使其看起来

当将具有水平滚动条的列表框添加到使用 MFC 类在应用程序中不会自动显示滚动条的对话框。

通过调用设置提供给最大元素的最大宽度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)在代码中。

   如果不设置此值，滚动条不会显示，甚至当列表框中的项都超过框。

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

## <a name="to-align-groups-of-controls"></a>若要对齐控件组

1. 选择你想要对齐的控件。 请务必选择你想要首先将主导控件的控件或将其设置为主导控件之前执行对齐方式或大小调整命令。

   最后一个控件组的位置取决于主导控件的位置。 选择主导控件的详细信息，请参阅[指定主导控件](../windows/specifying-the-dominant-control.md)。

1. 从**格式**菜单中，选择**对齐**，然后选择以下的对齐方式之一：

   |值|描述|
   |-----|-----------|
   |`Lefts`|将所选的控件沿它们的左边对齐。|
   |`Centers`|将所选的控件水平沿其中心点。|
   |`Rights`|将所选的控件沿其右侧。|
   |`Tops`|将所选的控件沿上边缘。|
   |`Middles`|将所选的控件它们的中心点沿垂直方向对齐。|
   |`Bottoms`|将所选的控件沿其下边缘对齐。|

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

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)