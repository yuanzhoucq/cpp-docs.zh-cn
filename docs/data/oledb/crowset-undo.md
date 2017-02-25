---
title: "CRowset::Undo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset.Undo"
  - "ATL::CRowset<TAccessor>::Undo"
  - "CRowset<TAccessor>::Undo"
  - "ATL.CRowset.Undo"
  - "ATL.CRowset<TAccessor>.Undo"
  - "CRowset<TAccessor>.Undo"
  - "ATL::CRowset::Undo"
  - "CRowset::Undo"
  - "Undo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Undo 方法"
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::Undo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

撤消所做的任何更改。行，因为最后获取或 [更新](../../data/oledb/crowset-update.md)。  
  
## 语法  
  
```  
  
      HRESULT Undo(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### 参数  
 `pcRows`  
 \[out\] 对 **撤消** 返回的行数数量，如果尝试去撤销。  
  
 `phRow`  
 \[out\] 对 **撤消** 返回一个句柄所有行它的位置的指针。尝试如果必须撤消。  
  
 `pStatus`  
 \[out\] 对 **撤消** 返回行状态值的位置的指针。  如果 `pStatus` 为空，则状态不会返回。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetUpdate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)