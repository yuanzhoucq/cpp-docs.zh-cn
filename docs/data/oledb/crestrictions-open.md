---
title: "CRestrictions::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRestrictions.Open"
  - "ATL::CRestrictions::Open"
  - "ATL.CRestrictions.Open"
  - "CRestrictions::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRestrictions::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根据用户提供的限制返回结果集。  
  
## 语法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true  
);  
```  
  
#### 参数  
 `session`  
 \[in\] 指定用于的现有会话对象连接到数据源。  
  
 *lpszParam*  
 \[in\] 在架构行集指定限制。  
  
 `bBind`  
 \[in\] 指定是否自动绑定列映射。  默认是 **true**，导致命令自动绑定。  设置 `bBind` 为 **false** 以阻止命令的自动绑定，以便手动绑定。\(OLAP 用户对手动绑定特别感兴趣。\)  
  
## 返回值  
 标准`HRESULT` 值之一。  
  
## 备注  
 在架构行集可以指定最多七限制。  
  
 获取有关每个架构行集，所定义限制的信息请参见 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)