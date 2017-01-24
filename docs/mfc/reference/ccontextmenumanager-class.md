---
title: "CContextMenuManager Class | Microsoft Docs"
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
  - "CContextMenuManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContextMenuManager class"
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: 32
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CContextMenuManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CContextMenuManager` 对象管理快捷菜单，也称为上下文菜单。  
  
## 语法  
  
```  
class CContextMenuManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CContextMenuManager::CContextMenuManager](../Topic/CContextMenuManager::CContextMenuManager.md)|构造 `CContextMenuManager` 对象。|  
|`CContextMenuManager::~CContextMenuManager`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CContextMenuManager::AddMenu](../Topic/CContextMenuManager::AddMenu.md)|添加新的快捷菜单。|  
|[CContextMenuManager::GetMenuById](../Topic/CContextMenuManager::GetMenuById.md)|将处理返回到菜单与提供的资源ID.|  
|[CContextMenuManager::GetMenuByName](../Topic/CContextMenuManager::GetMenuByName.md)|返回的句柄与所提供的菜单名的菜单。|  
|[CContextMenuManager::GetMenuNames](../Topic/CContextMenuManager::GetMenuNames.md)|返回菜单名列表。|  
|[CContextMenuManager::LoadState](../Topic/CContextMenuManager::LoadState.md)|加载在Windows注册表中存储的快捷菜单。|  
|[CContextMenuManager::ResetState](../Topic/CContextMenuManager::ResetState.md)|清除上下文菜单管理器的快捷菜单。|  
|[CContextMenuManager::SaveState](../Topic/CContextMenuManager::SaveState.md)|保存快捷菜单对于Windows注册表。|  
|[CContextMenuManager::SetDontCloseActiveMenu](../Topic/CContextMenuManager::SetDontCloseActiveMenu.md)|控件 `CContextMenuManager` 是否关闭活动的快捷菜单，在显示一个新的快捷菜单。|  
|[CContextMenuManager::ShowPopupMenu](../Topic/CContextMenuManager::ShowPopupMenu.md)|显示指定的快捷菜单。|  
|[CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md)|显示指定的快捷菜单。  返回选定菜单命令的索引。|  
  
## 备注  
 `CContextMenuManager` 管理快捷菜单并确保它们都具有一致的外观。  
  
 您不应该手动创建 `CContextMenuManager` 对象。  您的应用程序框架创建 `CContextMenuManager` 对象。  但是，那么，当您的应用程序初始化时，应调用 [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)。  在初始化上下文管理器后，请使用方法 [CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md) 获取指向您的应用程序的上下文管理器。  
  
 可以创建快捷菜单在运行时通过调用 `AddMenu`。  如果要显示菜单，而无需第一个接收的用户输入，请调用 `ShowPopupMenu`。  `TrackPopupMenu`，如果要创建菜单和等待用户输入时，请使用。  `TrackPopupMenu` 返回索引选定的命令或0，如果用户退出，而不选择任何操作。  
  
 `CContextMenuManager` 还可以保存和加载其状态更改为Windows注册表。  
  
## 示例  
 当 `CContextMenuManager` 对象公开一个新的弹出菜单时，下面的示例演示如何添加菜单。`CContextMenuManager` 对象和的不关闭活动的弹出菜单。  此代码段是 [自定义调用示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/CPP/ccontextmenumanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)  
  
## 要求  
 **标头:** afxcontextmenumanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)