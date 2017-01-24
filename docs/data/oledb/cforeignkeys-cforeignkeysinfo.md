---
title: "CForeignKeys，CForeignKeysInfo | Microsoft Docs"
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
  - "m_nOrdinal"
  - "m_szPKColumnName"
  - "FK_TABLE_NAME"
  - "m_guidFKColumn"
  - "FK_COLUMN_NAME"
  - "m_guidPKColumn"
  - "DELETE_RULE"
  - "m_szPKTableSchema"
  - "FK_COLUMN_PROPID"
  - "m_nFKColumnPropID"
  - "m_szFKTableCatalog"
  - "CForeignKeysInfo"
  - "FK_TABLE_SCHEMA"
  - "m_szPKTableCatalog"
  - "m_szDeleteRule"
  - "m_szUpdateRule"
  - "m_szPKTableName"
  - "m_szFKTableSchema"
  - "ORDINAL"
  - "m_nPKColumnPropID"
  - "m_szFKColumnName"
  - "FK_TABLE_CATALOG"
  - "FK_COLUMN_GUID"
  - "m_szFKTableName"
  - "CForeignKeys"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CForeignKeys typedef 类"
  - "CForeignKeysInfo 参数类"
  - "DELETE_RULE"
  - "FK_COLUMN_GUID"
  - "FK_COLUMN_NAME"
  - "FK_COLUMN_PROPID"
  - "FK_TABLE_CATALOG"
  - "FK_TABLE_NAME"
  - "FK_TABLE_SCHEMA"
  - "m_guidFKColumn"
  - "m_guidPKColumn"
  - "m_nFKColumnPropID"
  - "m_nOrdinal"
  - "m_nPKColumnPropID"
  - "m_szDeleteRule"
  - "m_szFKColumnName"
  - "m_szFKTableCatalog"
  - "m_szFKTableName"
  - "m_szFKTableSchema"
  - "m_szPKColumnName"
  - "m_szPKTableCatalog"
  - "m_szPKTableName"
  - "m_szPKTableSchema"
  - "m_szUpdateRule"
  - "ORDINAL 数据成员"
ms.assetid: 1c401a4a-0827-4255-9214-bc893e1cd79d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CForeignKeys，CForeignKeysInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CForeignKeys** 实现其参数类的 **CForeignKeysInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 返回由给定用户在目录中定义的外键列。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference* 中的 [KEYS\_LANGUAGES Rowset](https://msdn.microsoft.com/en-us/library/ms711276.aspx) 。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szPKTableCatalog|PK\_TABLE\_CATALOG|  
|m\_szPKTableSchema|PK\_TABLE\_SCHEMA|  
|m\_szPKTableName|PK\_TABLE\_NAME|  
|m\_szPKColumnName|PK\_COLUMN\_NAME|  
|m\_guidPKColumn|PK\_COLUMN\_GUID|  
|m\_nPKColumnPropID|PK\_COLUMN\_PROPID|  
|m\_szFKTableCatalog|FK\_TABLE\_CATALOG|  
|m\_szFKTableSchema|FK\_TABLE\_SCHEMA|  
|m\_szFKTableName|FK\_TABLE\_NAME|  
|m\_szFKColumnName|FK\_COLUMN\_NAME|  
|m\_guidFKColumn|FK\_COLUMN\_GUID|  
|m\_nFKColumnPropID|FK\_COLUMN\_PROPID|  
|m\_nOrdinal|ORDINAL|  
|m\_szUpdateRule|UPDATE\_RULE|  
|m\_szDeleteRule|DELETE\_RULE|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)