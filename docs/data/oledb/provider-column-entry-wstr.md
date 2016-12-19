---
title: "PROVIDER_COLUMN_ENTRY_WSTR | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_WSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_WSTR 宏"
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_WSTR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供程序所支持的特定列。  
  
## 语法  
  
```  
  
PROVIDER_COLUMN_ENTRY_WSTR(  
name  
, ordinal, member )  
```  
  
#### 参数  
 *name*  
 \[in\] 列名称。  
  
 `ordinal`  
 \[in\] 列号。  除非将列是书签列，列数无法为 0。  
  
 `member`  
 \[in\] 在存储数据的数据类的成员变量。  
  
## 备注  
 使用此宏，在列数据是以 null 终止的 Unicode 字符串时，[DBTYPE\_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)