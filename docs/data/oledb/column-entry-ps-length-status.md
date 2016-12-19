---
title: "COLUMN_ENTRY_PS_LENGTH_STATUS | Microsoft Docs"
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
  - "COLUMN_ENTRY_PS_LENGTH_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_PS_LENGTH_STATUS 宏"
ms.assetid: 04291671-329d-4974-b04e-36ef3f037787
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_PS_LENGTH_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示行集合绑定到数据库的特定列。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_PS_LENGTH_STATUS(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
,   
length  
,   
status  
 )  
  
```  
  
#### 参数  
 请参阅在*OLE DB Programmer's Reference* 中 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列号。  
  
 `nPrecision`  
 \[in\] 要绑定列的最大精度。  
  
 `nScale`  
 \[in\] 要绑定列的小数位数。  
  
 `data`  
 \[in\] 用户记录中的相应数据成员。  
  
 *length*  
 \[in\] 绑定的变量为列长度。  
  
 *status*  
 \[in\] 绑定变量到列状态。  
  
## 备注  
 允许您指定要绑定列的精度和小数位数。  如果只想支持长度和状态变量时，请使用此宏。  使用方法如下：  
  
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
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)