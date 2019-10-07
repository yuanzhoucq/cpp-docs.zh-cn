---
title: 菜单编辑器（C++）
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: f2a5f1ac63007bf44dc331e2104c6e9e5cac23da
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514823"
---
# <a name="menu-editor-c"></a>菜单编辑器（C++）

使用菜单，可以按照逻辑方式和易于查找的方式排列命令。 使用**菜单编辑器**，可以通过直接使用与已完成的应用程序中类似的菜单栏来创建和编辑菜单。

> [!TIP]
> 使用**菜单编辑器**时，在许多情况下，你可以右键单击以显示常用命令的弹出菜单。 可用命令取决于指针所指向的内容。

## <a name="how-to"></a>操作说明

**菜单编辑器**可用于：

### <a name="to-create-a-standard-menu"></a>创建标准菜单

1. **资源视图**"中转到" 菜单**视图** > "，然后右键单击**菜单**标题。 选择 "**添加资源**"，然后选择 "**菜单**"。

1. 在菜单栏上选择 "**新建项**" 框（此处包含 "*类型*" 的矩形）。

   ![菜单编辑器中的 "新建项" 框](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **新项**框

1. 键入新菜单的名称，例如 "*文件*"。

   键入的文本将同时出现在**菜单编辑器**和 "[属性" 窗口](/visualstudio/ide/reference/properties-window)的 "**标题**" 框中。 你可以在任一位置编辑新菜单的属性。

   为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。

   ![展开的 "新建项" 框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   键入菜单名称后焦点已移动的 "**新建项**" 框

   > [!NOTE]
   > 若要在菜单栏上创建单项菜单，请将**Popup**属性设置为**False**。

### <a name="to-create-a-submenu"></a>创建子菜单

1. 选择要为其创建子菜单的菜单命令。

1. 在出现在右侧的 **新项** 框显中键入新的菜单命令的名称。 此新命令将在子菜单的菜单中显示为第一个。

1. 将其他菜单命令添加到子菜单的菜单中。

### <a name="to-insert-a-new-menu-between-existing-menus"></a>在现有菜单之间插入新菜单

选择现有菜单名称并按**Insert**键，或右键单击菜单栏，然后选择 "**插入新**项"。

   **新项**框将插入到选定项的前面。

### <a name="to-add-commands-to-a-menu"></a>将命令添加到菜单

1. 创建菜单。 然后选择菜单名称，例如 "**文件**"。

   每个菜单都将展开，并显示一个新项框让你输入命令。 例如，可以将 "**新建**"、"**打开**" 和 "**关闭**" 命令添加到 "**文件**" 菜单。

1. 在新项框中，键入新菜单命令的名称。

   > [!NOTE]
   > 键入的文本将同时出现在**菜单编辑器**和 "[属性" 窗口](/visualstudio/ide/reference/properties-window)的 "**标题**" 框中。 你可以在任一位置编辑新菜单的属性。

   > [!TIP]
   > 你可以定义一个允许用户选择菜单命令的助记键（热键）。 在字母前面键入`&`与号（），将其指定为助记键。 用户可以通过键入该字母来选择菜单命令。

1. 在 "**属性**" 窗口中，选择适用的菜单命令属性。 有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。

1. 在 "**属性**" 窗口的 "**提示**" 框中，键入想要在应用程序状态栏中显示的提示字符串。

   此步骤将在字符串表中创建一个条目，该条目的资源标识符与创建的菜单命令相同。

   > [!NOTE]
   > 提示只能应用于**Popup**属性为**True**的菜单项。 例如，包含子菜单项的顶级菜单项可以有提示。 **提示符**的用途是指示在用户选择菜单项时将发生的情况。

1. 按**enter**完成菜单命令。

   将选定新项框，让你可以创建其他菜单命令。

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>选择多个菜单命令以运行批量操作，如删除或更改属性

按住**Ctrl**键的同时选择所需的菜单或子菜单命令。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>移动和复制菜单和菜单命令

- 使用拖放方法：

   1. 拖动或复制要移到下列位置的项：

      - 当前菜单上的新位置。

      - 不同的菜单。 可以通过将鼠标指针拖到其他菜单上来导航到这些菜单。

   1. 当插入参考线显示所需位置时放下菜单命令。

- 使用快捷菜单命令：

   1. 右键单击一个或多个菜单或菜单命令，然后选择 "**剪切**" （移动）或 "**复制**"。

   1. 如果要将项移到另一个菜单资源或资源脚本文件，请[在另一个窗口中将其打开](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

   1. 选择要将菜单或菜单命令移动或复制到的位置。

   1. 从快捷菜单中选择 **“粘贴”** 。 被移动或复制的项放在选定项的前面。

> [!NOTE]
> 还可以拖动、复制和粘贴到其他菜单窗口中的其他菜单中。

### <a name="to-delete-a-menu-or-menu-command"></a>若要删除菜单或菜单命令

右键单击菜单名称或命令，然后选择 "**删除**"。

> [!NOTE]
> 同样，可以使用快捷菜单来执行其他操作，例如，复制、剪切、粘贴、插入新项、插入分隔符、编辑 ID、以弹出方式查看、检查助记键等。

## <a name="pop-up-menus"></a>弹出菜单

[弹出菜单](../mfc/menus-mfc.md) 显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。

创建菜单资源后，应用程序代码需要加载菜单资源，并使用[TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)来显示菜单。 当用户通过在弹出菜单中进行选择来将其关闭，或选择了命令后，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。

> [!NOTE]
> 对于 Microsoft 基础类（MFC）库程序和 ATL 程序，使用**代码向导**将菜单命令与代码挂钩。 有关详细信息，请参阅[添加事件](../ide/adding-an-event-visual-cpp.md)和将[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

- 若要创建弹出菜单，请创建标题为空的菜单，并且不要提供*标题*。 然后，将菜单命令添加到 "新建" 菜单中，移动到空白菜单标题下的第一个菜单命令 *，并键入* *标题*和任何其他信息。

   对弹出菜单中的任何其他菜单命令重复此过程，并确保保存菜单资源。

- 例如，若要将弹出菜单连接到应用程序，请为 WM_CONTEXTMENU 添加消息处理程序，然后将以下代码添加到消息处理程序：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > 消息处理程序传递的[CPoint](../atl-mfc-shared/reference/cpoint-class.md)是屏幕坐标。

正常情况下，当你在**菜单编辑器**中工作时，菜单资源将显示为菜单栏。 但是，你可能拥有在程序运行时添加到应用程序菜单栏的菜单资源。

- 若要以弹出菜单方式查看菜单资源，请右键单击菜单，然后选择 "**以弹出方式查看**"。

   此选项只是查看首选项，不会修改菜单。

> [!TIP]
> 若要更改回菜单栏视图，请再次选择 "**查看为弹出**"。 此操作将删除复选标记并返回菜单栏视图。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[菜单命令](../windows/menu-command-properties.md)<br/>
[用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)<br/>
[菜单](../mfc/menus-mfc.md)<br/>
[菜单](/windows/win32/menurc/menus)