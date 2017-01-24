---
title: "COLUMN_ENTRY_EX | Microsoft Docs"
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
  - "COLUMN_ENTRY_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_EX 宏"
ms.assetid: dfad1b67-51c3-4289-b89a-da42d7e8bb88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对行集合的绑定到数据库中的特定列。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_EX(  
nOrdinal  
,   
wType  
,   
nLength  
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
 参阅《*OLE DB 程序员参考》\) 中的*[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列数。  
  
 `wType`  
 \[in\] 数据类型。  
  
 `nLength`  
 \[in\] 数据大小 \(以字节为单位\)。  
  
 `nPrecision`  
 \[in\] 用于获取数据和 `wType` 时的最大 `DBTYPE_NUMERIC`是精度。  或者，忽略此参数。  
  
 `nScale`  
 \[in\] 用于获取数据和 `wType` 使用的小数位数是 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL**。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
 *length*  
 \[in\] 绑定的变量为列长度。  
  
 *status*  
 \[in\] 绑定的变量为列状态。  
  
## 备注  
 `COLUMN_ENTRY_EX` 宏在以下位置：  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)[END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 宏和之间。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)[END\_ACCESSOR](../../data/oledb/end-accessor.md) 宏和之间。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md)[END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 宏和之间。  
  
## 示例  
 参见 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)