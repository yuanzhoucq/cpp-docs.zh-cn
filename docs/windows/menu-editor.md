---
title: 菜单编辑器 （c + +）
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
ms.openlocfilehash: b5d809fa4e0f608d4c0e6cbdaf8697688c6d3f9c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037271"
---
# <a name="menu-editor-c"></a>菜单编辑器 （c + +）

使用菜单，可以按照逻辑方式和易于查找的方式排列命令。 与**菜单编辑器**，可以创建和编辑菜单的密切合作，直接与菜单栏类似于一个完成的应用程序中。

> [!TIP]
> 使用时**菜单编辑器**，在许多情况下，你可以右击以显示常用命令的弹出菜单。 可用命令取决于指针所指向的内容。

## <a name="how-to"></a>操作说明

**菜单编辑器**，可以：

### <a name="to-create-a-standard-menu"></a>创建标准菜单

1. 转到菜单**视图** > **资源视图**，然后右键单击**菜单**标题。 选择**将资源添加**，然后**菜单**。

1. 选择**新项**框 (包含的矩形*在此处键入*) 在菜单栏上。

   ![菜单编辑器中的新项框](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **新项**框

1. 例如，键入新菜单的名称*文件*。

   键入的文本将同时出现在**菜单编辑器**并在**标题**框中[属性窗口](/visualstudio/ide/reference/properties-window)。 你可以在任一位置编辑新菜单的属性。

   为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。

   ![展开新项框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **新项**框的焦点移动后键入菜单名称

   > [!NOTE]
   > 若要在菜单栏上创建单项菜单，请设置**Popup**属性设置为**False**。

### <a name="to-create-a-submenu"></a>创建子菜单

1. 选择你想要创建子菜单的菜单命令。

1. 在出现在右侧的 **新项** 框显中键入新的菜单命令的名称。 此新命令将在子菜单的菜单中显示为第一个。

1. 将其他菜单命令添加到子菜单的菜单中。

### <a name="to-insert-a-new-menu-between-existing-menus"></a>在现有菜单之间插入新菜单

选择现有的菜单名称并按**插入**键，或者右键单击菜单栏上，选择**插入新**。

   **新项**框插入到所选的项之前。

### <a name="to-add-commands-to-a-menu"></a>将命令添加到菜单

1. 创建菜单。 然后选择菜单名，例如**文件**。

   每个菜单都将展开，并显示一个新项框让你输入命令。 例如，可以将命令添加**新建**，**打开**，并**关闭**到**文件**菜单。

1. 在新项框中，键入新菜单命令的名称。

   > [!NOTE]
   > 键入的文本将同时出现在**菜单编辑器**并在**标题**框中[属性窗口](/visualstudio/ide/reference/properties-window)。 你可以在任一位置编辑新菜单的属性。

   > [!TIP]
   > 你可以定义一个允许用户选择菜单命令的助记键（热键）。 输入与号 (`&`) 若要指定为助记键的某个字母前。 用户可以通过键入该字母来选择菜单命令。

1. 在中**属性**窗口中，选择菜单命令适用的属性。 有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。

1. 在中**提示符**框中**属性**窗口中，键入你想要在应用程序的状态栏中显示的提示字符串。

   此步骤中创建具有菜单命令创建与相同的资源标识符的字符串表中的项。

   > [!NOTE]
   > 提示只能应用于菜单项**Popup**的属性**True**。 例如，包含子菜单项的顶级菜单项可以有提示。 目的**提示**用于指示会发生什么情况是如果用户选择菜单项。

1. 按**Enter**完成菜单命令。

   将选定新项框，让你可以创建其他菜单命令。

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>若要选择多个菜单命令，运行大容量操作，如删除或更改属性

在按下**Ctrl**密钥，请选择菜单或所需的子菜单命令。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>若要移动和复制菜单和菜单命令

- 使用拖放方法：

   1. 拖动或复制要移到下列位置的项：

      - 当前菜单上的新位置。

      - 不同的菜单。 可以通过将鼠标指针拖过这些导航到其他菜单。

   1. 当插入参考线显示所需位置时放下菜单命令。

- 使用快捷菜单命令：

   1. 右键单击一个或多个菜单或菜单命令，然后选择**剪切**（若要移动） 或**副本**。

   1. 如果要将项移动到另一个菜单资源或资源脚本文件，[在另一个窗口中打开它](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

   1. 选择要将菜单或菜单命令移动或复制到的位置。

   1. 从快捷菜单中选择 **“粘贴”**。 被移动或复制的项放在选定项的前面。

> [!NOTE]
> 还可以拖动、复制和粘贴到其他菜单窗口中的其他菜单中。

### <a name="to-delete-a-menu-or-menu-command"></a>若要删除菜单或菜单命令

右键单击菜单名称或命令，然后选择**删除**。

> [!NOTE]
> 同样，可以使用快捷菜单来执行其他操作，例如，复制、剪切、粘贴、插入新项、插入分隔符、编辑 ID、以弹出方式查看、检查助记键等。

## <a name="pop-up-menus"></a>弹出菜单

[弹出菜单](../mfc/menus-mfc.md) 显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。

创建菜单资源后，应用程序代码需要加载该菜单资源并使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)才会显示该菜单。 一旦用户通过选择之外，解除了弹出菜单，或选择一个命令，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。

> [!NOTE]
> Microsoft 基础类 (MFC) 库程序和 ATL 程序，请使用**代码向导**将菜单命令与代码挂接。 有关详细信息，请参阅[添加事件](../ide/adding-an-event-visual-cpp.md)并[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

- 若要创建弹出菜单，创建一个菜单标题为空，但不提供*标题*。 然后，将菜单命令添加到的新菜单中，将转到空白菜单标题临时标题下方的第一个菜单命令*请在此处输入*并键入*标题*和任何其他信息。

   对于弹出菜单中的任何其他菜单命令重复此过程，请务必保存菜单资源。

- 若要将弹出菜单连接到你的应用程序，例如，为 WM_CONTEXTMENU，添加消息处理程序，然后将以下代码添加到消息处理程序：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)传递的消息处理程序是屏幕坐标。

通常情况下，当您在中工作**菜单编辑器**，菜单资源显示为菜单栏。 但是，你可能拥有在程序运行时添加到应用程序菜单栏的菜单资源。

- 若要查看以弹出菜单的菜单资源，请右键单击该菜单，然后选择**以弹出方式查看**。

   此选项只是查看首选项，并且不会修改你的菜单。

> [!TIP]
> 若要更改回菜单栏视图，请选择**以弹出方式查看**试。 此操作将删除复选标记，并返回菜单栏视图。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[菜单命令](../windows/menu-command-properties.md)<br/>

<!--
[User-Interface Objects and Command IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](https://msdn.microsoft.com/library/windows/desktop/ms646977.aspx)-->