---
title: "CProcedureParameters CProcedureParamInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "m_szDefault"
  - "CProcedureParameters"
  - "m_bHasDefault"
  - "CProcedureParamInfo"
  - "IS_NULLABLE"
  - "m_szCatalog"
  - "ORDINAL_POSITION"
  - "m_nOrdinalPosition"
  - "NUMERIC_PRECISION"
  - "m_nDataType"
  - "m_szSchema"
  - "CHARACTER_OCTET_LENGTH"
  - "NUMERIC_SCALE"
  - "m_szParameterName"
  - "m_nMaxLength"
  - "CHARACTER_MAXIMUM_LENGTH"
  - "m_nPrecision"
  - "m_szName"
  - "DATA_TYPE"
  - "m_nOctetLength"
  - "m_nType"
  - "m_bIsNullable"
  - "m_nScale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHARACTER_MAXIMUM_LENGTH"
  - "CHARACTER_OCTET_LENGTH"
  - "CProcedureParameters typedef 类"
  - "CProcedureParamInfo 参数类"
  - "DATA_TYPE"
  - "DESCRIPTION 类数据成员"
  - "IS_NULLABLE"
  - "m_bHasDefault"
  - "m_bIsNullable"
  - "m_nDataType"
  - "m_nMaxLength"
  - "m_nOctetLength"
  - "m_nOrdinalPosition"
  - "m_nPrecision"
  - "m_nScale"
  - "m_nType"
  - "m_szCatalog"
  - "m_szDefault"
  - "m_szDescription"
  - "m_szName"
  - "m_szParameterName"
  - "m_szSchema"
  - "NUMERIC_PRECISION"
  - "NUMERIC_SCALE"
  - "ORDINAL_POSITION"
ms.assetid: 61f8d55a-684a-47a3-b102-068cc3f52d84
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CProcedureParameters CProcedureParamInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CProcedureParameters** 实现其参数类的 **CProcedureParamInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 返回有关过程的参数和返回代码的信息。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference* 中的 [PROCEDURE\_PARAMETERS Rowset](https://msdn.microsoft.com/en-us/library/ms713623.aspx) 。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|PROCEDURE\_CATALOG|  
|m\_szSchema|PROCEDURE\_SCHEMA|  
|m\_szName|PROCEDURE\_NAME|  
|m\_szParameterName|PARAMETER\_NAME|  
|m\_nOrdinalPosition|ORDINAL\_POSITION|  
|m\_nType|PARAMETER\_TYPE|  
|m\_bHasDefault|PARAMETER\_HASDEFAULT|  
|m\_szDefault|PARAMETER\_DEFAULT|  
|m\_bIsNullable|IS\_NULLABLE|  
|m\_nDataType|DATA\_TYPE|  
|m\_nMaxLength|CHARACTER\_MAXIMUM\_LENGTH|  
|m\_nOctetLength|CHARACTER\_OCTET\_LENGTH|  
|m\_nPrecision|NUMERIC\_PRECISION|  
|m\_nScale|NUMERIC\_SCALE|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)