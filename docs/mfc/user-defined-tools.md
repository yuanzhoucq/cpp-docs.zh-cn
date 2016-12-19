---
title: "用户定义的工具 | Microsoft Docs"
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
  - "用户定义的工具（MFC 扩展）"
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用户定义的工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支持用户定义的工具。  用户定义的工具为执行外部的特定命令，用户指定的程序。  可以使用自定义过程取决管理用户定义的工具。  但是，在中，如果应用程序将从 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)对象，未派生您无法使用此过程。  有关自定义项的更多信息，请参见 [MFC 自定义](../mfc/customization-for-mfc.md)。  
  
 如果启用用户定义的工具，支持自定义对话框自动包含 **工具** 选项卡。  下图显示 **工具** 页。  
  
 ![“自定义”对话框中的“工具”选项卡](../mfc/media/custdialogboxtoolstab.png "CustDialogBoxToolsTab")  
自定义对话框工具"选项卡  
  
## 启用用户定义的工具支持  
 在应用程序中启用用户定义的工具，调用 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)。  但是，必须首先定义在应用程序的资源文件中多常数用作参数。此调用。  
  
 在资源编辑器中创建使用适当的命令 ID. 的假的命令  在下面的示例中，我们使用 **ID\_TOOLS\_ENTRY** 作为命令 ID.  此命令 ID。指示框架将插入用户定义的工具一个或多个菜单中的位置。  
  
 在字符串表必须预留一些后续 ID 表示用户定义的工具。  可以留出的字符串的数量与的用户工具的最大数字等于的用户可定义。  在下面的示例中，**ID\_USER\_TOOL1** 通过这些名为 **ID\_USER\_TOOL10**。  
  
 可以为用户提供帮助。建议选择目录和参数将被作为工具的程序外部的。  为此，请创建一个资源编辑器的两个弹出菜单。  在下面这些示例中名为 **IDR\_MENU\_ARGS** 和 **IDR\_MENU\_DIRS**。  对于这些菜单中的所有命令，请定义一字符串应用程序在字符串表中。  字符串资源的 ID 必须相等与 . 命令 ID  
  
 也可以从 [CUserTool Class](../mfc/reference/cusertool-class.md) 创建的派生类替换默认实现。  为此，请传递派生类的运行时信息作为第四个参数。CWinAppEx::EnableUserTools，而不是 RUNTIME\_CLASS \([CUserTool Class](../mfc/reference/cusertool-class.md)\)。  
  
 在定义了相应的常数后，请调用 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) 启用用户定义的工具。  
  
 下面的方法调用添加演示如何使用这些常数：  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/CPP/user-defined-tools_1.cpp)]  
  
 在此示例中，"工具选项卡将是包含在 **自定义** 对话框。  框架将替换任何命令与任意菜单的命令 ID **ID\_TOOLS\_ENTRY** 的集当前定义的用户工具，每当用户打开该菜单。  命令 ID **ID\_USER\_TOOL1** 通过 **ID\_USER\_TOOL10** 保留为用户定义的工具使用。  类处理 [CUserTool Class](../mfc/reference/cusertool-class.md) 调用用户工具。  **自定义** 对话框工具的选项卡在参数和目录输入字段右侧的按钮访问菜单 **IDR\_MENU\_ARGS** 和 **IDR\_MENU\_DIRS**。，当用户选择这些菜单之一中的命令，框架将筛选器追加到相应的文本框有资源 ID 等于 . 命令 ID 的字符串  
  
### 包括预定义的工具  
 如果预定义要在应用程序启动的某些工具，必须重写应用程序主窗口有关的方法。[CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 在该方法，您必须执行下列步骤。  
  
##### 添加新工具。LoadFrame  
  
1.  获取一个指向对象通过调用 [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md)[CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md)。  
  
2.  对于要创建的每个工具，调用 [CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md)。  此方法返回指向 [CUserTool Class](../mfc/reference/cusertool-class.md) 对象并将新创建用户工具。工具的内部集合。  如果针对 [CUserTool Class](../mfc/reference/cusertool-class.md) 派生类提供的运行时信息为 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)[CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md) 第四个参数，将实例化并返回该类的实例。  
  
3.  对于每工具，通过设置 `CUserTool::m_strLabel` 来设置其文本标签并通过调用 `CUserTool::SetCommand`将其命令。  [CUserTool Class](../mfc/reference/cusertool-class.md) 的默认实现。在对 `SetCommand`的调用中指定程序自动检索可用图标。  
  
## 请参阅  
 [MFC 自定义](../mfc/customization-for-mfc.md)   
 [CUserTool Class](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)