---
title: "COLUMN_ENTRY_PS_STATUS | Microsoft Docs"
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
  - "COLUMN_ENTRY_PS_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_PS_STATUS 宏"
ms.assetid: c02140c6-246f-4df5-8b86-698d7d137022
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_PS_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对行集合的绑定到数据库中的特定列。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_PS_STATUS(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
,   
status  
 )  
  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列数。  
  
 `nPrecision`  
 \[in\] 要绑定列的最大事精度。  
  
 `nScale`  
 \[in\] 要绑定的列的小数位数。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
 *status*  
 \[in\] 绑定的变量为列状态。  
  
## 备注  
 允许您指定要绑定列的精度和小数位数。  此宏支持 *状态* 变量。  在以下位置：  
  
-   在 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)[END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) 宏和之间。  
  
-   在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)[END\_ACCESSOR](../../data/oledb/end-accessor.md) 宏和之间。  
  
-   在 [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md)[END\_PARAM\_MAP](../../data/oledb/end-param-map.md) 宏和之间。  
  
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
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)