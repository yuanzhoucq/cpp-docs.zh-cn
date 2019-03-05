---
title: 用户定义的工具
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: 785e37c63653dde91176bedd0321fc58ac122c7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269703"
---
# <a name="user-defined-tools"></a>用户定义的工具

MFC 支持用户定义的工具。 用户定义的工具是执行、 用户定义的外部程序的特殊命令。 自定义过程可用于管理用户定义的工具。 但是，不能使用此过程，如果您的应用程序对象不派生自[CWinAppEx 类](../mfc/reference/cwinappex-class.md)。 有关自定义的详细信息，请参阅[MFC 自定义](../mfc/customization-for-mfc.md)。

如果启用用户定义的工具支持，会自动包括自定义对话框**工具**选项卡。如下图所示**工具**页。

![工具选项卡中自定义对话框](../mfc/media/custdialogboxtoolstab.png "自定义对话框中的工具选项卡") <br/>
自定义对话框工具选项卡

## <a name="enabling-user-defined-tools-support"></a>启用用户定义工具支持

若要启用用户定义的应用程序中的工具，请调用[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)。 但是，您必须首先在应用程序以使用作为参数，此调用的资源文件中定义多个常量。

在资源编辑器中创建虚拟命令，使用相应的命令 id。 在以下示例中，我们使用`ID_TOOLS_ENTRY`作为命令 id。 此命令 ID 将标记一个或多个菜单中的某个位置，其中该框架将插入的用户定义的工具。

你必须留出一些连续 Id 来表示用户定义的工具在字符串表中。 留出的字符串数等于，用户可以定义的用户工具的最大数目。 在以下示例中，它们被命名为`ID_USER_TOOL1`通过`ID_USER_TOOL10`。

可以向用户以帮助他们选择的目录和参数将调用外部程序作为工具来提供建议。 若要执行此操作，请在资源编辑器中创建两个弹出菜单。 在下面的示例它们被命名为`IDR_MENU_ARGS`和`IDR_MENU_DIRS`。 对于每个命令在这些菜单中，应用程序字符串表中定义的字符串。 字符串的资源 ID 必须等于命令 id。

此外可以创建从派生的类[CUserTool 类](../mfc/reference/cusertool-class.md)来替换默认实现。 若要执行此操作，将作为 CWinAppEx::EnableUserTools，而不是 RUNTIME_CLASS 中的第四个参数传递派生的类的运行时信息 ([CUserTool 类](../mfc/reference/cusertool-class.md))。

定义的相应常量后，调用[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户定义的工具。

以下方法调用演示了如何使用这些常量：

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

在此示例中，将在包含工具选项卡**自定义**对话框。 该框架会将命令 ID 相匹配的任何命令为`ID_TOOLS_ENTRY`中的每次用户打开该菜单时的当前定义的用户工具集的任何菜单。 命令 Id`ID_USER_TOOL1`通过`ID_USER_TOOL10`仅供用户定义的工具的使用。 该类[CUserTool 类](../mfc/reference/cusertool-class.md)处理对用户工具的调用。 工具选项卡**自定义**对话框中提供了按钮右侧的参数和目录条目字段来访问菜单**IDR_MENU_ARGS**和**IDR_MENU_DIRS**.当用户选择从一个这些菜单命令时，框架将追加到相应的文本框中的字符串具有资源 ID 等于命令 id。

### <a name="including-predefined-tools"></a>包括预定义的工具

如果你想要预定义的应用程序在一些工具，则必须重写[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)的应用程序的主窗口的方法。 在该方法中，必须执行以下步骤。

##### <a name="to-add-new-tools-in-loadframe"></a>若要在 LoadFrame 中添加新的工具

1. 获取一个指向[CUserToolsManager 类](../mfc/reference/cusertoolsmanager-class.md)对象通过调用[CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)。

1. 对于每个你想要创建的工具，调用[CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)。 此方法返回一个指向[CUserTool 类](../mfc/reference/cusertool-class.md)对象并将新创建的用户工具添加到内部集合的工具。 如果提供的派生类的运行时信息[CUserTool 类](../mfc/reference/cusertool-class.md)的第四个参数作为[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)， [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)将实例化并改为返回该类的实例。

1. 为每个工具，通过设置来设置其文本标签`CUserTool::m_strLabel`并将其命令设置通过调用`CUserTool::SetCommand`。 默认实现[CUserTool 类](../mfc/reference/cusertool-class.md)自动从调用中指定的程序中检索可用图标`SetCommand`。

## <a name="see-also"></a>请参阅

[MFC 自定义](../mfc/customization-for-mfc.md)<br/>
[CUserTool 类](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager 类](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx 类](../mfc/reference/cwinappex-class.md)
