---
title: "CCharacterSets，CCharacterSetInfo | Microsoft Docs"
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
  - "m_szCollateName"
  - "m_szCatalog"
  - "DEFAULT_COLLATE_NAME"
  - "m_szCollateSchema"
  - "FORM_OF_USE"
  - "DEFAULT_COLLATE_SCHEMA"
  - "m_szCollateCatalog"
  - "CCharacterSets"
  - "CHARACTER_SET_NAME"
  - "DEFAULT_COLLATE_CATALOG"
  - "CHARACTER_SET_SCHEMA"
  - "m_szFormOfUse"
  - "NUMBER_OF_CHARACTERS"
  - "m_szSchema"
  - "CHARACTER_SET_CATALOG"
  - "CCharacterSetInfo"
  - "m_nNumCharacters"
  - "m_szName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCharacterSetInfo 参数类"
  - "CCharacterSets typedef 类"
  - "CHARACTER_SET_CATALOG"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "DEFAULT_COLLATE_CATALOG"
  - "DEFAULT_COLLATE_NAME"
  - "DEFAULT_COLLATE_SCHEMA"
  - "FORM_OF_USE OLE DB 列"
  - "m_nNumCharacters"
  - "m_szCatalog"
  - "m_szCollateCatalog"
  - "m_szCollateName"
  - "m_szCollateSchema"
  - "m_szFormOfUse"
  - "m_szName"
  - "m_szSchema"
  - "NUMBER_OF_CHARACTERS"
ms.assetid: 029d068c-8bb2-4fc0-8709-78ce7f74446e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCharacterSets，CCharacterSetInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typedef 类调用 **CCharacterSets** 实现其参数类的 **CCharacterSetInfo**。  
  
## 备注  
 参见 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 中使用 typedef 类的更多信息。  
  
 此类标识对特定用户进行访问目录中定义的字符转换。  
  
 下表列出了类数据成员及其对应的 OLE DB 行。  有关架构和列的详细信息，请参阅 *OLE DB Programmer's Reference*中的[CHARACTER\_SETS Rowset](https://msdn.microsoft.com/en-us/library/ms722638.aspx)。  
  
|数据成员|OLE DB 列|  
|----------|--------------|  
|m\_szCatalog|CHARACTER\_SET\_CATALOG|  
|m\_szSchema|CHARACTER\_SET\_SCHEMA|  
|m\_szName|CHARACTER\_SET\_NAME|  
|m\_szFormOfUse|FORM\_OF\_USE|  
|m\_nNumCharacters|NUMBER\_OF\_CHARACTERS|  
|m\_szCollateCatalog|DEFAULT\_COLLATE\_CATALOG|  
|m\_szCollateSchema|DEFAULT\_COLLATE\_SCHEMA|  
|m\_szCollateName|DEFAULT\_COLLATE\_NAME|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)