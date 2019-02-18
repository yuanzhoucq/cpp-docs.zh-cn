---
title: 如何：排列控件 （c + +） |Microsoft Docs
ms.date: 02/15/2019
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
ms.openlocfilehash: d9bd73c9cc81b113f222bbc090c62200c93554b2
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336626"
---
# <a name="how-to-arrange-controls-c"></a>如何：排列控件 （c + +）

**对话框**编辑器提供了布局工具一致，并自动调整控件的大小。 对于大多数任务，你可以使用[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**对话框编辑器**工具栏命令还位于**格式**菜单中和大多数具有[键盘快捷方式](../windows/accelerator-keys-for-the-dialog-editor.md)。

仅当选择多个控件提供了为对话框的许多布局命令。 你可以选择单个控件或多个控件，并选中多个控件后，你选择的第一个是默认情况下的"基准"控件。 选择控件和主导控件的信息，请参阅[选择控件](../windows/selecting-controls.md)。

位置、 高度和宽度的当前控件的右下角的状态栏显示。 选中整个对话框后，状态栏将显示作为一个整体，其高度和宽度的对话框中的位置。

## <a name="guides-and-grids"></a>参考线和网格

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

### <a name="to-create-edit-and-delete-guides-and-margins"></a>若要创建、 编辑和删除参考线和边距

是否正在移动控件，添加控件，或重新排列当前布局，指南可帮助您对齐控件在对话框中精确地。 参考线显示为蓝色点线横跨编辑器，然后在顶部和左侧和右侧的标尺中的相应箭头显示的对话框**对话框**编辑器。

当创建一个对话框时，将提供四个边距。 边距是修改后的参考线，以蓝色点线显示。 请参阅以下操作：

- 若要创建的指南，标尺，请在选择一次来创建参考线。 (单击一次创建一个新指南; 双击启动**参考线设置**可以在其中指定参考线设置对话框。)

- 若要设置指南中，对话框中，选择的指南，并将其拖到新位置。 （您还可以选择箭头拖动关联的参考线标尺中。）本指南的坐标被显示在窗口底部的状态栏和标尺中。 将指针移动标尺以显示该指南的准确位置中的箭头。

- 若要移动边距，拖动到新位置的边距。 若要使边距消失，移动到零位置的边距。 若要使重新边距，将鼠标指针放在边距的零位置并将边距移至相应位置。

- 若要删除一个指南，请将指南拖到对话框的外或拖离标尺相应的箭头。

### <a name="to-align-controls-on-a-guide"></a>若要在一条参考线上对齐控件

当移动控件，并参考线对齐控件是否存在任何控件之前对齐到指南时，控件的大小调整句柄对齐参考线。 一条参考线移动时，会对齐到它的控件也同时移动。 参考指南之一移动时调整大小将与多个指南对齐的控件。

由对话框单元 (Dlu) 定义中确定的指南和控件的间距标尺刻度。 DLU 基于对话框字体，通常的 8 磅 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体平均宽度。 垂直 DLU 是字体的平均除以 8 的高度。

#### <a name="to-size-a-group-of-controls-with-guides"></a>若要通过指南大小的一组控件

1. 与参考线对齐控件 （或控件） 的一侧。

1. 拖动控件 （或控件） 的另一端的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

1. 将移动任一调整大小的控件 （或控件） 的指南。

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要更改的时间刻度线的间隔

从**格式**菜单中，选择**参考线设置**，然后在**网格间距**字段中，指定新的宽度和高度 Dlu。

### <a name="to-disable-guides"></a>若要禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

- 若要禁用参考线对齐效果，同时持有向下拖动控件**Alt**密钥。

- 若要移动而无需移动对齐的控件的指南，此时，一直向下拖动参考线**Shift**密钥。

- 若要关闭这些指南，从**格式**菜单中，选择**参考线设置**。 然后在**参考线设置**对话框中的**版式参考线**，选择**None**。

   > [!NOTE]
   > 此外可以双击标尺栏以便访问**参考线设置**对话框。

> [!TIP]
> 若要关闭指南的快捷方式位于**格式**菜单中，选择**切换辅助线**。

### <a name="to-modify-the-layout-grid"></a>若要修改布局网格

当要放置或排列控件在对话框中的时，可用于更精确地定位布局网格。 打开网格时，将显示控件与"对齐"网格的虚线像磁化。 您可以打开和关闭此"对齐网格"功能和更改布局网格单元格的大小。

- 若要启用布局网格开还是关，从**格式**菜单中，选择**参考线设置**，然后选中或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框中**使用的编辑器窗口**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

- 若要从更改布局网格的大小**格式**菜单中，选择**参考线设置**，然后键入的高度和宽度 Dlu 网格中的单元格。 最小高度或宽度为 4 个 Dlu。

## <a name="select-controls"></a>选择控件

选择控件以调整大小、 对齐、 移动、 复制，或删除它们，，然后完成所需的操作。 在大多数情况下，您需要选择要使用的大小和对齐方式的工具上的多个控件[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

当控件被选定时，它有带实心 （活动） 在其周围的阴影的边框或空心 （非活动）"大小调整控点，"小方块，显示在选择边框。 当选择多个控件时，主导控件具有坚实的调整大小控点和所有其他所选的控件具有空心调整大小控点。

调整大小或对齐多个控件时**对话框**编辑器使用"主导控件"来确定如何调整大小或对齐其他控件。 默认情况下，主导控件为所选的第一个控件。

### <a name="to-select-controls"></a>若要选择控件

1. 在中[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择**指针**工具。

1. 使用以下步骤之一进行选择：

   - 拖动指针以绘制你想要在对话框中选择的控件周围的选择框。 当释放鼠标按钮时内, 和相交所选内容框中选择所有控件。

   - 按住**Shift**键并选择你想要在所选内容中包含的控件。

   - 按住**Ctrl**键并选择你想要在所选内容中包含的控件。

1. 若要添加或从所选控件的组中删除一个控件，请按住**Shift**键并选择你想要添加或删除的控件。

> [!NOTE]
> 按住**Ctrl**键并选择所选内容内的控件将使该控件中所选内容的主要控件。

### <a name="to-select-a-dominant-control"></a>若要选择主导控件

- 若要指定主导控件，请按住**Ctrl**键并选择你想要使用影响大小或位置的其他控件的控件*第一个*。

- 若要更改主导控件，通过选择所有当前所选控件外部清除当前所选内容并重复上一过程，首先选择一个不同的控件。

> [!NOTE]
> 主导控件的大小调整句柄是纯色，而下级控件的句柄是空心。 所有进一步调整大小或对齐方式取决于主导控件。

## <a name="size-controls"></a>控件的大小

使用大小调整句柄来调整控件的大小。 仅当鼠标指针置于调整大小控点时，它将改变形状以指示可以在其中调整控件的说明操作。 Solid active 调整大小控点，并且如果空心调整大小控点，不能沿该轴调整控件的大小。

> [!TIP]
> 此外可以通过将控件与参考线或边距，对齐更改控件的大小，或通过将移动一个对齐控件和参考线彼此。

### <a name="to-size-a-control"></a>若要调整控件的大小

1. 选择的控件。

1. 拖动调整大小控点，若要更改控件的大小：

   - 在顶部和边的大小句柄来更改水平或垂直大小。

   - 角的大小句柄更改水平和垂直大小。

   > [!TIP]
   > 可以通过按下一次调整控件一个对话框单元 （dlu） 地**Shift**密钥和使用**右**并**下**箭头键。

> [!TIP]
> 若要自动调整大小以适应其中的文本的控件，请打开**格式**菜单或右键单击该控件，然后选择**内容调整大小**。

### <a name="to-make-controls-the-same-size"></a>若要使大小相同的控件

您可以调整大小一的组基于主导控件大小的控件。

1. 选择要重设大小的控件。

   所选序列中的第一次控件是主导控件。 主导控件的大小取决于组中控件的最终大小。

1. 从**格式**菜单中，选择**使大小相同**，然后选择**同时**，**高度**，或**宽度**.

### <a name="combo-box"></a>组合框

时将其添加到对话框中，可以调整组合框的大小。 此外可以指定下拉列表框的大小。 有关详细信息，请参阅[添加到组合框控件的值](../windows/adding-values-to-a-combo-box-control.md)。

1. 选择组合框右侧的下拉箭头按钮。

   ![在 MFC 项目组合框上的箭头](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   此控件改为使用扩展的下拉列表区域显示组合框的大小的轮廓。

1. 使用较低的调整大小控点更改下拉列表区域的初始大小。

   ![组合&#45;MFC 项目中的框大小调整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 选择下拉箭头以关闭组合框的下拉列表部分。

### <a name="horizontal-scroll-bar"></a>水平滚动条

当将具有水平滚动条的列表框添加到使用 MFC 类在应用程序中不会自动显示滚动条的对话框。

通过调用设置提供给最大元素的最大宽度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)在代码中。 如果不设置此值，滚动条不会显示，甚至当列表框中的项都超过框。

## <a name="align-controls"></a>对齐控件

1. 选择你想要对齐的控件。 请务必选择你想要首先主导控件或将其设置为主导控件之前执行对齐方式或大小调整命令。

   最后一个控件组的位置取决于主导控件的位置。

1. 从**格式**菜单中，选择**对齐**，然后选择以下的对齐方式之一：

   |对齐方式|描述|
   |-----|-----------|
   |`Lefts`|将所选的控件沿它们的左边对齐。|
   |`Centers`|将所选的控件水平沿其中心点。|
   |`Rights`|将所选的控件沿其右侧。|
   |`Tops`|将所选的控件沿上边缘。|
   |`Middles`|将所选的控件它们的中心点沿垂直方向对齐。|
   |`Bottoms`|将所选的控件沿其下边缘对齐。|

### <a name="to-even-spacing-between-controls"></a>甚至控件之间的间距

**对话框**编辑器使您能够选择最外层控件之间均匀分配的空间控件。

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**均匀隔开**，然后选择以下间距对齐方式之一：

   |间距|描述|
   |---|---|
   |`Across`|最左侧和所选最右边的控件之间均匀分配的空间控件。|
   |`Down`|最上面和最下面选择的控件之间均匀分配的空间控件。|

### <a name="to-center-controls"></a>若要使控件

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**在对话框内居中**，然后选择以下的排列方式之一：

   |排列方式|描述|
   |---|---|
   |`Vertical`|在对话框中垂直居中对齐控件。|
   |`Horizontal`|在对话框中水平居中对齐控件。|

### <a name="to-arrange-push-buttons"></a>若要排列普通按钮

1. 选择一个或多个推送按钮。

1. 从**格式**菜单中，选择**排列按钮**，然后选择以下的排列方式之一：

   |排列方式|描述|
   |---|---|
   |`Right`|对齐普通按钮的对话框中的右边缘。|
   |`Bottom`|对齐对话框的底部边缘的普通按钮。|

   如果选择不是普通按钮控件，其位置不受影响。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)