---
title: "CCheckConstraints，CCheckConstraintInfo | Microsoft Docs"
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
  - "CCheckConstraintInfo"
  - "CHECK_CONSTRAINTS"
  - "m_szCatalog"
  - "CCheckConstraints"
  - "CONSTRAINT_NAME"
  - "m_szSchema"
  - "CHECK_CLAUSE"
  - "m_szCheckClause"
  - "m_szName"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCheckConstraintInfo 参数类"
  - "CCheckConstraints typedef 类"
  - "CHECK_CLAUSE"
  - "CHECK_CONSTRAINTS"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "DESCRIPTION 类数据成员"
  - "m_szCatalog"
  - "m_szCheckClause"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: e53e79a5-01e5-42b7-aa8c-164aec94b011
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCheckConstraints，CCheckConstraintInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CCheckConstraints** 实现其参数类的 **CCheckConstraintInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 使用 typedef 有关类的更多信息。  
  
 此类标识约束，定义检查目录中，由特定用户拥有。  CHECK 约束指定表内一列或多列中可接受的数据值或格式。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  参阅《*OLE DB 程序员参考》\) 中的*[CHECK\_CONSTRAINTS 行集合](https://msdn.microsoft.com/en-us/library/ms712845.aspx) 有关架构和列的更多信息。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_szCheckClause|CHECK\_CLAUSE|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)