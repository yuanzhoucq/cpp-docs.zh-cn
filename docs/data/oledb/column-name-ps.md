---
title: "COLUMN_NAME_PS | Microsoft Docs"
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
  - "COLUMN_NAME_PS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME_PS 宏"
ms.assetid: 681795d5-0a95-4c8d-b188-2e6ed121ffaa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_NAME_PS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对行集合的绑定到行集合中的特定列。  类似于 [COLUMN\_NAME](../../data/oledb/column-name.md)，除此之外，此宏还使用精度和小数位数。  
  
## 语法  
  
```  
  
COLUMN_NAME_PS(  
pszName  
,   
nPrecision  
,   
nScale  
,   
data )  
```  
  
#### 参数  
 `pszName`  
 \[in\] 为列名的指针。  名称必须是一个 Unicode 字符串。  例如可以通过放置一个"左”Finalize 此名称，在前面：`L"MyColumn"`。  
  
 `nPrecision`  
 \[in\] 要绑定列的最大精度。  
  
 `nScale`  
 \[in\] 要绑定列的小数位数。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 备注  
 参见的信息使用 **COLUMN\_NAME\_\*** 宏对的 [COLUMN\_NAME](../../data/oledb/column-name.md) 有关。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME](../../data/oledb/column-name.md)   
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)