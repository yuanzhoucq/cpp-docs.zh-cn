---
title: "CRowset::CRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset<TAccessor>::CRowset"
  - "CRowset.CRowset"
  - "ATL::CRowset::CRowset"
  - "ATL::CRowset<TAccessor>::CRowset"
  - "ATL.CRowset.CRowset"
  - "CRowset"
  - "CRowset<TAccessor>.CRowset"
  - "CRowset::CRowset"
  - "ATL.CRowset<TAccessor>.CRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowset 类, 构造函数"
ms.assetid: 1c6f72e2-f4f4-48dc-957e-038ae8914ba7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::CRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建新的 `CRowset` 对象，并 \(可选\) 它与为参数中提供的 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) 接口。  
  
## 语法  
  
```  
  
      CRowset( );   
CRowset(  
   IRowset* pRowset   
);  
```  
  
#### 参数  
 `pRowset`  
 \[in\] 将关联 `IRowset` 接口的指针使用此类。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)