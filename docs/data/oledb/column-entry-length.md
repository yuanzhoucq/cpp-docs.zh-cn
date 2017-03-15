---
title: "COLUMN_ENTRY_LENGTH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_LENGTH 宏"
ms.assetid: 1758babf-204c-4d1d-b82a-f9a607072e9a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示行集合绑定到数据库的特定列。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_LENGTH(  
nOrdinal  
,   
data  
,   
length  
 )  
  
```  
  
#### 参数  
 请参阅在*OLE DB Programmer's Reference* 中 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列数，从一个语句开始。  书签列对应于零。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
 *length*  
 \[in\] 绑定的变量为列长度。  
  
## 备注  
 此宏支持 *长度* 变量。  使用方法如下：  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)和 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 宏之间。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和[END\_ACCESSOR](../../data/oledb/end-accessor.md) 宏之间。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) 和[END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 宏之间。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)