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
ms.openlocfilehash: 8e97fb88a8860ab0831f62bf2413b1f8f7174c7b
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336678"
---
# <a name="menu-editor-c"></a>菜单编辑器 （c + +）

使用菜单，可以按照逻辑方式和易于查找的方式排列命令。 与**菜单**编辑器中，您可以创建和编辑通过直接使用与完成的应用程序中的一个相似的菜单栏的菜单。

> [!TIP]
> 使用时**菜单**编辑器中的，在许多情况下，您可以单击鼠标右键按钮以显示常用命令的快捷菜单。 可用命令取决于指针所指向的内容。

> [!NOTE]
> 对于 Microsoft 基础类库 (MFC) 程序和 ATL 程序，你可以使用**代码向导**将菜单命令与代码挂接。 有关更多信息，请参阅 [添加事件](../ide/adding-an-event-visual-cpp.md)。

## <a name="how-to"></a>操作说明

> [!NOTE]
> **资源窗口**在 Express 版本中不可用。

**菜单**编辑器，可以：

### <a name="to-create-a-standard-menu"></a>创建标准菜单

1. 从**视图**菜单中，选择**资源视图**，然后右键单击**菜单**标题并选择**添加资源**。 选择 **“菜单”**。

1. 选择菜单栏上的“新建项目”  框（包含“请在此处输入”的矩形）。

   ![菜单编辑器中的新项框](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   新建项目框

1. 键入新菜单的名称，例如“文件”。

   键入的文本将同时出现在 **菜单** 编辑器 以及 **属性窗口** 中的 [“标题”](/visualstudio/ide/reference/properties-window)框中。 你可以在任一位置编辑新菜单的属性。

   为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。

   ![展开新项框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   新项目框的焦点在键入菜单名称后转移

   > [!NOTE]
   > 若要在菜单栏上创建单项菜单，请设置**Popup**属性设置为**False**。

### <a name="to-create-a-submenu"></a>创建子菜单

1. 选择你想要创建子菜单的菜单命令。

1. 在出现在右侧的 **新项** 框显中键入新的菜单命令的名称。 此新命令将在子菜单的菜单中显示为第一个。

1. 将其他菜单命令添加到子菜单的菜单中。

## <a name="to-insert-a-new-menu-between-existing-menus"></a>在现有菜单之间插入新菜单

选择现有的菜单名称并按**插入**键或右键单击菜单栏上，选择**插入新**从快捷菜单。

**新项**框插入到所选的项之前。

### <a name="to-add-commands-to-a-menu"></a>将命令添加到菜单

1. 创建菜单。

1. 选择菜单名，例如**文件**。

   每个菜单都将展开，并显示一个新项框让你输入命令。 例如，可以将命令添加**新建**，**打开**，并**关闭**到**文件**菜单。

1. 在新项框中，键入新菜单命令的名称。

   > [!NOTE]
   > 键入的文本将同时出现在 **菜单** 编辑器 以及 **属性窗口** 中的 [“标题”](/visualstudio/ide/reference/properties-window)框中。 你可以在任一位置编辑新菜单的属性。

   > [!TIP]
   > 你可以定义一个允许用户选择菜单命令的助记键（热键）。 输入与号 (`&`) 若要指定为助记键的某个字母前。 用户可以通过键入该字母来选择菜单命令。

1. 在中**属性**窗口中，选择菜单命令适用的属性。 有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。

1. 在中**提示符**框中**属性**窗口中，键入你想要在应用程序的状态栏中显示的提示字符串。

   此步骤中创建具有菜单命令创建与相同的资源标识符的字符串表中的项。

   > [!NOTE]
   > 提示只能应用于菜单项**Popup**的属性**True**。 例如，包含子菜单项的顶级菜单项可以有提示。 目的**提示**用于指示会发生什么情况是如果用户选择菜单项。

1. 按**Enter**完成菜单命令。

   将选定新项框，让你可以创建其他菜单命令。

### <a name="to-select-multiple-menu-commands"></a>选择多个菜单命令

可以选择多个菜单名称或要运行大容量操作，如删除或更改属性的菜单命令。

在按下**Ctrl**密钥，请选择菜单或所需的子菜单命令。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>若要移动和复制菜单和菜单命令

> [!NOTE]
> 还可以拖动、复制和粘贴到其他菜单窗口中的其他菜单中。

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移动或复制菜单或菜单命令

1. 拖动或复制要移到下列位置的项：

   - 当前菜单上的新位置。

   - 不同的菜单。 （可以通过在其他菜单上拖动鼠标指针来导航到这些菜单。）

1. 当插入参考线显示所需位置时放下菜单命令。

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用快捷菜单命令移动或复制菜单或菜单命令

1. 右键单击一个或多个菜单或菜单命令。

1. 从快捷菜单中选择 **“剪切”** （移动）或 **“复制”**。

1. 如果要将项移动到另一个菜单资源或资源脚本文件，[在另一个窗口中打开它](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

1. 选择要将菜单或菜单命令移动或复制到的位置。

1. 从快捷菜单中选择 **“粘贴”**。 被移动或复制的项放在选定项的前面。

### <a name="to-delete-a-menu-or-menu-command"></a>若要删除菜单或菜单命令

右键单击菜单名称或命令，然后选择**删除**从快捷菜单。

> [!NOTE]
> 同样，可以使用快捷菜单来执行其他操作，例如，复制、剪切、粘贴、插入新项、插入分隔符、编辑 ID、以弹出方式查看、检查助记键等。

## <a name="pop-up-menus"></a>弹出菜单

[弹出菜单](../mfc/menus-mfc.md) 显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。

创建菜单资源后，应用程序代码需要加载该菜单资源并使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)才会显示该菜单。 一旦用户通过选择之外，解除了弹出菜单，或选择一个命令，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。

### <a name="to-create-a-pop-up-menu"></a>创建弹出菜单

1. 创建菜单使用空标题 (不提供**标题**)。

1. [将菜单命令添加到新菜单](../windows/adding-commands-to-a-menu.md)。 将移动到空白菜单标题下的第一个菜单命令 (临时标题显示`Type Here`)。 键入 **标题** 和任何其他信息。

   对弹出菜单中的任何其他菜单命令重复此过程。

1. 保存菜单资源。

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>将弹出菜单连接到应用程序

1. （例如） 添加 WM_CONTEXTMENU 消息处理程序。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

1. 将以下代码添加到消息处理程序：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)传递的消息处理程序是屏幕坐标。

> [!NOTE]
> 弹出菜单连接到你的应用程序需要 MFC。

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>以弹出菜单方式查看菜单资源

通常情况下，当您在中工作**菜单**编辑器中，菜单资源显示为菜单栏。 但是，你可能拥有在程序运行时添加到应用程序菜单栏的菜单资源。

右键单击该菜单，然后选择**以弹出方式查看**从快捷菜单。

   此选项只是查看首选项，并且不会修改你的菜单。

> [!NOTE]
> 若要更改回菜单栏视图，请选择**以弹出方式查看**再次 （它将删除复选标记，并返回菜单栏视图）。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[菜单命令](../windows/menu-command-properties.md)<br/>

<!--
[User-Interface Objects and Command IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](https://msdn.microsoft.com/library/windows/desktop/ms646977.aspx)-->