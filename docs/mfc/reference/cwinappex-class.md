---
title: "CWinAppEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinAppEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinAppEx class"
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinAppEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CWinAppEx` 处理应用程序状态，保存该状态对注册表，从注册表加载该状态，初始化应用程序管理器，并提供指向相同的应用程序管理器。  
  
## 语法  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinAppEx::CWinAppEx](../Topic/CWinAppEx::CWinAppEx.md)|构造 `CWinAppEx` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinAppEx::CleanState](../Topic/CWinAppEx::CleanState.md)|从Windows注册表移除了有关应用程序的信息。|  
|[CWinAppEx::EnableLoadWindowPlacement](../Topic/CWinAppEx::EnableLoadWindowPlacement.md)|指定应用程序是否从注册表将加载主框架窗口的初始大小和位置。|  
|[CWinAppEx::EnableTearOffMenus](../Topic/CWinAppEx::EnableTearOffMenus.md)|启用拖曳应用程序菜单。|  
|[CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)|在应用程序允许用户创建自定义菜单命令。|  
|[CWinAppEx::ExitInstance](../Topic/CWinAppEx::ExitInstance.md)|调用由框架从 `Run` 成员函数的内部退出应用程序的此实例。  （重写 [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)。）|  
|[CWinAppEx::GetBinary](../Topic/CWinAppEx::GetBinary.md)|读取与指定的注册表值的二进制数据。|  
|[CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md)|返回指向全局 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) 对象。|  
|[CWinAppEx::GetDataVersion](../Topic/CWinAppEx::GetDataVersion.md)||  
|[CWinAppEx::GetDataVersionMajor](../Topic/CWinAppEx::GetDataVersionMajor.md)|返回在Windows注册表保存的应用程序的主版本号。|  
|[CWinAppEx::GetDataVersionMinor](../Topic/CWinAppEx::GetDataVersionMinor.md)|返回在Windows注册表保存的应用程序的次版本。|  
|[CWinAppEx::GetInt](../Topic/CWinAppEx::GetInt.md)|读取与从注册表中指定的数字数据。|  
|[CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md)|返回指向全局 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) 对象。|  
|[CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)|返回指向全局 [CMouseManager](../../mfc/reference/cmousemanager-class.md) 对象。|  
|[CWinAppEx::GetObject](../Topic/CWinAppEx::GetObject.md)|读取 `CObject`\-与从注册表中指定的派生数据。|  
|[CWinAppEx::GetRegSectionPath](../Topic/CWinAppEx::GetRegSectionPath.md)|返回一个注册表项路径的字符串。  此路径连接的应用程序路径的所提供的相对路径。|  
|[CWinAppEx::GetRegistryBase](../Topic/CWinAppEx::GetRegistryBase.md)|返回应用程序的注册表路径。|  
|[CWinAppEx::GetSectionBinary](../Topic/CWinAppEx::GetSectionBinary.md)|读取与指定的键和值从注册表中的二进制数据。|  
|[CWinAppEx::GetSectionInt](../Topic/CWinAppEx::GetSectionInt.md)|将从注册表中读取数值数据与该指定的键和值。|  
|[CWinAppEx::GetSectionObject](../Topic/CWinAppEx::GetSectionObject.md)|读取与指定的键和值从注册表中 `CObject` 数据。|  
|[CWinAppEx::GetSectionString](../Topic/CWinAppEx::GetSectionString.md)|读取与指定的键和值从注册表中的字符串数据。|  
|[CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md)|返回指向全局 [CShellManager](../../mfc/reference/cshellmanager-class.md) 对象。|  
|[CWinAppEx::GetString](../Topic/CWinAppEx::GetString.md)|读取与从注册表中指定的字符串数据。|  
|[CWinAppEx::GetTooltipManager](../Topic/CWinAppEx::GetTooltipManager.md)|返回指向全局 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) 对象。|  
|[CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md)|返回指向全局 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) 对象。|  
|[CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)|初始化 `CContextMenuManager` 对象。|  
|[CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)|初始化 `CKeyboardManager` 对象。|  
|[CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md)|初始化 `CMouseManager` 对象。|  
|[CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md)|初始化 `CShellManager` 选件类|  
|[CWinAppEx::InitTooltipManager](../Topic/CWinAppEx::InitTooltipManager.md)|初始化 `CTooltipManager` 类。|  
|[CWinAppEx::IsResourceSmartUpdate](../Topic/CWinAppEx::IsResourceSmartUpdate.md)||  
|[CWinAppEx::IsStateExists](../Topic/CWinAppEx::IsStateExists.md)|指示指定的键是否在注册表中。|  
|[CWinAppEx::LoadState](../Topic/CWinAppEx::LoadState.md)|从注册表中加载应用程序状态。|  
|[CWinAppEx::OnAppContextHelp](../Topic/CWinAppEx::OnAppContextHelp.md)|调用由结构，当 **自定义项** 对话框的用户请求上下文的帮助。|  
|[CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md)|当用户在应用程序的任意位置时，双击调用用户定义的命令。|  
|[CWinAppEx::OnWorkspaceIdle](../Topic/CWinAppEx::OnWorkspaceIdle.md)||  
|[CWinAppEx::SaveState](../Topic/CWinAppEx::SaveState.md)|编写应用程序框架的状态对于Windows注册表中。|  
|[CWinAppEx::SetRegistryBase](../Topic/CWinAppEx::SetRegistryBase.md)|设置默认注册表项的路径。  此密钥将用作所有后续注册表调用的支持。|  
|[CWinAppEx::ShowPopupMenu](../Topic/CWinAppEx::ShowPopupMenu.md)|显示弹出菜单。|  
|[CWinAppEx::WriteBinary](../Topic/CWinAppEx::WriteBinary.md)|到指定的注册表的二进制数据值的写访问权。|  
|[CWinAppEx::WriteInt](../Topic/CWinAppEx::WriteInt.md)|到指定的注册表的数值数据值的写访问权。|  
|[CWinAppEx::WriteObject](../Topic/CWinAppEx::WriteObject.md)|从派生 [CObject Class](../../mfc/reference/cobject-class.md) 到指定的注册表值的写入数据。|  
|[CWinAppEx::WriteSectionBinary](../Topic/CWinAppEx::WriteSectionBinary.md)|写入指定的注册表项的值的二进制数据。|  
|[CWinAppEx::WriteSectionInt](../Topic/CWinAppEx::WriteSectionInt.md)|写入指定的注册表项的值的数字数据。|  
|[CWinAppEx::WriteSectionObject](../Topic/CWinAppEx::WriteSectionObject.md)|写入数据从 `CObject` 选件类派生到指定的注册表项的值。|  
|[CWinAppEx::WriteSectionString](../Topic/CWinAppEx::WriteSectionString.md)|写入指定的注册表项的值的字符串数据。|  
|[CWinAppEx::WriteString](../Topic/CWinAppEx::WriteString.md)|到指定的注册表的字符串数据值编写。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CWinAppEx::LoadCustomState](../Topic/CWinAppEx::LoadCustomState.md)|调用由结构，当应用程序状态加载的。|  
|[CWinAppEx::LoadWindowPlacement](../Topic/CWinAppEx::LoadWindowPlacement.md)|调用由结构，当从注册表加载应用程序的大小和位置。  已填充的数据时包括主框架的大小和位置已关闭的应用程序上次。|  
|[CWinAppEx::OnClosingMainFrame](../Topic/CWinAppEx::OnClosingMainFrame.md)|调用由结构，当主框架窗口操作 `WM_CLOSE`。|  
|[CWinAppEx::PreLoadState](../Topic/CWinAppEx::PreLoadState.md)|调用由应用程序状态之前的framework加载。|  
|[CWinAppEx::PreSaveState](../Topic/CWinAppEx::PreSaveState.md)|调用由应用程序状态之前的framework保存。|  
|[CWinAppEx::ReloadWindowPlacement](../Topic/CWinAppEx::ReloadWindowPlacement.md)|重新加载所提供的窗口的大小和位置从注册表中|  
|[CWinAppEx::SaveCustomState](../Topic/CWinAppEx::SaveCustomState.md)|调用由框架，它将写入应用程序状态写入注册表之后。|  
|[CWinAppEx::StoreWindowPlacement](../Topic/CWinAppEx::StoreWindowPlacement.md)|调用由框架编写主框架的大小和位置写入注册表。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWinAppEx::m\_bForceImageReset](../Topic/CWinAppEx::m_bForceImageReset.md)|指定框架是否将重置所有工具栏图像，即包含工具栏的框架窗口加载。|  
  
## 备注  
 MFC框架提供的许多功能取决于 `CWinAppEx` 选件类。  可以通过两种方式之一来合并 `CWinAppEx` 选件类到应用程序中:  
  
-   构造在主线程中 `CWinAppEx` 选件类。  
  
-   从派生 `CWinAppEx`主应用程序选件类。  
  
 在其中合并 `CWinAppEx` 到应用程序中后，可以初始化任何一个应用程序管理器。  在使用应用程序管理器之前，必须通过调用适当初始化它初始化方法。  若要获取指向特定管理器，请调用关联的获取方法。  `CWinAppEx` 选件类管理以下应用程序管理器: [CMouseManager Class](../../mfc/reference/cmousemanager-class.md)、 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)、 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)、 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)和 [CMenuTearOffManager Class](../../mfc/reference/cmenutearoffmanager-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## 要求  
 **标头:** afxwinappex.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager Class](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)