---
title: 演练：将控件置于工具栏上
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 0c62a8b484cb666427f873244221afec5d4719da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510739"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>演练：将控件置于工具栏上

本文介绍如何将包含 Windows 控件的工具栏按钮添加到工具栏中。 在 MFC 中, 工具栏按钮必须是[CMFCToolBarButton 类](../mfc/reference/cmfctoolbarbutton-class.md)派生类, 例如[CMFCToolBarComboBoxButton 类](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)、 [CMFCToolBarEditBoxButton 类](../mfc/reference/cmfctoolbareditboxbutton-class.md)、 [CMFCDropDownToolbarButton 类](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)或[CMFCToolBarMenuButton 类](../mfc/reference/cmfctoolbarmenubutton-class.md)。

## <a name="adding-controls-to-toolbars"></a>将控件添加到工具栏

若要将控件添加到工具栏，请执行以下步骤：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。 有关如何在 Visual Studio 中使用**工具栏编辑器**创建按钮的详细信息, 请参阅 "[工具栏编辑器](../windows/toolbar-editor.md)" 一文。

1. 在父级工具栏的所有位图中保留该按钮的工具栏图像（按钮图标）。

1. 在处理`AFX_WM_RESETTOOLBAR`消息的消息处理程序中, 执行以下步骤:

   1. 使用 `CMFCToolbarButton` 派生的类构造此按钮控件。

   1. 使用[CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)将虚拟按钮替换为新控件。 可在堆栈上构造按钮对象，因为 `ReplaceButton` 会复制按钮对象并保留副本。

> [!NOTE]
>  如果在应用程序中启用了自定义, 则可能必须使用 "**自定义**" 对话框的 "**工具栏**" 选项卡上的 "**重置**" 按钮重置工具栏, 才能在重新编译后查看应用程序中已更新的控件。 工具栏状态将保存在 Windows 注册表中，并且在应用程序启动期间，在执行 `ReplaceButton` 方法后将加载并应用注册表信息。

## <a name="toolbar-controls-and-customization"></a>工具栏控件和自定义

"**自定义**" 对话框的 "**命令**" 选项卡包含可在应用程序中使用的命令的列表。 默认情况下, "**自定义**" 对话框处理应用程序菜单, 并在每个菜单类别中生成标准工具栏按钮的列表。 若要保持工具栏控件提供的扩展功能, 必须将标准工具栏按钮替换为自定义对话框中的自定义控件。

启用自定义时, 可以通过使用[CMFCToolBarsCustomizeDialog 类](../mfc/reference/cmfctoolbarscustomizedialog-class.md)类在自定义处理`OnViewCustomize`程序中创建 "**自定义**" 对话框。 在通过调用[CMFCToolBarsCustomizeDialog:: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)显示 "**自定义**" 对话框之前, 调用[CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)将标准按钮替换为新控件。

## <a name="example-creating-a-find-combo-box"></a>示例:创建 "查找" 组合框

本部分介绍如何创建显示在工具栏上并包含最近使用过的搜索字符串的 "**查找**" 组合框控件。 用户可在控件中键入一个字符串，然后按 Enter 键来搜索文档，或按 Esc 键将焦点返回主框架。 此示例假定文档穦 [CEditView 类](../mfc/reference/ceditview-class.md)-派生的视图。

### <a name="creating-the-find-control"></a>创建 Find 控件

首先, 创建 "**查找**" 组合框控件:

1. 将此按钮及其命令添加到应用程序资源：

   1. 在应用程序资源中，将命令 ID 为 `ID_EDIT_FIND` 的新按钮添加到应用程序中的工具栏以及与此工具栏相关的任何位图。

   1. 使用`ID_EDIT_FIND`命令 ID 创建新的菜单项。

   1. 将新字符串“Find the text\nFind”添加到字符串表并为其分配 `ID_EDIT_FIND_COMBO` 命令 ID。 此 ID 将用作 "**查找**" 组合框按钮的命令 id。

        > [!NOTE]
        > 由于 `ID_EDIT_FIND` 是一个由 `CEditView` 处理的标准命令，因此您不需要为此命令实现特殊处理程序。  但是，您必须实现新命令 `ID_EDIT_FIND_COMBO` 的处理程序。

1. 创建一个派生自`CFindComboBox` [CComboBox 类](../mfc/reference/ccombobox-class.md)的新类。

1. 在 `CFindComboBox` 类中，重写 `PreTranslateMessage` 虚方法。 此方法将启用组合框来处理[WM_KEYDOWN](/windows/win32/inputdev/wm-keydown)消息。 如果用户点击 Esc 键 (`VK_ESCAPE`)，则将焦点返回到主框架窗口。 如果用户点击 Enter 键 (`VK_ENTER`)，则会向主框架窗口发送一条包含 `WM_COMMAND` 命令 ID 的 `ID_EDIT_FIND_COMBO` 消息。

1. 为 "**查找**" 组合框按钮创建一个类, 该类派生自[CMFCToolBarComboBoxButton 类](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。 在此示例中，命名为 `CFindComboButton`。

1. `CMFCToolbarComboBoxButton` 的构造函数具有三个参数：按钮的命令 ID、按钮图像索引和组合框的样式。 按以下方式设置这些参数：

   1. 将 `ID_EDIT_FIND_COMBO` 作为命令 ID 传递。

   1. 使用[CCommandManager:: GetCmdImage](reference/internal-classes.md) `ID_EDIT_FIND`获取图像索引。

   1. 有关可用组合框样式的列表, 请参阅[组合框样式](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

1. 在 `CFindComboButton` 类中，重写 `CMFCToolbarComboBoxButton::CreateCombo` 方法。 在这里，您应创建 `CFindComboButton` 对象并返回一个指向该对象的指针。

1. 使用[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏将组合按钮设置为永久性。 工作区管理器自动加载按钮状态并将其保存在 Windows 注册表中。

1. 在文档视图中实现 `ID_EDIT_FIND_COMBO` 处理程序。 使用[CMFCToolBar:: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) `ID_EDIT_FIND_COMBO`来检索所有**查找**组合框按钮。 由于自定义，因此存在具有同一命令 ID 的多个按钮副本。

1. 在消息处理程序`OnFind`中, 使用[CMFCToolBar:: IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton)来确定是否已从 "查找" 组合框按钮发送 "查找" 命令。 `ID_EDIT_FIND` 如果是这样，则查找文本并将搜索字符串添加到组合框。

### <a name="adding-the-find-control-to-the-main-toolbar"></a>将 find 控件添加到主工具栏

若要将组合框按钮添加到工具栏，请执行以下步骤：

1. 在主框架窗口中实现 `AFX_WM_RESETTOOLBAR` 消息处理程序 `OnToolbarReset`。

    > [!NOTE]
    > 在应用程序启动期间初始化工具栏时或在自定义期间重置工具栏时，此框架会将该消息发送到主框架窗口。 在任一情况下, 都必须将标准工具栏按钮替换为 "自定义**查找**" 组合框按钮。

1. 在处理程序中, 检查工具栏 ID, 即 AFX_WM_RESETTOOLBAR 消息的*WPARAM。* `AFX_WM_RESETTOOLBAR` 如果工具栏 ID 等于包含 "**查找**" 组合框按钮的工具栏的 ID, 请调用[CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)来替换 "**查找**" 按钮 (即带有包含`ID_EDIT_FIND)` `CFindComboButton`对象的命令 ID 的按钮)。

    > [!NOTE]
    > 您可以在堆栈上构造 `CFindComboBox` 对象，因为 `ReplaceButton` 会复制此按钮对象并保留副本。

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>将 Find 控件添加到“自定义”对话框

在自定义处理`OnViewCustomize`程序中调用[CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)以将 "**查找**" 按钮 (即带有命令 ID `ID_EDIT_FIND`的按钮) `CFindComboButton`替换为对象。

## <a name="see-also"></a>请参阅

[层次结构图](../mfc/hierarchy-chart.md)<br/>
[类](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 类](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 类](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog 类](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
