---
title: "CViewColumnUsage，CViewColumnInfo | Microsoft Docs"
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
  - "m_szTableSchema"
  - "m_szCatalog"
  - "m_nColumnPropID"
  - "COLUMN_GUID"
  - "m_szColumnName"
  - "m_szTableCatalog"
  - "CViewColumnInfo"
  - "m_szSchema"
  - "CViewColumnUsage"
  - "COLUMN_PROPID"
  - "m_guidColumn"
  - "m_szTableName"
  - "m_szName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_GUID"
  - "COLUMN_NAME"
  - "COLUMN_PROPID"
  - "CViewColumnInfo 参数类"
  - "CViewColumnUsage typedef 类"
  - "m_guidColumn"
  - "m_nColumnPropID"
  - "m_szCatalog"
  - "m_szColumnName"
  - "m_szName"
  - "m_szSchema"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 4af14d6b-b224-4d72-b035-9d3aaacde32f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CViewColumnUsage，CViewColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 typedef 类 **CViewColumnUsage** 实现其参数类 **CViewColumnInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 定义视图表上的列的类在在目录中定义并由给定用户拥有的表，是从属的。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB 程序员参考* 中 [VIEW\_COLUMN\_USAGE 行集](https://msdn.microsoft.com/en-us/library/ms714896.aspx)。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|VIEW\_CATALOG|  
|m\_szSchema|VIEW\_SCHEMA|  
|m\_szName|VIEW\_NAME|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szColumnName|COLUMN\_NAME|  
|m\_guidColumn|COLUMN\_GUID|  
|m\_nColumnPropID|COLUMN\_PROPID|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)