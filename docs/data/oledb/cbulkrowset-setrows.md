---
title: "CBulkRowset::SetRows | Microsoft Docs"
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
  - "ATL.CBulkRowset.SetRows"
  - "CBulkRowset::SetRows"
  - "CBulkRowset<TAccessor>.SetRows"
  - "ATL.CBulkRowset<TAccessor>.SetRows"
  - "CBulkRowset<TAccessor>::SetRows"
  - "ATL::CBulkRowset<TAccessor>::SetRows"
  - "ATL::CBulkRowset::SetRows"
  - "CBulkRowset.SetRows"
  - "SetRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetRows 方法"
ms.assetid: 7e92312a-bfd0-4c24-a799-62bef663f28e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::SetRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置行数每个调用检索的句柄。  
  
## 语法  
  
```  
  
      void SetRows(  
   DBROWCOUNT nRows   
) throw( );  
```  
  
#### 参数  
 `nRows`  
 \[in\] 行集合 \(行数的新范围。\)  
  
## 备注  
 如果调用该函数，则它必须是，在之前打开行集合。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)