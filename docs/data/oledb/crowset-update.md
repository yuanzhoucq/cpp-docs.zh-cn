---
title: "CRowset::Update | Microsoft Docs"
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
  - "CRowset.Update"
  - "ATL.CRowset.Update"
  - "ATL.CRowset<TAccessor>.Update"
  - "ATL::CRowset<TAccessor>::Update"
  - "CRowset<TAccessor>::Update"
  - "CRowset::Update"
  - "CRowset<TAccessor>.Update"
  - "ATL::CRowset::Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update 方法"
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

传输其上进行为当前行，因为最后获取或 **更新** 调用所有挂起的更改。  
  
## 语法  
  
```  
  
      HRESULT Update(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### 参数  
 `pcRows`  
 \[out\] 对 **更新** 返回的行数。它尝试更新位置的指针，则必须。  
  
 `phRow`  
 \[out\] 对 **更新** 返回行处理它的位置的指针。尝试更新。  如果 `phRow` 为 null，句柄未返回。  
  
 `pStatus`  
 \[out\] 对 **更新** 返回行状态值的位置的指针。  如果 `pStatus` 为空，则状态不会返回。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 传输从那时起进行的所有挂起的更改。获取最后一行或更新的当前行 \(使用 **更新** 或\)。[UpdateAll](../../data/oledb/crowset-updateall.md) 通常连续调用 [SetData](../../data/oledb/crowset-setdata.md) 将列的数据值，然后调用 **更新** 传输这些更改。  
  
 此方法要求可选接口 `IRowsetUpdate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)