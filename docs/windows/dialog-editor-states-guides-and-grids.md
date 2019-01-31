---
title: 对话框编辑器状态 （参考线和网格） （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484989"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>对话框编辑器状态 （参考线和网格） （c + +）

你可以排列控件上使用对话框**对话框**编辑器在以下三种不同状态：

- 参考线和边距上 （默认设置）

- 与上的布局网格

- 不包含任何对齐或对齐方式功能

[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制的状态的按钮。 若要更改状态，请单击相应图标。 此外可以通过更改状态**参考线设置**命令**格式**菜单。

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

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="create-and-set-guides-and-margins"></a>创建并设置参考线和边距

是否正在移动控件，添加控件，或重新排列当前布局，指南可帮助您对齐控件在对话框中精确地。 参考线显示为蓝色点线横跨编辑器，然后在顶部和左侧和右侧的标尺中的相应箭头显示的对话框**对话框**编辑器。

当创建一个对话框时，将提供四个边距。 边距是修改后的参考线，以蓝色点线显示。

### <a name="to-create-a-guide"></a>若要创建参考线

标尺，请在单击一次以创建参考线。 (单击一次创建一个新指南; 双击启动**参考线设置**可以在其中指定参考线设置对话框。)

### <a name="to-set-a-guide"></a>若要设置参考线

在对话框中，单击该指南并将其拖动到新位置。 （您可以单击标尺拖动相关联的指南中的箭头）。

本指南的坐标被显示在窗口底部的状态栏和标尺中。 将指针移动标尺以显示该指南的准确位置中的箭头。

### <a name="to-delete-a-guide"></a>删除参考线

将指南拖出对话框的。

\- 或 -

将拖离标尺相应的箭头。

### <a name="to-move-margins"></a>若要移动边距

拖动到新位置的边距。

若要使边距消失，移动到零位置的边距。 若要使重新边距，将鼠标指针放在边距的零位置并将边距移至相应位置。

## <a name="align-controls-on-a-guide"></a>在参考线上对齐控件

当移动控件，并参考线对齐控件是否存在任何控件之前对齐到指南时，控件的大小调整句柄对齐参考线。 一条参考线移动时，会对齐到它的控件也同时移动。 参考指南之一移动时调整大小将与多个指南对齐的控件。

由对话框单元 (Dlu) 定义中确定的指南和控件的间距标尺刻度。 DLU 基于对话框字体，通常的 8 磅 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体平均宽度。 垂直 DLU 是字体的平均除以 8 的高度。

### <a name="to-size-a-group-of-controls-with-guides"></a>若要通过指南大小的一组控件

1. 与参考线对齐控件 （或控件） 的一侧。

1. 拖动控件 （或控件） 的另一端的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

1. 将移动任一调整大小的控件 （或控件） 的指南。

### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要更改的时间刻度线的间隔

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中**网格间距**字段中，指定新的宽度和高度 Dlu。

## <a name="disable-guides"></a>禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>若要禁用参考线的对齐效果

此时，一直向下拖动控件**Alt**密钥。

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>若要移动的参考线，而无需移动对齐的控件

此时，一直向下拖动参考线**Shift**密钥。

### <a name="to-turn-off-the-guides"></a>若要关闭这些指南

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中的**版式参考线**，选择**None**。

   > [!NOTE]
   > 此外可以双击标尺栏以便访问**参考线设置**对话框。

\- 或 -

上**格式**菜单中，选择**切换辅助线**。

## <a name="modify-the-layout-grid"></a>修改布局网格

当要放置或排列控件在对话框中的时，可用于更精确地定位布局网格。 打开网格时，将显示控件与"对齐"网格的虚线像磁化。 您可以打开和关闭此"对齐网格"功能和更改布局网格单元格的大小。

### <a name="to-turn-the-layout-grid-on-or-off"></a>若要打开或关闭的布局网格

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框中，选中或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框中**使用的编辑器窗口**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

### <a name="to-change-the-size-of-the-layout-grid"></a>若要更改布局网格的大小

1. 从**格式**菜单中，选择**参考线设置**。

1. 在中**参考线设置**对话框框中，在网格中的单元格 Dlu 中键入的高度和宽度。 最小高度或宽度为 4 个 Dlu。 Dlu 的详细信息，请参阅[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件 (MFC)](../mfc/controls-mfc.md)<br/>
