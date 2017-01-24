---
title: "CProcedures，CProcedureInfo | Microsoft Docs"
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
  - "CProcedures"
  - "m_szCatalog"
  - "CProcedureInfo"
  - "m_szSchema"
  - "m_szDefinition"
  - "m_szName"
  - "m_nType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProcedureInfo 参数类"
  - "CProcedures typedef 类"
  - "DESCRIPTION 类数据成员"
  - "m_nType"
  - "m_szCatalog"
  - "m_szDefinition"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: d0c7375e-ee0c-441d-aae6-6108150860a0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CProcedures，CProcedureInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CProcedures** 实现其参数类的 **CProcedureInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 使用 typedef 有关类的更多信息。  
  
 此类标识过程定义，在目录，由特定用户拥有。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  参阅《*OLE DB 程序员参考》\) 中的*[过程行集合](https://msdn.microsoft.com/en-us/library/ms724021.aspx) 有关架构和列的更多信息。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|PROCEDURE\_CATALOG|  
|m\_szSchema|PROCEDURE\_SCHEMA|  
|m\_szName|PROCEDURE\_NAME|  
|m\_nType|PROCEDURE\_TYPE|  
|m\_szDefinition|PROCEDURE\_DEFINITION|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)