---
title: "CProcedureColumns，CProcedureColumnInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "m_guidType"
  - "CProcedureColumnInfo"
  - "IS_NULLABLE"
  - "m_szCatalog"
  - "m_nRowsetNumber"
  - "m_nColumnPropID"
  - "ORDINAL_POSITION"
  - "m_nOrdinalPosition"
  - "COLUMN_GUID"
  - "m_szColumnName"
  - "NUMERIC_PRECISION"
  - "m_nDataType"
  - "m_szSchema"
  - "CHARACTER_OCTET_LENGTH"
  - "NUMERIC_SCALE"
  - "COLUMN_PROPID"
  - "m_guidColumn"
  - "m_nMaxLength"
  - "CHARACTER_MAXIMUM_LENGTH"
  - "m_nPrecision"
  - "m_szName"
  - "CProcedureColumns"
  - "DATA_TYPE"
  - "m_nOctetLength"
  - "m_bIsNullable"
  - "m_nScale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHARACTER_MAXIMUM_LENGTH"
  - "CHARACTER_OCTET_LENGTH"
  - "COLUMN_GUID"
  - "COLUMN_NAME"
  - "COLUMN_PROPID"
  - "CProcedureColumnInfo 参数类"
  - "CProcedureColumns typedef 类"
  - "DATA_TYPE"
  - "DESCRIPTION 类数据成员"
  - "IS_NULLABLE"
  - "m_bIsNullable"
  - "m_guidColumn"
  - "m_guidType"
  - "m_nColumnPropID"
  - "m_nDataType"
  - "m_nMaxLength"
  - "m_nOctetLength"
  - "m_nOrdinalPosition"
  - "m_nPrecision"
  - "m_nRowsetNumber"
  - "m_nScale"
  - "m_szCatalog"
  - "m_szColumnName"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
  - "NUMERIC_PRECISION"
  - "NUMERIC_SCALE"
  - "ORDINAL_POSITION"
ms.assetid: c82626c4-8047-4b9c-b342-e35bf37b7611
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CProcedureColumns，CProcedureColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CProcedureColumns** 实现其参数类的 **CProcedureColumnInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 使用 typedef 有关类的更多信息。  
  
 返回有关此类过程返回行集中列的信息。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  参阅《*OLE DB 程序员参考》\) 中的*[PROCEDURE\_COLUMNS 行集合](https://msdn.microsoft.com/en-us/library/ms723092.aspx) 有关架构和列的更多信息。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|PROCEDURE\_CATALOG|  
|m\_szSchema|PROCEDURE\_SCHEMA|  
|m\_szName|PROCEDURE\_NAME|  
|m\_szColumnName|COLUMN\_NAME|  
|m\_guidColumn|COLUMN\_GUID|  
|m\_nColumnPropID|COLUMN\_PROPID|  
|m\_nRowsetNumber|ROWSET\_NUMBER|  
|m\_nOrdinalPosition|ORDINAL\_POSITION|  
|m\_bIsNullable|IS\_NULLABLE|  
|m\_nDataType|DATA\_TYPE|  
|m\_guidType|TYPE\_GUID|  
|m\_nMaxLength|CHARACTER\_MAXIMUM\_LENGTH|  
|m\_nOctetLength|CHARACTER\_OCTET\_LENGTH|  
|m\_nPrecision|NUMERIC\_PRECISION|  
|m\_nScale|NUMERIC\_SCALE|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)