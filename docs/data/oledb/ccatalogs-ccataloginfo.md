---
title: "CCatalogs，CCatalogInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCatalogs"
  - "m_szName"
  - "CCatalogInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCatalogInfo 参数类"
  - "CCatalogs typedef 类"
  - "DESCRIPTION 类数据成员"
  - "m_szDescription"
  - "m_szName"
ms.assetid: 8362cbbd-2f00-4272-8518-fc235c4de193
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CCatalogs，CCatalogInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CCatalogs** 实现其参数类的 **CCatalogInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 此类标识物理特性与目录访问从用于 DBMS。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference* 中的 [CATALOGS Rowset](https://msdn.microsoft.com/en-us/library/ms721241.aspx) 。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szName|CATALOG\_NAME|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)