---
title: "CUserToolsManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserToolsManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserToolsManager class"
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CUserToolsManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

维护 [CUserTool Class](../../mfc/reference/cusertool-class.md) 对象的集合在应用程序中。  用户工具是运行外部应用程序的菜单项。  `CUserToolsManager` 对象使位用户或开发人员添加新用户工具到应用程序。  它支持命令的执行与用户工具，因此，它还保存有关用户工具的信息在Windows注册表。  
  
## 语法  
  
```  
class CUserToolsManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CUserToolsManager::CUserToolsManager](../Topic/CUserToolsManager::CUserToolsManager.md)|构造 `CUserToolsManager`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md)|创建新的用户工具。|  
|[CUserToolsManager::FindTool](../Topic/CUserToolsManager::FindTool.md)|返回指向与指定的命令ID.的 `CMFCUserTool` 对象|  
|[CUserToolsManager::GetArgumentsMenuID](../Topic/CUserToolsManager::GetArgumentsMenuID.md)|返回与 **自定义** 对话框的 **工具** 选项的 **参数** 菜单的资源ID。|  
|[CUserToolsManager::GetDefExt](../Topic/CUserToolsManager::GetDefExt.md)|返回 **打开的文件** 对话框的默认扩展名\([CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)\)在 **自定义** 对话框的 **工具** 选项的 **命令** 字段。|  
|[CUserToolsManager::GetFilter](../Topic/CUserToolsManager::GetFilter.md)|返回 **打开的文件** 对话框的文件筛选器\([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\)在 **自定义** 对话框的 **工具** 选项的 **命令** 字段。|  
|[CUserToolsManager::GetInitialDirMenuID](../Topic/CUserToolsManager::GetInitialDirMenuID.md)|返回与 **自定义** 对话框的 **工具** 选项的 **初始目录** 菜单的资源ID。|  
|[CUserToolsManager::GetMaxTools](../Topic/CUserToolsManager::GetMaxTools.md)|返回的用户工具的最大数在应用程序中分配。|  
|[CUserToolsManager::GetToolsEntryCmd](../Topic/CUserToolsManager::GetToolsEntryCmd.md)|返回菜单项占位符的命令ID用户工具。|  
|[CUserToolsManager::GetUserTools](../Topic/CUserToolsManager::GetUserTools.md)|返回对用户工具列表。|  
|[CUserToolsManager::InvokeTool](../Topic/CUserToolsManager::InvokeTool.md)|执行应用程序与具有指定的命令ID的用户工具.|  
|[CUserToolsManager::IsUserToolCmd](../Topic/CUserToolsManager::IsUserToolCmd.md)|确定命令ID是否与用户工具。|  
|[CUserToolsManager::LoadState](../Topic/CUserToolsManager::LoadState.md)|从Windows注册表加载有关用户工具的信息。|  
|[CUserToolsManager::MoveToolDown](../Topic/CUserToolsManager::MoveToolDown.md)|将指定的用户工具下在用户工具列表。|  
|[CUserToolsManager::MoveToolUp](../Topic/CUserToolsManager::MoveToolUp.md)|将指定的用户工具在用户工具列表。|  
|[CUserToolsManager::RemoveTool](../Topic/CUserToolsManager::RemoveTool.md)|从应用程序中移除指定的用户工具。|  
|[CUserToolsManager::SaveState](../Topic/CUserToolsManager::SaveState.md)|在Windows注册表存储有关用户工具的信息。|  
|[CUserToolsManager::SetDefExt](../Topic/CUserToolsManager::SetDefExt.md)|指定 **打开的文件** 对话框的默认扩展名\([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\)在 **自定义** 对话框的 **工具** 选项的 **命令** 字段。|  
|[CUserToolsManager::SetFilter](../Topic/CUserToolsManager::SetFilter.md)|指定 **打开的文件** 对话框的文件筛选器\([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\)在 **自定义** 对话框的 **工具** 选项的 **命令** 字段。|  
  
## 备注  
 若要将用户工具到应用程序中，您必须:  
  
 1.  保留菜单项和一个关联的命令ID用户的工具菜单项。  
  
 2.  保留控件续命令ID用户在应用程序中定义的每个用户工具。  
  
 3.  调用 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) 方法并提供了以下参数:菜单命令ID、首次用户工具命令ID和最后一个用户工具命令ID.  
  
 只应为每应用程序全局 `CUserToolsManager` 对象。  
  
 有关用户工具的示例，请参见VisualStudioDemo示例项目。  
  
## 示例  
 下面的示例演示如何检索对 `CUserToolsManager` 对象以及如何创建新用户工具。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/CPP/cusertoolsmanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)  
  
## 要求  
 **标头:** afxusertoolsmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserTool Class](../../mfc/reference/cusertool-class.md)