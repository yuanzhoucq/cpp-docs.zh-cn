---
title: "PROVIDER_COLUMN_ENTRY_LENGTH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_COLUMN_ENTRY_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_LENGTH 宏"
ms.assetid: b4a67246-c049-4622-bb65-242cc8cae4be
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# PROVIDER_COLUMN_ENTRY_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供程序所支持的特定列。  
  
## 语法  
  
```  
  
PROVIDER_COLUMN_ENTRY_LENGTH(  
name  
, ordinal, size, member )  
```  
  
#### 参数  
 *name*  
 \[in\] 列名。  
  
 `ordinal`  
 \[in\] 列数。  除非将列是书签列，列数无法为 0。  
  
 `size`  
 \[in\] 列大小 \(以字节为单位\)。  
  
 `member`  
 \[in\] 列存储数据。`dataClass` 的成员变量。  
  
## 备注  
 可以指定列的大小。  
  
## 示例  
 参见 [BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)