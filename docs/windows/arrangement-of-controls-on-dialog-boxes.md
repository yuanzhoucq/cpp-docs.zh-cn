---
title: 如何：布局控件 (C++) |Microsoft Docs
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
ms.openlocfilehash: 878b7371dfa77880d68f1001444ed44b84d7240c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037416"
---
# <a name="how-to-layout-controls-c"></a>如何：布局控件 (C++)

**对话框编辑器**提供布局工具一致，并自动调整控件的大小。 对于大多数任务，你可以使用[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 所有**对话框编辑器**工具栏命令还位于**格式**菜单中和大多数具有[键盘快捷方式](../windows/accelerator-keys-for-the-dialog-editor.md)。

仅当选择多个控件提供了为对话框的许多布局命令。 你可以选择单个控件或多个控件，并选中多个控件后，第一个选择是默认情况下主导控件。

位置、 高度和宽度的当前控件的右下角的状态栏显示。 选中整个对话框后，状态栏将显示作为一个整体，其高度和宽度的对话框中的位置。

## <a name="arrange-controls"></a>排列控件

你可以排列控件上使用对话框**对话框编辑器**中三种不同状态之一：

- 使用参考线和边距上的，设置为默认值。

- 与上的布局网格。

- 无需任何管理单元或对齐方式的功能。

[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制的状态的按钮。

- 若要更改状态，选择相应的图标，或转到菜单**格式** > **参考线设置**。

**参考线设置**对话框具有以下属性：

|属性|描述|
|---|---|
|**版式参考线**|显示布局参考线设置。|
|**无**|隐藏布局工具。|
|**标尺和参考线**|启用时，将标尺添加到布局工具，并允许放在标尺中的指南。 默认指南将边距。|
|**网格**|创建布局网格。 新控件将自动对齐到网格中。|
|**网格间距**|对话框框单元 (Dlu) 中显示的网格间距的设置。|
|**宽度：Dlu**|Dlu 中设置布局网格的宽度。 水平 DLU 是除以 4 的对话框字体平均宽度。|
|**高：Dlu**|Dlu 中设置的布局网格的高度。 垂直 DLU 是平均除以 8 对话框字体的高度。|

### <a name="guides-and-margins"></a>参考线和边距

是否正在移动控件，添加控件，或重新排列当前布局参考线和边距可以帮助您对齐控件在对话框中精确地。

时创建对话框中，调用边距的四个已修改的指南提供了，并以蓝色点线显示。

- 若要移动边距，拖动到新位置的边距。

- 若要使边距消失，移动到零位置的边距。

- 若要使重新边距，将鼠标指针放在边距的零位置并将边距移至相应位置。

参考线显示为蓝色点线横跨编辑器，然后在顶部和左侧和右侧的标尺中的相应箭头显示的对话框**对话框编辑器**。 当移动控件，并参考线对齐控件是否存在任何控件之前对齐到指南时，控件的大小调整句柄对齐参考线。 一条参考线移动时，会对齐到它的控件也同时移动。 参考指南之一移动时调整大小将与多个指南对齐的控件。

- 若要创建标尺中的指南，请选择一次来创建参考线，或双击以启动**参考线设置**可以在其中指定参考线设置对话框。

- 要设置对话框的指南，请选择指南并将其拖动到新位置，或选择将关联的参考线标尺中的箭头。

   本指南的坐标会显示在窗口的底部的状态栏中，标尺中或将指针移到标尺以显示该指南的准确位置中的箭头。

- 若要删除一个指南，请将指南拖到对话框的外或拖离标尺相应的箭头。

由对话框单元 (Dlu) 定义中确定的指南和控件的间距标尺刻度。 DLU 基于对话框字体，通常的 8 磅 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体平均宽度。 垂直 DLU 是字体的平均除以 8 的高度。

- 若要更改刻度线的间隔，请转到菜单**格式** > **参考线设置**，然后在**网格间距**字段中，指定新的宽度和高度 Dlu。

### <a name="layout-grid"></a>布局网格

当您放置或排列控件在对话框中的，使用更精确地定位的布局网格。 启用网格后，控件将对齐到网格的虚线，像磁化。

- 若要打开或关闭的布局网格，请转到菜单**格式** > **参考线设置**并选择或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框编辑器**使用 windows**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

- 若要更改布局网格的大小，请转到菜单**格式** > **参考线设置**Dlu 中键入的高度和宽度，在网格中的单元格。 最小高度或宽度为 4。

### <a name="disable-guides"></a>禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

- 若要禁用参考线对齐效果，同时持有向下拖动控件**Alt**密钥。

- 若要移动而无需移动对齐的控件的指南，此时，一直向下拖动参考线**Shift**密钥。

- 若要关闭这些指南，请转到菜单**格式** > **参考线设置**。 然后，在**版式参考线**，选择**None**。

   > [!TIP]
   > 此外可以在菜单中使用该快捷方式**格式** > **切换辅助线**。

## <a name="select-controls"></a>选择控件

选择控件以调整大小、 对齐、 移动、 复制，或删除它们，，然后完成所需的操作。 在大多数情况下，您需要选择要使用的大小和对齐方式的工具上的多个控件[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

选中控件后，它将具有阴影的边框与实线 （活动） 或大小调整控点显示在选择边框的小方块的空心 （非活动）。 当选择多个控件时，主导控件具有坚实的调整大小控点和所有其他所选的控件具有空心调整大小控点。

- 若要在中选择控件，[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择**指针**工具，然后使用以下步骤之一来进行选择：

  - 拖动指针以绘制你想要在对话框中选择的控件周围的选择框。 当释放鼠标按钮时内, 和相交所选内容框中选择所有控件。

  - 按住**Shift**键并选择你想要在所选内容中包含的控件。

  - 按住**Ctrl**键并选择你想要在所选内容中包含的控件。

- 若要添加或从所选控件的组中删除一个控件，请按住**Shift**键并选择你想要添加或删除的控件。

### <a name="dominant-controls"></a>主导控件

调整大小或对齐多个控件时**对话框编辑器**主导控件用于确定如何调整大小或对齐其他控件。 默认情况下，主导控件为所选的第一个控件。

- 若要指定主导控件，请按住**Ctrl**键并选择你想要使用影响大小或位置的其他控件的控件*第一个*。 按住**Ctrl**键并选择所选内容内的控件，还可以控制所选内容的主导控件。

- 若要更改主导控件，通过选择所有当前所选控件外部清除当前所选内容并重复上述过程中，选择一个不同的控件*第一个*。

> [!NOTE]
> 主导控件的大小调整句柄是纯色，而下级控件的句柄是空心。 所有进一步调整大小或对齐方式取决于主导控件。

## <a name="size-controls"></a>控件的大小

使用大小调整句柄来调整控件的大小。 仅当鼠标指针置于调整大小控点时，它将改变形状以指示可以在其中调整控件的说明操作。 Solid active 调整大小控点，并且如果空心调整大小控点，不能沿该轴调整控件的大小。

- 若要调整控件的大小，选择控件并拖动调整大小控点，若要更改的大小。

  - 在顶部和边的大小句柄来更改水平或垂直大小。

  - 角的大小句柄更改水平和垂直大小。

   > [!TIP]
   > 可以通过按下一次调整控件一个对话框单元 （dlu） 地**Shift**密钥和使用**右**并**下**箭头键。

- 若要自动调整大小以适应其中的文本的控件，请转到菜单**格式**或者右键单击该控件，然后选择**内容调整大小**。

- 若要使控件大小相同，请选择你想要重设大小，并转到菜单的控件**格式** > **使大小相同**，然后选择**同时**， **高度**，或**宽度**。

   调整大小一的组基于主导控件，这是所选序列中的第一次控件大小的控件。 主导控件的大小取决于组中控件的最终大小。

- 若要使用参考线的大小的一组控件，与参考线对齐控件 （或控件） 的一侧，然后拖动控件 （或控件） 的另一端的指南。 现在可以继续任一调整大小的控件 （或控件） 的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

### <a name="other-controls"></a>其他控件

时将其添加到对话框中，可以调整组合框的大小。 此外可以指定下拉列表框的大小。 有关详细信息，请参阅[添加到组合框控件的值](../windows/adding-values-to-a-combo-box-control.md)。

1. 选择组合框右侧的下拉箭头按钮。

   ![在 MFC 项目组合框上的箭头](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   此控件改为使用扩展的下拉列表区域显示组合框的大小的轮廓。

1. 使用较低的调整大小控点更改下拉列表区域的初始大小。

   ![组合&#45;MFC 项目中的框大小调整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 选择下拉箭头以关闭组合框的下拉列表部分。

> [!NOTE]
> 当将具有水平滚动条的列表框添加到使用 MFC 对话框中时，滚动条不会自动显示在你的应用程序。
>
> 通过调用设置提供给最大元素的最大宽度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)在代码中。 如果不设置此值，滚动条不会显示，甚至当列表框中的项都超过框。

## <a name="align-controls"></a>对齐控件

- 若要对齐控件，选择你想要对齐的控件。 转到菜单**格式** > **对齐**，然后选择以下的对齐方式：

   |对齐方式|描述|
   |-----|-----------|
   |**左对齐**|将所选的控件沿它们的左边对齐。|
   |**中心**|将所选的控件水平沿其中心点。|
   |**权限**|将所选的控件沿其右侧。|
   |**顶部**|将所选的控件沿上边缘。|
   |**中间对齐**|将所选的控件它们的中心点沿垂直方向对齐。|
   |**底端**|将所选的控件沿其下边缘对齐。|

   请务必选择你想要首先主导控件或将其设置为主导控件之前执行对齐方式或大小调整命令，如最后一个控件组的位置取决于主导控件的位置。

- 平均空间控件，选择你想要重新排列这些的控件。 转到菜单**格式** > **均匀隔开**，然后选择以下间距对齐方式：

   |间距|描述|
   |---|---|
   |**跨**|最左侧和所选最右边的控件之间均匀分配的空间控件。|
   |**向下**|最上面和最下面选择的控件之间均匀分配的空间控件。|

- 若要置于控件，选择你想要重新排列的控件。 转到菜单**格式** > **在对话框内居中**，然后选择下列排列方式：

   |排列方式|描述|
   |---|---|
   |**垂直**|在对话框中垂直居中对齐控件。|
   |**水平**|在对话框中水平居中对齐控件。|

- 若要对齐普通按钮，选择一个或多个推送按钮。 转到菜单**格式** > **排列按钮**，然后选择以下的排列方式之一：

   |排列方式|描述|
   |---|---|
   |右侧|对齐普通按钮的对话框中的右边缘。|
   |底部|对齐对话框的底部边缘的普通按钮。|

   如果选择不是普通按钮控件，其位置不受影响。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[管理对话框控件](controls-in-dialog-boxes.md)<br/>
[如何：添加、编辑或删除控件](adding-editing-or-deleting-controls.md)<br/>
[如何：定义控件访问权限和值](defining-mnemonics-access-keys.md)<br/>