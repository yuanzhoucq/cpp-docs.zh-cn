---
title: "PROVIDER_COLUMN_ENTRY_FIXED | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_FIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_FIXED 宏"
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_FIXED
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供程序所支持的特定列。  
  
## 语法  
  
```  
  
PROVIDER_COLUMN_ENTRY_FIXED(  
name  
, ordinal, dbtype, member )  
```  
  
#### 参数  
 *name*  
 \[in\] 列名称。  
  
 `ordinal`  
 \[in\] 列号。  除非将列是书签列，列数无法为 0。  
  
 `dbtype`  
 \[in\] 在 [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)的数据类型。  
  
 `member`  
 \[in\] 将数据存储在 `dataClass` 的成员变量。  
  
## 备注  
 可以指定列的数据类型。  
  
## 示例  
 参见[BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)