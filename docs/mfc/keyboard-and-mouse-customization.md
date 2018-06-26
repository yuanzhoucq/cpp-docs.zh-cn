---
title: 键盘和鼠标自定义 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fda670198dd9bd03a6d944ce4db70542926bf41
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931575"
---
# <a name="keyboard-and-mouse-customization"></a>键盘和鼠标自定义
MFC 允许应用程序用户自定义其处理键盘和鼠标输入的方式。 用户可通过为命令分配键盘快捷键来自定义键盘输入。 用户还可通过选择应在用户双击应用程序特定窗口内时执行的命令来自定义鼠标输入。 本主题介绍如何为您的应用程序自定义输入。  
  
 在**自定义**对话框中，用户可以更改鼠标和键盘的自定义控件。 若要显示此对话框中，用户指向**自定义**上**视图**菜单，然后单击**工具栏和停靠**。 在对话框中，用户将单击**键盘**选项卡或**鼠标**选项卡。  
  
## <a name="keyboard-customization"></a>键盘自定义  
 下图显示**键盘**选项卡**自定义**对话框。  
  
 ![自定义对话框中的键盘选项卡](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab")  
键盘自定义选项卡  
  
 用户将与键盘选项卡交互以为命令分配一个或多个键盘快捷键。 可用命令将列在选项卡的左侧。用户可从菜单中选择任何可用命令。 仅菜单命令与键盘快捷键相关。 用户输入一个新的快捷方式之后,**分配**按钮将变为启用状态。 当用户单击此按钮时，应用程序会将选定命令与该快捷键关联。  
  
 右列的列表框中将列出当前分配的所有键盘快捷键。 用户还可选择单独的快捷键并删除它们，或为应用程序重置所有映射。  
  
 如果你想要支持此自定义应用程序中，则必须创建[CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)对象。 若要创建`CKeyboardManager`对象，请调用该函数[CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager)。 此方法将创建并初始化一个键盘管理器。 如果手动创建键盘管理器，则仍必须调用 `CWinAppEx::InitKeyboardManager` 初始化键盘管理器。  
  
 如果使用向导创建应用程序，则向导将初始化键盘管理器。 在应用程序初始化键盘管理器后，框架就会将**键盘**tab 键移动到**自定义**对话框。  
  
## <a name="mouse-customization"></a>鼠标自定义  
 下图显示**鼠标**选项卡**自定义**对话框。  
  
 ![自定义对话框中的鼠标选项卡](../mfc/media/mfcnextmousetab.png "mfcnextmousetab")  
鼠标自定义选项  
  
 用户将与此选项卡交互，以为鼠标双击操作分配菜单命令。 用户将从窗口左侧选择视图，然后使用右侧的控件将命令与双击操作关联。 之后用户可单击**关闭**，每当用户双击视图中的任意位置，应用程序执行关联的命令。  
  
 默认情况下，当您使用向导创建应用程序时，不会启用鼠标自定义。  
  
#### <a name="to-enable-mouse-customization"></a>启用鼠标自定义  
  
1.  初始化[CMouseManager](../mfc/reference/cmousemanager-class.md)对象通过调用[CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager)。  
  
2.  获取指向鼠标管理器的使用[CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager)。  
  
3.  将视图添加到鼠标管理器中，通过使用[CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview)方法。 针对要添加到鼠标管理器的每个视图执行此操作。  
  
 在应用程序初始化鼠标管理器后，框架就会将**鼠标**tab 键移动到**自定义**对话框。 如果未添加任何视图，则访问此选项将导致未经处理的异常。 创建的视图列表之后**鼠标**选项卡可供用户。  
  
 当您将新视图添加到鼠标管理器后，您将为其提供一个唯一 ID。 如果你想要支持鼠标自定义窗口，你必须处理 WM_LBUTTONDBLCLICK 消息并调用[CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick)函数。 当您调用此函数时，其中一个参数就是该窗口的 ID。 程序员负责记录 ID 号以及与其关联的对象。  
  
## <a name="security-concerns"></a>安全问题  
 中所述[用户定义的工具](../mfc/user-defined-tools.md)，用户可以将用户定义的工具 ID 与双击事件关联。 当用户双击视图时，应用程序将寻找与关联 ID 匹配的用户工具。 如果应用程序找到匹配的工具，则它将执行该工具。 如果应用程序无法找到匹配的工具，则它将向双击的视图发送带有 ID 的 WM_COMMAND 消息。  
  
 自定义的设置存储在注册表中。 通过编辑注册表，攻击者可将有效的用户工具 ID 替换为任意命令。 当用户双击视图时，视图将处理攻击者植入的命令。 这可能导致意外和潜在的危险行为。  
  
 此外，此类攻击可以绕开用户界面安全措施。 例如，假定应用程序已禁用打印。 也就是说，在其用户界面，**打印**菜单和按钮都不可用。 通常这将防止应用程序打印。 但如果攻击者编辑注册表，则用户现在可通过双击视图、绕过不可用的用户界面元素直接发送打印命令。  
  
 若要防止此类攻击，请向应用程序命令处理程序添加代码，以在命令执行前验证命令是否有效。 请勿依赖用户界面来阻止命令发送到应用程序。  
  
## <a name="see-also"></a>请参阅  
 [MFC 自定义](../mfc/customization-for-mfc.md)   
 [CKeyboardManager 类](../mfc/reference/ckeyboardmanager-class.md)   
 [CMouseManager 类](../mfc/reference/cmousemanager-class.md)   
 [自定义对安全有何影响](../mfc/security-implications-of-customization.md)

