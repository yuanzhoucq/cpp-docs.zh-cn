---
title: "CConstraintTableUsage，CConstraintTableUsageInfo | Microsoft Docs"
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
  - "CConstraintTableUsageInfo"
  - "CONSTRAINT_TABLE_USAGE"
  - "m_szTableSchema"
  - "m_szConstraintCatalog"
  - "CONSTRAINT_NAME"
  - "m_szTableCatalog"
  - "m_szConstraintSchema"
  - "m_szTableName"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
  - "CConstraintTableUsage"
  - "m_szConstraintName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConstraintTableUsage typedef 类"
  - "CConstraintTableUsageInfo 参数类"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "CONSTRAINT_TABLE_USAGE"
  - "m_szConstraintCatalog"
  - "m_szConstraintName"
  - "m_szConstraintSchema"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 666b44de-3922-4c5e-ad17-d5ea27120174
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CConstraintTableUsage，CConstraintTableUsageInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 typedef 类 **CConstraintTableUsage** 实现其参数类的 **CConstraintTableUsageInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 类标识由引用约束、唯一约束、CHECK 约束和在目录中定义并由给定用户拥有的断言使用的表。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB 程序员参考* 中 [CONSTRAINT\_TABLE\_USAGE 行集](https://msdn.microsoft.com/en-us/library/ms724522.aspx)。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szConstraintCatalog|CONSTRAINT\_CATALOG|  
|m\_szConstraintSchema|CONSTRAINT\_SCHEMA|  
|m\_szConstraintName|CONSTRAINT\_NAME|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)