---
title: "CRowset::GetOriginalData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.GetOriginalData"
  - "CRowset<TAccessor>::GetOriginalData"
  - "GetOriginalData"
  - "ATL::CRowset<TAccessor>::GetOriginalData"
  - "ATL.CRowset.GetOriginalData"
  - "CRowset::GetOriginalData"
  - "ATL::CRowset::GetOriginalData"
  - "CRowset.GetOriginalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOriginalData 方法"
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetOriginalData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用检索数据的新 **IRowsetUpdate::GetOriginalData** 提取或传输到数据源。  
  
## 语法  
  
```  
  
HRESULT GetOriginalData( ) throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法检索数据从新或传输到数据源；它不检索基于挂起的更改的值。  
  
 此方法要求可选接口 `IRowsetUpdate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)