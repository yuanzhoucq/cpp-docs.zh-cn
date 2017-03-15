---
title: "CColumnPrivileges，CColumnPrivilegeInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "m_szTableSchema"
  - "CColumnPrivileges"
  - "m_bIsGrantable"
  - "m_nColumnPropID"
  - "m_szPrivilegeType"
  - "COLUMN_GUID"
  - "IS_GRANTABLE"
  - "m_szColumnName"
  - "m_szTableCatalog"
  - "m_szGrantor"
  - "GRANTOR"
  - "GRANTEE"
  - "COLUMN_PROPID"
  - "m_guidColumn"
  - "COLUMN_PRIVILEGES"
  - "m_szTableName"
  - "CColumnPrivilegeInfo"
  - "m_szGrantee"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColumnPrivilegeInfo 参数类"
  - "CColumnPrivileges typedef 类"
  - "COLUMN_GUID"
  - "COLUMN_NAME"
  - "COLUMN_PRIVILEGES"
  - "COLUMN_PROPID"
  - "GRANTEE"
  - "GRANTOR"
  - "IS_GRANTABLE"
  - "m_bIsGrantable"
  - "m_guidColumn"
  - "m_nColumnPropID"
  - "m_szColumnName"
  - "m_szGrantee"
  - "m_szGrantor"
  - "m_szPrivilegeType"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 245df365-421f-43c6-9fcd-fb2197c871c6
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CColumnPrivileges，CColumnPrivilegeInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用定义类型类 **CColumnPrivileges** 实现其参数类的 **CColumnPrivilegeInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 使用 typedef 有关类的更多信息。  
  
 这个类标识了表中列的特权，在目录中定义、给定用户可获得或负责授予。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 [COLUMN\_PRIVILEGES 行集](https://msdn.microsoft.com/en-us/library/ms715800.aspx) 在 *OLE DB 程序员参考*  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szGrantor|GRANTOR|  
|m\_szGrantee|GRANTEE|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szColumnName|COLUMN\_NAME|  
|m\_guidColumn|COLUMN\_GUID|  
|m\_nColumnPropID|COLUMN\_PROPID|  
|m\_szPrivilegeType|PRIVILEGE\_TYPE|  
|m\_bIsGrantable|IS\_GRANTABLE|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)