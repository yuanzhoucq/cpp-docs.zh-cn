---
title: "如何： 添加重新启动管理器支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a413f28909a52e3bc82e9d8f2694d559bf8a885c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-restart-manager-support"></a>如何：添加重新启动管理器支持
重新启动管理器是添加到用于 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]的一项功能。 如果发生意外关闭或重启，重新启动管理器将为你的应用程序添加支持。 重新启动管理器的行为取决于应用程序的类型。 如果你的应用程序是文档编辑器，则重新启动管理器让应用程序能够自动保存任何打开文档的状态和内容，并在意外关闭后重启应用程序。 如果你的应用程序不是文档编辑器，则重新启动管理器将重启该应用程序，但无法默认保存应用程序的状态。  
  
 重启后，如果应用程序采用 Unicode 编码，则该应用程序将显示任务对话框。 如果是 ANSI 应用程序，则该应用程序将显示 Windows 消息框。 此时，用户可以选择是否要还原自动保存的文档。 如果用户不还原自动保存的文档，则重新启动管理器将放弃临时文件。  
  
> [!NOTE]
>  可以重写重新启动管理器保存数据和重启应用程序的默认行为。  
  
 默认情况下，当通过 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的项目向导创建的 MFC 应用程序在具有 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]的计算机上运行时，这些应用程序支持重新启动管理器。 如果不希望你的应用程序支持重新启动管理器，可以在新项目向导中禁用重新启动管理器。  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>向现有应用程序添加重新启动管理器支持  
  
1.  打开 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]中的现有 MFC 应用程序。  
  
2.  打开主应用程序的源文件。 默认情况下，这是与你的应用程序具有相同名称的 .cpp 文件。 例如，MyProject 的主应用程序源文件为 MyProject.cpp。  
  
3.  找到主应用程序的构造函数。 例如，如果你的项目是 MyProject，则构造函数为 `CMyProjectApp::CMyProjectApp()`。  
  
4.  将以下代码行添加到你的构造函数。  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  请确保应用程序的 `InitInstance` 方法将调用其父 `InitInstance` 方法： [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) 或 `CWinAppEx::InitInstance`的一项功能。 `InitInstance` 方法负责检查 `m_dwRestartManagerSupportFlags` 参数。  
  
6.  编译并运行应用程序。  
  
## <a name="see-also"></a>请参阅  
 [CDataRecoveryHandler 类](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [CWinApp 类](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

