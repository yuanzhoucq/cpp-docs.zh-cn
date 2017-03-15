---
title: "CSimpleRow::CSimpleRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSimpleRow"
  - "ATL::CSimpleRow::CSimpleRow"
  - "CSimpleRow.CSimpleRow"
  - "ATL.CSimpleRow.CSimpleRow"
  - "CSimpleRow::CSimpleRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleRow 类, 构造函数"
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSimpleRow::CSimpleRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

构造函数。  
  
## 语法  
  
```  
  
      CSimpleRow(  
   DBCOUNTITEM iRowsetCur   
);  
```  
  
#### 参数  
 `iRowsetCur`  
 \[in\] 当前对行集合的索引。  
  
## 备注  
 [m\_iRowset](../../data/oledb/csimplerow-m-irowset.md) 设置为 `iRowsetCur`。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)