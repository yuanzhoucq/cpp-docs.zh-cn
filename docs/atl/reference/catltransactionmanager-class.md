---
title: "CAtlTransactionManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlTransactionManager"
  - "atltransactionmanager/ATL::CAtlTransactionManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTransactionManager class"
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CAtlTransactionManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CAtlTransactionManager选件类提供一个包装为核心事务管理器\(KTM\)功能。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
class CAtlTransactionManager;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlTransactionManager::~CAtlTransactionManager](../Topic/CAtlTransactionManager::~CAtlTransactionManager.md)|CAtlTransactionManager析构函数。|  
|[CAtlTransactionManager::CAtlTransactionManager](../Topic/CAtlTransactionManager::CAtlTransactionManager.md)|CAtlTransactionManager构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlTransactionManager::Close](../Topic/CAtlTransactionManager::Close.md)|结束事务处理。|  
|[CAtlTransactionManager::Commit](../Topic/CAtlTransactionManager::Commit.md)|请求该事务提交。|  
|[CAtlTransactionManager::Create](../Topic/CAtlTransactionManager::Create.md)|创建事务处理。|  
|[CAtlTransactionManager::CreateFile](../Topic/CAtlTransactionManager::CreateFile.md)|创建或打开一个文件流、文件或目录为已处理的操作。|  
|[CAtlTransactionManager::DeleteFile](../Topic/CAtlTransactionManager::DeleteFile.md)|删除现有文件为已处理的操作。|  
|[CAtlTransactionManager::FindFirstFile](../Topic/CAtlTransactionManager::FindFirstFile.md)|搜索一个目录文件或子目录为已处理的操作。|  
|[CAtlTransactionManager::GetFileAttributes](../Topic/CAtlTransactionManager::GetFileAttributes.md)|检索指定的文件或目录中的文件系统属性为已处理的操作。|  
|[CAtlTransactionManager::GetFileAttributesEx](../Topic/CAtlTransactionManager::GetFileAttributesEx.md)|检索指定的文件或目录中的文件系统属性为已处理的操作。|  
|[CAtlTransactionManager::GetHandle](../Topic/CAtlTransactionManager::GetHandle.md)|返回事务处理。|  
|[CAtlTransactionManager::IsFallback](../Topic/CAtlTransactionManager::IsFallback.md)|确定为后备是否调用启用。|  
|[CAtlTransactionManager::MoveFile](../Topic/CAtlTransactionManager::MoveFile.md)|移动现有文件或一个目录，包括其子级，为已处理的操作。|  
|[CAtlTransactionManager::RegCreateKeyEx](../Topic/CAtlTransactionManager::RegCreateKeyEx.md)|创建指定的注册表项并将其与事务。  如果此键已存在，则函数将其打开。|  
|[CAtlTransactionManager::RegDeleteKey](../Topic/CAtlTransactionManager::RegDeleteKey.md)|从注册表中指定的平台特定视图删除子项及其值为已处理的操作。|  
|[CAtlTransactionManager::RegOpenKeyEx](../Topic/CAtlTransactionManager::RegOpenKeyEx.md)|打开指定的注册表项并将其与事务。|  
|[CAtlTransactionManager::Rollback](../Topic/CAtlTransactionManager::Rollback.md)|请求该事务将被回滚。|  
|[CAtlTransactionManager::SetFileAttributes](../Topic/CAtlTransactionManager::SetFileAttributes.md)|将文件或目录的属性为已处理的操作。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlTransactionManager::m\_bFallback](../Topic/CAtlTransactionManager::m_bFallback.md)|`TRUE`，如果为后备支持;否则 `FALSE`。|  
|[CAtlTransactionManager::m\_hTransaction](../Topic/CAtlTransactionManager::m_hTransaction.md)|事务处理。|  
  
## 备注  
  
## 继承层次结构  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## 要求  
 **Header:** atltransactionmanager.h  
  
## 请参阅  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)