---
title: "CTables，CTableInfo | Microsoft Docs"
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
  - "m_szCatalog"
  - "TABLE_SCHEMA"
  - "CTables"
  - "TABLE_NAME"
  - "TABLE_CATALOG"
  - "CTableInfo"
  - "m_guidTable"
  - "m_szType"
  - "m_szSchema"
  - "m_szName"
  - "TABLE_GUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTableInfo 参数类"
  - "CTables typedef 类"
  - "DESCRIPTION 类数据成员"
  - "m_guidTable"
  - "m_szCatalog"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
  - "m_szType"
  - "TABLE_CATALOG"
  - "TABLE_GUID"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 57670f1b-ba99-43b0-b406-4c75b44f14f6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTables，CTableInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 typedef 类**CTables** 实现其参数类 **CTableInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 使用 typedef 有关类的更多信息。  
  
 该类定义在目录中定义、给定用户可使用或负责授予的对表中列的特权。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference* 中的 [TABLES Rowset](https://msdn.microsoft.com/en-us/library/ms716980.aspx) 。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|TABLE\_CATALOG|  
|m\_szSchema|TABLE\_SCHEMA|  
|m\_szName|TABLE\_NAME|  
|m\_szType|TABLE\_TYPE|  
|m\_guidTable|TABLE\_GUID|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)