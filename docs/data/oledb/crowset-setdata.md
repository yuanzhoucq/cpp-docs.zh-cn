---
title: "CRowset::SetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.SetData"
  - "SetData"
  - "ATL::CRowset::SetData"
  - "CRowset<TAccessor>.SetData"
  - "CRowset::SetData"
  - "ATL.CRowset.SetData"
  - "CRowset.SetData"
  - "CRowset<TAccessor>::SetData"
  - "ATL::CRowset<TAccessor>::SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData 方法"
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置一行中的一列或多列中的数据值。  
  
## 语法  
  
```  
  
      HRESULT SetData( ) const throw( );   
HRESULT SetData(  
   int nAccessor   
) const throw( );  
```  
  
#### 参数  
 `nAccessor`  
 \[in\] 用来访问数据的访问器的索引号  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 对于不接受参数的 `SetData` 形式，所有访问器会使用更新。  通常可以调用 **SetData** 运行将数据列的值，然后调用 [更新](../../data/oledb/crowset-update.md) 传输这些更改。  
  
 此方法要求可选接口 `IRowsetChange`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置**DBPROP\_IRowsetChange**为`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
 如果一个或多个列是不可写，将操作可能失败。  修改游标映射以更正此问题。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)