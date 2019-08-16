---
title: 工具栏编辑器 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514688"
---
# <a name="toolbar-editor-c"></a>工具栏编辑器 (C++)

利用**工具栏编辑器**, 可以创建工具栏资源并将位图转换为工具栏资源。 **工具栏编辑器**使用图形显示来显示工具栏和按钮, 它们与它们在已完成的应用程序中的显示效果大致相似。

**工具栏编辑器**窗口显示按钮图像的两个视图, 与 "**图像编辑器**" 窗口相同。 拆分栏分隔两个窗格, 你可以将拆分条从一端拖动到另一端来更改窗格的相对大小。 "活动" 窗格显示选择边框, 在图像的两个视图上方是主题工具栏。

![工具栏编辑器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**工具栏编辑器**

**工具栏编辑器**类似于功能中的**图像编辑器**, 两者之间的菜单项、图形工具和位图网格是相同的。 "**图像**" 菜单中有一个菜单命令, 可在**工具栏编辑器**和**图像编辑器**之间切换。 有关使用**图形**工具栏、调色板或**图像**菜单的详细信息, 请参阅[图像编辑器](../windows/image-editor-for-icons.md)。

通过转换位图, 可以在C++项目中创建新的工具栏。 位图中的图形会转换为工具栏的按钮图像。 位图通常在单个位图上包含多个按钮图像, 每个按钮有一个图像。 图像可以为任意大小, 因为默认值为16像素宽和图像的高度。 在 "**图像编辑器**" 中的 "**图像**" 菜单中选择 "**工具栏编辑器**" 时, 可以在 "**新建工具栏资源**" 对话框中指定按钮图像的大小。

使用 "**新建工具栏资源**" 对话框可以指定要添加到C++项目中的工具栏资源的按钮的宽度和高度。 默认值为16×15像素。

用于创建工具栏的位图的最大宽度为 2048, 因此, 如果将该**按钮的宽度**设置为*512*, 则只能使用四个按钮。 如果将宽度设置为*513*, 则只能有三个按钮。

"**新建工具栏资源**" 对话框具有下列属性:

|Property|描述|
|---|---------------|
|**按钮宽度**|为您提供空间, 用于输入要从位图资源转换为工具栏资源的工具栏按钮的宽度。|
|**按钮高度**|提供空间以输入要从位图资源转换为工具栏资源的工具栏按钮的高度。|

> [!NOTE]
> 将图像裁剪为指定的宽度和高度, 并调整颜色以使用标准工具栏颜色 (16 种颜色)。

默认情况下, 工具栏的右端将显示一个新的或空白的按钮。 你可以在编辑此按钮之前移动它。 创建新按钮时, "编辑" 按钮的右侧会出现另一个空白按钮。 保存工具栏后, 不会保存空白按钮。

工具栏按钮具有以下属性:

|Property|描述|
|--------------|-----------------|
|**ID**|定义按钮的 ID。 下拉列表提供通用**ID**名称。|
|**Width**|设置按钮的宽度。 建议使用16像素。|
|**Height**|设置按钮的高度。 一个按钮的高度会改变工具栏上所有按钮的高度。 建议使用15像素。|
|**提示**|定义显示在状态栏中的消息。 添加 *\n* ，并将添加一个名称**工具提示**向工具栏按钮。 有关详细信息, 请参阅[创建工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|

**宽度**和**高度**适用于所有按钮。 用于创建工具栏的位图的最大宽度为 2048, 因此, 如果将该按钮的宽度设置为*512*, 则只能使用四个按钮, 如果将宽度设置为*513*, 则只能有三个按钮。

## <a name="how-to"></a>操作说明

**工具栏编辑器**允许您:

### <a name="to-create-new-toolbars"></a>创建新工具栏

1. 在**资源视图**中, 右键单击 *.rc*文件, 然后选择 "**添加资源**"。 如果 *.rc*文件中已有一个工具栏, 则可以右键单击**工具栏**文件夹, 然后选择 "**插入工具栏**"。

1. 在 "**添加资源**" 对话框中, 选择 "**资源类型**" 列表中的 "**工具栏**", 然后选择 "**新建**"。

   如果工具栏资源类型旁边 **+** 出现一个加号 () , 则表示工具栏模板可用。 选择加号以展开模板列表, 选择模板, 然后选择 "**新建**"。

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>将位图转换为工具栏资源

1. 在[图像编辑器](../windows/image-editor-for-icons.md)中打开现有的位图资源。 如果该位图还不在 *.rc*文件中, 请右键单击 *.rc*文件, 然后选择 "**导入**", 然后导航到要添加到 *.rc*文件的位图, 然后选择 "**打开**"。

1. 中转到菜单**图像** > **工具栏编辑器**。

   此时将显示 "**新建工具栏资源**" 对话框。 您可以更改图标图像的宽度和高度, 使之与位图匹配。 然后, 工具栏图像将显示在**工具栏编辑器**中。

1. 若要完成转换, 请使用[属性窗口](/visualstudio/ide/reference/properties-window)更改按钮的命令**ID** 。 键入新*id*或从下拉列表中选择**id** 。

   > [!TIP]
   > "**属性**" 窗口在标题栏中包含一个图钉按钮, 然后选择此项可以启用或禁用窗口**自动隐藏**。 若要循环浏览所有工具栏按钮属性, 而无需重新打开各个属性窗口, 请关闭**自动隐藏**, 这样 "**属性**" 窗口将保持不变。

   还可以通过使用[属性窗口](/visualstudio/ide/reference/properties-window)更改新工具栏上的按钮的命令 id。

### <a name="to-manage-toolbar-buttons"></a>管理工具栏按钮

#### <a name="to-create-a-new-toolbar-button"></a>创建新的工具栏按钮

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)展开资源文件夹 (例如, *Project1*)。

1. 展开**工具栏**文件夹, 选择要编辑的工具栏, 然后执行下列操作之一:

   - 向工具栏右端的空白按钮分配 ID。 可以通过在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中编辑 " **ID** " 属性来执行此操作。 例如, 你可能想要为工具栏按钮提供与菜单选项相同的 ID。 在这种情况下, 请使用下拉列表框选择菜单选项的**ID** 。

   - 选择**工具栏视图**窗格中工具栏右端的空白按钮, 然后开始绘制。 分配默认按钮命令 ID (ID_BUTTON\<n >)。

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>将图像作为按钮添加到工具栏

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中, 通过双击来打开工具栏。

1. 接下来, 打开要添加到工具栏的映像。

   > [!NOTE]
   > 如果在 Visual Studio 中打开该图像, 它将在**图像编辑器**中打开。 您还可以在其他图形程序中打开该图像。

1. 中转到菜单**编辑** > **副本**。

1. 通过选择工具栏上的 "源" 窗口顶部的选项卡来切换到工具栏。

1. "切换到菜单" "**编辑** > " "**粘贴**"。

   图像将作为新按钮出现在工具栏上。

#### <a name="to-move-a-toolbar-button"></a>移动工具栏按钮

在工具栏的 "**视图**" 窗格中, 将要移动的按钮拖动到工具栏上的新位置。

- 若要从工具栏中复制按钮, 请按住**Ctrl**键, 然后在**工具栏视图**窗格中, 将按钮拖动到工具栏上的新位置或另一个工具栏上的某个位置。

- 若要删除工具栏按钮, 请选择工具栏按钮, 然后将其拖到工具栏中。

- 若要在工具栏上的按钮之间插入或删除空格, 请在工具栏上的按钮之间进行拖放。

|操作|步骤|
|------|------|
|在不后跟空格的按钮之前插入空格|向右或向下拖动按钮, 直到它与 "下一步" 按钮约一半重叠。|
|在按钮前插入一个空格, 后面跟一个空格并保留尾随空格|拖动按钮, 直到右边缘或下边缘只触及 "下一步" 按钮或只是重叠。|
|在按钮前插入一个空格, 后面跟一个空格并关闭后面的空格|向右或向下拖动按钮, 直到它与 "下一步" 按钮约一半重叠。|
|在工具栏上的按钮之间删除空格|将位于空间一侧的按钮拖到空间另一侧的按钮上, 直到它与 "下一步" 按钮大约一半。|

> [!NOTE]
> 如果要拖动的按钮一侧没有空间, 而您拖动按钮的次数超过了相邻按钮的一半, 则**工具栏编辑器**会在要拖动的按钮的另一侧插入一个空格。

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>更改工具栏按钮的属性

1. 在C++项目中, 选择工具栏按钮。

1. 在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)的 " **ID** " 属性中键入新 id, 或使用下拉列表选择新**id**。

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>为工具栏按钮创建工具提示

1. 选择工具栏按钮。

1. 在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)的 "**提示**" 字段中, 为状态栏和消息后添加按钮的说明, 添加`\n`和工具提示名称。

例如, 若要在**写字板**中查看 "**打印**" 按钮的工具提示:

1. 打开 "**写字板**"。

1. 将鼠标指针悬停在 "**打印**" 工具栏按钮上, 并`Print`注意到现在单词在鼠标指针下浮动。

1. 查看 "**写字板**" 窗口底部的状态栏, 注意它现在会显示文本`Prints the active document`。

`Print`是工具提示名称, `Prints the active document`是状态栏的按钮的说明。

如果希望使用**工具栏编辑器**产生这种效果, 请将**Prompt**属性设置`Prints the active document\nPrint`为。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)
[菜单和其他资源](/windows/win32/menurc/resources)<br/>
[工具栏按钮属性](../windows/toolbar-button-properties.md)<br/>
