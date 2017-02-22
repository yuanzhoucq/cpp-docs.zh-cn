---
title: "COLUMN_NAME | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME 宏"
ms.assetid: a213b9a0-2148-4a08-9111-d9fa8fdec462
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_NAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表行集中一个绑定行集到特定列。  类似于 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)，除此之外，此宏使用列名代替列数。  
  
## 语法  
  
```  
  
COLUMN_NAME(  
pszName  
,   
data  
 )  
  
```  
  
#### 参数  
 `pszName`  
 \[in\] 为列名的指针。  名称必须是一个 Unicode 字符串。  例如可以通过放置一个 'L'在名称前面，例如：`L"MyColumn"`。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 备注  
 **COLUMN\_NAME\_\*** 宏在同一位置。[COLUMN\_ENTRY](../../data/oledb/column-entry.md):  
  
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
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)