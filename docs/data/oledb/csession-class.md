---
title: "CSession 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession"
  - "ATL::CSession"
  - "ATL.CSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession 类"
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示单个数据库访问会话。  
  
## 语法  
  
```  
class CSession  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[中止](../../data/oledb/csession-abort.md)|取消（终止）事务。|  
|[关闭](../../data/oledb/csession-close.md)|关闭会话。|  
|[提交](../../data/oledb/csession-commit.md)|提交事务。|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|返回有关事务的信息。|  
|[打开](../../data/oledb/csession-open.md)|启动数据源对象的新会话。|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|开始此会话的新事务。|  
  
## 备注  
 一个或多个会话可以与每个提供程序连接 \(数据源\)，该请求由对象表示。[CDataSource](../../data/oledb/cdatasource-class.md) 创建 `CDataSource`的新 `CSession`，调用 [CSession::Open](../../data/oledb/csession-open.md)。  若要开始数据库执行，`CSession` 提供了 `StartTransaction` 方法。  事务一旦启动，使用 **提交** 方法，可以提交到，它使用 **中止** 方法，也请移除它。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [CatDB](../../top/visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)