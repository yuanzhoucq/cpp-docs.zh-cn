---
title: "COLUMN_ENTRY | Microsoft Docs"
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
  - "COLUMN_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY 宏"
ms.assetid: a10aef29-6d70-49ec-b572-5b5c4abe1b46
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表行集中一个绑定行集到特定列。  
  
## 语法  
  
```  
  
COLUMN_ENTRY(  
nOrdinal  
,   
data  
 )  
  
```  
  
#### 参数  
 请参阅在*OLE DB Programmer's Reference* 中 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列号。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 备注  
 `COLUMN_ENTRY` 宏在以下位置：  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)和 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 宏之间。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和[END\_ACCESSOR](../../data/oledb/end-accessor.md) 宏之间。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) 和[END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 宏之间。  
  
## 示例  
 参见在宏主题、[BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) 和 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)的示例。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [COLUMN\_ENTRY\_TYPE](../../data/oledb/column-entry-type.md)   
 [COLUMN\_ENTRY\_TYPE\_SIZE](../../data/oledb/column-entry-type-size.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)