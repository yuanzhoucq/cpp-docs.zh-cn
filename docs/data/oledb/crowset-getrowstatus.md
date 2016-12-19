---
title: "CRowset::GetRowStatus | Microsoft Docs"
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
  - "CRowset.GetRowStatus"
  - "ATL.CRowset<TAccessor>.GetRowStatus"
  - "ATL::CRowset<TAccessor>::GetRowStatus"
  - "CRowset::GetRowStatus"
  - "ATL::CRowset::GetRowStatus"
  - "CRowset<TAccessor>::GetRowStatus"
  - "ATL.CRowset.GetRowStatus"
  - "CRowset<TAccessor>.GetRowStatus"
  - "GetRowStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowStatus 方法"
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::GetRowStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回所有行状态。  
  
## 语法  
  
```  
  
      HRESULT GetRowStatus(   
   DBPENDINGSTATUS* pStatus    
) const throw( );  
```  
  
#### 参数  
 `pStatus`  
 \[out\] `GetRowStatus` 将状态值返回到位置的指针。  请参见 OLE DB 程序员参考中的DBPENDINGSTATUS。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetUpdate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)