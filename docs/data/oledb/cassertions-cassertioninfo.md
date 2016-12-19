---
title: "CAssertions，CAssertionInfo | Microsoft Docs"
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
  - "CAssertions"
  - "m_szCatalog"
  - "m_bInitiallyDeferred"
  - "CONSTRAINT_NAME"
  - "m_szSchema"
  - "INITIALLY_DEFERRED"
  - "m_bIsDeferrable"
  - "m_szName"
  - "CAssertionInfo"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
  - "IS_DEFERRABLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAssertionInfo 参数类"
  - "CAssertions typedef 类"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "DESCRIPTION 类数据成员"
  - "INITIALLY_DEFERRED"
  - "IS_DEFERRABLE"
  - "m_bInitiallyDeferred"
  - "m_bIsDeferrable"
  - "m_szCatalog"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAssertions，CAssertionInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用typedef 类 **CAssertions** 以实现其参数类 **CAssertionInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 此类引用定义在目录中由特定用户拥有的指针。  
  
 下表列出 **CAssertionInfo**的数据成员及其对应的 OLE DB 列。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference* 中的 [STATISTICS Rowset](https://msdn.microsoft.com/en-us/library/ms719776.aspx)。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_bIsDeferrable|IS\_DEFERRABLE|  
|m\_bInitiallyDeferred|INITIALLY\_DEFERRED|  
|m\_szDescription|DESCRIPTION|  
  
## 要求  
 **页眉：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)