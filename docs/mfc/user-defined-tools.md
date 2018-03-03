---
title: "用户定义的工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0751a2cb3f78730ec948d737dc99b85c2e735
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-tools"></a>用户定义的工具
MFC 支持用户定义的工具。 用户定义的工具是执行程序外部的用户指定的特殊命令。 可以使用的自定义过程来管理用户定义的工具。 但是，不能使用此过程，如果你的应用程序对象不派生自[CWinAppEx 类](../mfc/reference/cwinappex-class.md)。 有关自定义的详细信息，请参阅[MFC 自定义](../mfc/customization-for-mfc.md)。  
  
 如果启用用户定义的工具支持时，会自动包括的自定义对话框**工具**选项卡。下图显示**工具**页。  
  
 ![工具选项卡中自定义对话框中](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab")  
自定义对话框的工具栏  
  
## <a name="enabling-user-defined-tools-support"></a>启用用户定义的工具支持  
 若要启用应用程序中的用户定义的工具，请调用[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)。 但是，你必须首先在你的应用程序，用于进行此调用作为参数的资源文件中定义多个常量。  
  
 在资源编辑器中创建 dummy 命令，使用相应的命令 id。 在以下示例中，我们使用**ID_TOOLS_ENTRY**作为命令 id。 此命令 ID 将标记一个或多个菜单中的某个位置，框架将插入的用户定义的工具的位置。  
  
 你必须留出一些连续的 Id 字符串表中的表示用户定义的工具。 留出的字符串的数量等于最大的用户可以定义的用户工具数。 在下面的示例中，这些名为**ID_USER_TOOL1**通过**ID_USER_TOOL10**。  
  
 你可以提供给用户以帮助他们选择作为工具的目录和自变量将调用外部程序的建议。 若要执行此操作，请在资源编辑器中创建以下两个弹出菜单。 在下面的示例命名这些**IDR_MENU_ARGS**和**IDR_MENU_DIRS**。 对于每个命令使用这些菜单中，你的应用程序字符串表中定义的字符串。 字符串的资源 ID 必须等于命令 id。  
  
 你还可以创建从派生的类[CUserTool 类](../mfc/reference/cusertool-class.md)替换默认实现。 若要执行此操作，将在派生类的运行时信息传递作为 CWinAppEx::EnableUserTools，而不是 RUNTIME_CLASS 中的第四个参数 ([CUserTool 类](../mfc/reference/cusertool-class.md))。  
  
 你定义的相应常量后，调用[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户定义的工具。  
  
 下面的方法调用演示如何使用这些常量：  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]  
  
 在此示例中，工具选项卡将包括在**自定义**对话框。 框架将替换与的命令 ID 匹配任何命令**ID_TOOLS_ENTRY**在任何菜单中提供的当前定义的用户工具每当用户打开该菜单集。 命令 Id **ID_USER_TOOL1**通过**ID_USER_TOOL10**仅供用户定义的工具的使用。 类[CUserTool 类](../mfc/reference/cusertool-class.md)处理调用到用户工具。 工具选项卡的**自定义**对话框中提供的按钮右侧的自变量和目录输入字段来访问菜单**IDR_MENU_ARGS**和**IDR_MENU_DIRS**.当用户从一个使用这些菜单中选择命令时，该框架追加到相应的文本框中的字符串具有资源 ID 等于命令 id。  
  
### <a name="including-predefined-tools"></a>包括预定义的工具  
 如果你想要在应用程序启动一些工具来预定义表单，则必须重写[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)你的应用程序的主窗口的方法。 在该方法中，你必须执行以下步骤。  
  
##### <a name="to-add-new-tools-in-loadframe"></a>若要添加新的工具在 LoadFrame  
  
1.  获取指向的[CUserToolsManager 类](../mfc/reference/cusertoolsmanager-class.md)对象通过调用[CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)。  
  
2.  对于你想要创建每个工具，调用[CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)。 此方法返回一个指向[CUserTool 类](../mfc/reference/cusertool-class.md)对象并将新创建的用户工具添加到内部集合的工具。 如果你提供的派生类的运行时信息[CUserTool 类](../mfc/reference/cusertool-class.md)作为第四个参数的[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)， [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)将实例化并改为返回该类的实例。  
  
3.  为每个工具，通过设置来设置其文本标签`CUserTool::m_strLabel`并设置其命令通过调用`CUserTool::SetCommand`。 默认实现[CUserTool 类](../mfc/reference/cusertool-class.md)从调用中指定的程序将自动检索可用图标`SetCommand`。  
  
## <a name="see-also"></a>请参阅  
 [MFC 自定义](../mfc/customization-for-mfc.md)   
 [CUserTool 类](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager 类](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx 类](../mfc/reference/cwinappex-class.md)




