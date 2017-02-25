---
title: "CShellManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CShellManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CShellManager class"
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CShellManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行允许使用指针使用到标识符列出的几种方法\(PIDLs）。  
  
## 语法  
  
```  
class CShellManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CShellManager::CShellManager](../Topic/CShellManager::CShellManager.md)|构造 `CShellManager` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CShellManager::BrowseForFolder](../Topic/CShellManager::BrowseForFolder.md)|显示用户可以选择shell文件夹的对话框。|  
|[CShellManager::ConcatenateItem](../Topic/CShellManager::ConcatenateItem.md)|串联两PIDLs。|  
|[CShellManager::CopyItem](../Topic/CShellManager::CopyItem.md)|创建新的PIDL并复制所提供的PIDL给它。|  
|[CShellManager::CreateItem](../Topic/CShellManager::CreateItem.md)|创建指定大小的新PIDL。|  
|[CShellManager::FreeItem](../Topic/CShellManager::FreeItem.md)|删除所提供的PIDL。|  
|[CShellManager::GetItemCount](../Topic/CShellManager::GetItemCount.md)|返回的项数。提供的PIDL的。|  
|[CShellManager::GetItemSize](../Topic/CShellManager::GetItemSize.md)|返回所提供的PIDL的大小。|  
|[CShellManager::GetNextItem](../Topic/CShellManager::GetNextItem.md)|返回从PIDL的下一项。|  
|[CShellManager::GetParentItem](../Topic/CShellManager::GetParentItem.md)|检索将所提供的项的父级项目。|  
|[CShellManager::ItemFromPath](../Topic/CShellManager::ItemFromPath.md)|检索由提供的路径所标识的项的PIDL。|  
  
## 备注  
 `CShellManager` 的方法类进行PIDLs的所有事务。  PIDL是shell对象的唯一标识符。  
  
 您不应该手动创建 `CShellManager` 对象。  它将由应用程序框架自动创建。  但是，您应调用时 [CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md) 初始化过程您的应用程序。  获取对shell管理器的指针应用程序中，调用 [CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## 要求  
 **标头:** afxshellmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)