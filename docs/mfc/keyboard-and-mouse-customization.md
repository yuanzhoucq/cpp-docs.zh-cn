---
title: "键盘和鼠标自定义 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义, 键盘和鼠标（MFC 扩展）"
  - "键盘和鼠标自定义（MFC 扩展）"
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 键盘和鼠标自定义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 允许应用程序的用户自定义如何处理键盘和鼠标输入。  用户可以通过分配键盘快捷方式自定义键盘输入来命令。  当用户双击应用程序内的特定窗口时，用户也可以通过选择应执行的命令自定义鼠标输入。  本主题解释如何为应用程序自定义输入。  
  
 在 **自定义** 对话框中，用户可以更改鼠标和键盘的自定义控件。  若要显示此对话框，用户在 **视图** 菜单中指向 **自定义** ，然后单击 **工具栏和停靠**。  在对话框中，用户单击 **键盘** 选项或 **鼠标** 选项。  
  
## 键盘自定义  
 下图显示 **自定义** 对话框的 **键盘** 选项 。  
  
 ![“自定义”对话框中的“键盘”选项卡](../mfc/media/mfcnextkeyboardtab.png "MFCNextKeyboardTab")  
键盘自定义选项  
  
 用户与键盘选项交互将一个或多个键盘快捷方式分配给一个命令。  可用命令列在选项的左侧。  用户可以选择从菜单中的任意可用命令。  仅菜单命令与键盘快捷键相关。  在用户输入新的快捷方式 后，**分配** 按钮将变为启用状态。  当用户单击此按钮，应用程序将选定命令与快捷方式关联。  
  
 所有当前分配的键盘快捷方式列在列表框中左边列中。  用户也可选择单个快捷键并移除或重置应用程序的所有映射。  
  
 如果要在应用程序中支持此自定义项，必须创建一个 [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) 对象。  创建一个 `CKeyboardManager` 对象，调用函数 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md) 。  此方法创建并初始化一个键盘管理器。  如果手动创建一个键盘管理器，仍然必须调用 `CWinAppEx::InitKeyboardManager` 初始化它。  
  
 如果使用向导创建应用程序，则该向导将初始化键盘管理器。  在应用程序初始化键盘管理器后，框架将在**自定义** 对话框中添加 **键盘** 选项卡。  
  
## 鼠标自定义  
 下图显示 **自定义** 对话框的 **鼠标** 选项 。  
  
 ![“自定义”对话框中的“鼠标”选项卡](../mfc/media/mfcnextmousetab.png "MFCNextMouseTab")  
鼠标自定义选项  
  
 用户与此选项交互以给双击鼠标操作分配命令。  用户选择从窗口左侧的视图，然后使用右侧的控件与双击操作的命令关联。  在用户单击 **关闭**后，只要用户在视图中的任意位置双击，应用程序执行相关命令。  
  
 默认情况下，当使用向导创建应用程序时，鼠标自定义状态为未启用。  
  
#### 启用鼠标自定义  
  
1.  通过调用 [CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md) 初始化 [CMouseManager](../mfc/reference/cmousemanager-class.md) 对象。  
  
2.  通过使用 [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md) 获取一个指针指向鼠标管理器。  
  
3.  通过使用 [CMouseManager::AddView](../Topic/CMouseManager::AddView.md) 方法，添加视图到鼠标管理器。  为每个想添加到鼠标管理器的试图执行它。  
  
 在应用程序初始化鼠标管理器之后，框架添加 **鼠标** 选项到 **自定义** 对话框。  如果不添加任何视图，访问选项将导致未经处理的异常。  在创建视图列表之后，**鼠标** 选项卡可供用户使用。  
  
 当您将新视图添加到鼠标管理器时，您赋予它唯一 ID.  如果希望支持窗口设置鼠标自定义，您必须处理 `WM_LBUTTONDBLCLICK` 消息和调用 [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) 函数。  当您调用此函数时，其中一参数是该窗口的 ID。  由程序员负责记录 ID 号以及对象与它们关联。  
  
## 安全因素  
 正如 [用户定义的工具](../mfc/user-defined-tools.md) 所述，用户可以将一个用户定义的工具 ID 与双击事件关联。  当用户双击视图时，应用程序查找匹配相关 ID 的用户工具。  如果应用程序找到匹配的工具，则它将执行该工具。  如果应用程序找不到匹配的工具，则它将具有 ID 的 WM\_COMMAND 信息发送给双击后的视图。  
  
 自定义设置存储在注册表中。  通过编辑注册表，攻击者可以使用任意命令替换有效的用户 ID 工具。  当用户双击视图时，视图处理攻击者种植的命令。  这可能导致意外和潜在的危险行为。  
  
 此外，此类攻击可以跳过用户界面安全措施。  例如，假定应用程序已禁用打印。  即在其用户界面，**打印** 菜单和按钮不可用。  通常这防止应用程序打印。  但是，如果攻击者编辑注册表，现在用户可以直接通过双击视图发送打印命令，绕过不可用的用户界面元素。  
  
 若要防止出现这类攻击，请在执行之前，将代码添加到应用程序命令处理程序以验证命令有效。  不要依赖用户界面以阻止命令发送给应用程序。  
  
## 请参阅  
 [MFC 自定义](../mfc/customization-for-mfc.md)   
 [CKeyboardManager Class](../mfc/reference/ckeyboardmanager-class.md)   
 [CMouseManager Class](../mfc/reference/cmousemanager-class.md)   
 [自定义对安全有何影响](../mfc/security-implications-of-customization.md)