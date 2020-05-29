---
title: 如何：布局控件（C++） |Microsoft Docs
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
ms.openlocfilehash: ee732cfb414f011e95edbbb57b218d81179d44f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168572"
---
# <a name="how-to-layout-controls-c"></a>如何：布局控件（C++）

**对话框编辑器**提供了自动对齐和调整控件大小的布局工具。 对于大多数任务，您可以使用[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。 "**格式**" 菜单上还提供了所有 "**对话框编辑器**" 工具栏命令，其中大多数都具有[快捷键](../windows/accelerator-keys-for-the-dialog-editor.md)。

仅当选择了多个控件时，对话框的许多布局命令才可用。 您可以选择单个控件或多个控件，选择多个控件时，您选择的第一个控件默认为主导控件。

当前控件的位置、高度和宽度显示在状态栏的右下角。 当整个对话框处于选中状态时，状态栏将显示对话框的整体位置及其高度和宽度。

## <a name="arrange-controls"></a>排列控件

您可以将对话框中的控件与**对话框编辑器**一起排列在三种不同的状态之一：

- 对于上的参考线和边距，将设置为默认值。

- 布局网格位于上。

- 没有任何对齐或对齐功能。

"[对话框编辑器" 工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制状态的按钮。

- 若要更改状态，请选择相应的图标，或转到 " > **指南设置**" 的 "菜单**格式**"。

"**参考线设置**" 对话框具有下列属性：

|properties|说明|
|---|---|
|**布局参考线**|显示布局指南的设置。|
|无|隐藏布局工具。|
|**标尺和参考线**|启用后，会将标尺添加到布局工具，并允许在标尺中放置参考线。 默认指南为边距。|
|**网格**|创建布局网格。 新控件将自动与网格对齐。|
|**网格间距**|显示对话框单位（Dlu）中网格间距的设置。|
|**Width： Dlu**|设置以 Dlu 为单位的布局网格的宽度。 水平 DLU 是对话框字体除以4的平均宽度。|
|**高度： Dlu**|设置以 Dlu 为单位的布局网格高度。 垂直 DLU 是对话框字体的平均高度除以8。|

### <a name="guides-and-margins"></a>参考线和边距

无论是移动控件、添加控件，还是重新排列当前布局、参考线和边距，都可以帮助您在对话框内准确对齐控件。

创建对话框时，将提供四个称为 "边距" 的已修改的参考线，并将其显示为蓝色虚线。

- 若要移动边距，请将边距拖到新位置。

- 若要使边距消失，请将边距移动到零位置。

- 若要恢复边距，请将指针放在边距的零位置上，并将边距移动到位置。

参考线在编辑器中显示的对话框中显示为蓝色虚线，并显示在**对话框编辑器**顶部和顶部的标尺中的相应箭头内。 当移动控件时，控件的大小调整手柄将与参考线对齐; 如果前面没有任何控件与指南对齐，则辅助线对齐控件。 移动指南时，与之对齐的控件也将移动。 当移动某个指南时，将调整与多个指南对齐的控件的大小。

- 若要在标尺内创建指南，请选择 "一次" 以创建指南，或双击以启动 "**参考线设置**" 对话框，在其中可以指定 "参考线设置"。

- 若要在对话框中设置指南，请选择指南并将其拖到新位置，或选择标尺中的箭头拖动相关的指南。

   参考线的坐标显示在窗口底部的状态栏中和标尺上，或将指针移到标尺中的箭头上方，以显示参考线的确切位置。

- 若要删除某个指南，请将该指南拖出对话框，或将相应的箭头拖离标尺。

标尺中确定参考线和控件间距的刻度线由对话单位（Dlu）定义。 DLU 基于对话框字体的大小，通常为8点 MS Shell Dlg。 水平 DLU 是指用四个对话框字体分隔的平均宽度。 垂直 DLU 是该字体的平均高度除以8。

- 若要更改刻度线的间隔，请转到 "菜单**格式**" > "**参考线设置**"，然后在 "**网格间距**" 字段中指定以 dlu 为单位的新宽度和高度。

### <a name="layout-grid"></a>布局网格

当你在对话框中放置或排列控件时，请使用布局网格来更精确地定位。 当网格打开时，控件将与网格线对齐，就像磁化一样。

- 若要打开或关闭布局网格，请转到 "菜单**格式** > "**指南设置**"，然后选择或清除"**网格**"按钮。

   你仍可以使用 "[对话框编辑器" 工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)上的 "**切换网格**" 按钮来控制各个**对话框编辑器**窗口中的网格。

- 若要更改布局网格的大小，请转到 "菜单**格式** > "**指南设置**"，然后在" 网格 "中为单元格键入 dlu 的高度和宽度。 最小高度或宽度为4。

### <a name="disable-guides"></a>禁用参考线

您可以将特殊键与鼠标结合使用来禁用参考线的对齐效果。 使用**Alt**键禁用所选指南的对齐效果。 使用**Shift**键移动指南可防止对齐的控件与指南一起移动。

- 若要禁用参考线的对齐效果，请在按住**Alt**键的同时拖动控件。

- 若要移动参考线而不移动对齐的控件，请在按住**Shift**键的同时拖动参考线。

- 若要关闭指南，请转到 "菜单**格式**" > **指南设置**"。 然后，在 "**布局指南**" 下，选择 "**无**"。

   > [!TIP]
   > 还可以使用菜单**格式**的快捷方式 > **切换参考线**。

## <a name="select-controls"></a>选择控件

选择要调整大小、对齐、移动、复制或删除控件的控件，然后完成所需的操作。 在大多数情况下，您需要在[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)上选择多个控件以使用大小调整和对齐工具。

选择控件时，该控件的周围有阴影边框，其中包含纯色（活动）或空心（非活动）大小调整控点，即显示在选择边框中的小方块。 如果选择了多个控件，则主导控件具有实尺寸控点，并且所有其他选定控件都具有空白尺寸控点。

- 若要选择控件，请在 "[工具箱" 窗口](/visualstudio/ide/reference/toolbox)中选择 "**指针**" 工具，然后使用以下步骤之一进行选择：

  - 拖动指针以在对话框中要选择的控件周围绘制选择框。 释放鼠标按钮后，选择框内和下的所有控件都将处于选中状态。

  - 按住**Shift**键并选择要包含在选定内容中的控件。

  - 按住**Ctrl**键并选择要包含在选定内容中的控件。

- 若要在选定控件组中添加或删除控件，请按住**Shift**键并选择要添加或删除的控件。

### <a name="dominant-controls"></a>主导控件

当调整多个控件的大小时，**对话框编辑器**将使用主导控件来确定其他控件如何调整大小或对齐。 默认情况下，主导控件是选定的第一个控件。

- 若要指定主导控件，请按住**Ctrl**键并选择要用于影响其他控件的大小或位置的*控件。* 按住**Ctrl**键并选择所选内容中的控件也将使该选择中的主导控件成为控件。

- 若要更改主导控件，请在当前选定的所有控件外进行选择，清除当前选择，然后重复上述过程，*首先*选择一个不同的控件。

> [!NOTE]
> 主导控件的大小调整句柄是纯色的，而从属控件的句柄是空心的。 所有进一步的大小调整或对齐都基于主导控件。

## <a name="size-controls"></a>大小控件

使用大小调整控点重设控件的大小。 当指针定位到大小调整控点上时，它会更改形状以指示控件的大小调整方向。 活动的调整大小控点为实线，如果调整大小控点为空心，则不能沿该轴调整控件的大小。

- 若要调整控件大小，请选择控件，并拖动调整大小控点以更改大小。

  - 顶部和侧面的大小控点将更改水平或垂直大小。

  - 拐角处的大小控点同时更改水平和垂直大小。

   > [!TIP]
   > 可以通过按住**Shift**键并使用**向右**和**向下**箭头键，一次调整控件一个对话框单位（DLU）的大小。

- 若要自动调整控件的大小以适应其中的文本，请参阅菜单**格式**或右键单击控件，然后选择 "**大小为内容**"。

- 若要使控件具有相同的大小，请选择要调整大小的控件并选择 "打开" 菜单**格式** > "**使大小相同**"，然后选择 "高"、"**高度**"**或 "** **宽度**"。

   根据主导控件的大小调整控件组的大小，该控件是序列中第一个选定的控件。 组中控件的最终大小取决于主导控件的大小。

- 若要调整控件组的大小和参考线，请将控件的一侧对齐到一个指南，然后将一个指南拖到控件的另一侧（或控件）。 现在，你可以移动任一指南来调整控件的大小（或控件）。

   如果有多个控件需要，请调整每个控件的大小以与第二个指南对齐。

### <a name="other-controls"></a>其他控件

将组合框添加到对话框中时，可以调整组合框的大小。 您还可以指定下拉列表框的大小。 有关详细信息，请参阅向[组合框控件添加值](../windows/adding-values-to-a-combo-box-control.md)。

1. 选择组合框右侧的下拉箭头按钮。

   ![MFC 项目中组合框上的箭头](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控件的轮廓将更改为显示组合框的大小，并扩展下拉列表区域。

1. 使用较低的调整大小控点来更改下拉列表区域的初始大小。

   ![MFC&#45;项目中的组合框大小调整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 再次选择下拉箭头以关闭组合框的下拉列表部分。

> [!NOTE]
> 当使用 MFC 向对话框添加水平滚动条的列表框时，滚动条不会自动显示在应用程序中。
>
> 通过在代码中调用[CListBox：： SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ，为最宽元素设置最大宽度。 如果未设置此值，则即使列表框中的项大于框，也不会显示滚动条。

## <a name="align-controls"></a>对齐控件

- 若要对齐控件，请选择要对齐的控件。 "中转到" 菜单**格式** > **对齐**"，然后选择以下对齐方式之一：

   |Alignment|说明|
   |-----|-----------|
   |**对齐**|将选定控件沿其左侧对齐。|
   |**中心**|沿中心点水平对齐选定的控件。|
   |权限|将选定控件沿其右边缘对齐。|
   |**祝愿**|将选定控件沿其上边缘对齐。|
   |**对齐**|将选定控件沿其中间点垂直对齐。|
   |**底端**|将选定控件沿其下边缘对齐。|

   请确保先选择要进行主导的控件或将其设置为主导控件，然后再执行对齐或调整大小命令，因为控件组的最终位置取决于主导控件的位置。

- 若要均匀隔开控件，请选择要重新排列的控件。 "中转到" 菜单**格式** > **间距**"，然后选择以下间距对齐方式之一：

   |间距|说明|
   |---|---|
   |**对**|在选定的最左侧和最右边的控件之间平均间隔控制。|
   |**向下**|在选定的最顶部和最底层控件之间平均间隔控制。|

- 若要使控件居中，请选择要重新排列的控件。 **在对话框中 > "** 开始" 菜单**格式**，然后选择以下排列方式之一：

   |排列|说明|
   |---|---|
   |**垂直**|在对话框中将控件垂直居中。|
   |**水平**|使控件在对话框中水平居中。|

- 若要对齐 "推送" 按钮，请选择一个或多个 "推送" 按钮。  > "**排列" 按钮**，请参阅 "菜单**格式**"，然后选择以下排列方式之一：

   |排列|说明|
   |---|---|
   |**Right**|沿对话框的右边缘对齐 "推送" 按钮。|
   |底部|沿对话框下边缘对齐 "推送" 按钮。|

   如果选择的控件不是 "推送" 按钮，则其位置不受影响。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[管理对话框控件](controls-in-dialog-boxes.md)<br/>
[如何：添加、编辑或删除控件](adding-editing-or-deleting-controls.md)<br/>
[如何：定义控件访问和值](defining-mnemonics-access-keys.md)<br/>
