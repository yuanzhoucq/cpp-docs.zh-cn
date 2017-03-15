---
title: "CRowset::UpdateAll | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::UpdateAll"
  - "ATL.CRowset.UpdateAll"
  - "CRowset<TAccessor>.UpdateAll"
  - "ATL.CRowset<TAccessor>.UpdateAll"
  - "UpdateAll"
  - "CRowset.UpdateAll"
  - "ATL::CRowset<TAccessor>::UpdateAll"
  - "CRowset<TAccessor>::UpdateAll"
  - "ATL::CRowset::UpdateAll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UpdateAll 方法"
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::UpdateAll
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

传输对它进行的对所有行，因为最后获取或 **更新** 调用所有挂起的更改。  
  
## 语法  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### 参数  
 `pcRows`  
 \[out\] 为 `UpdateAll` 返回的行数。它尝试更新位置的指针，则必须。  
  
 `pphRow`  
 \[out\] 设置为 `UpdateAll` 以返回行处理它的内存的指针。尝试更新。  如果 `pphRow` 为 null，句柄未返回。  
  
 `ppStatus`  
 \[out\] 对 **更新** 返回行状态值的位置的指针。  如果 `ppStatus` 为空，则状态不会返回。  
  
## 备注  
 使用 [更新](../../data/oledb/crowset-update.md) 或 `UpdateAll`，那么，这些行或更新，因为最后提取传输进行的所有挂起的更改的所有行。  `UpdateAll` 将更新修改的每一行，不管 \+ 是否仍有其处理 \(请参见 `pphRow`\)。  
  
 例如，在中，如果使用 **插入** 插入到行集合的五行，您可以调用 **更新** 五次或一次调用 `UpdateAll` 更新全部。  
  
 此方法要求可选接口 `IRowsetUpdate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)