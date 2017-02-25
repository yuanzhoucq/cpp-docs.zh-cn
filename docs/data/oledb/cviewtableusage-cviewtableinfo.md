---
title: "CViewTableUsage，CViewTableInfo | Microsoft Docs"
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
  - "m_szCatalog"
  - "CViewTableInfo"
  - "m_szTableCatalog"
  - "m_szSchema"
  - "m_szTableName"
  - "m_szName"
  - "CViewTableUsage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CViewTableInfo 参数类"
  - "CViewTableUsage typedef 类"
  - "m_szCatalog"
  - "m_szName"
  - "m_szSchema"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CViewTableUsage，CViewTableInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用typedef 类 **CViewTableUsage** 实现其参数类的 **CViewTableInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 此类标识显示的表，在目录中定义，指向特定用户进行访问。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB 程序员参考* 中的[VIEW\_COLUMN\_USAGE 行集](https://msdn.microsoft.com/en-us/library/ms719727.aspx)。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|VIEW\_CATALOG|  
|m\_szSchema|VIEW\_SCHEMA|  
|m\_szName|VIEW\_NAME|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)