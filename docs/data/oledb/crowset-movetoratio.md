---
title: "CRowset::MoveToRatio | Microsoft Docs"
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
  - "MoveToRatio"
  - "CRowset<TAccessor>::MoveToRatio"
  - "CRowset::MoveToRatio"
  - "CRowset<TAccessor>.MoveToRatio"
  - "ATL.CRowset.MoveToRatio"
  - "ATL::CRowset::MoveToRatio"
  - "CRowset.MoveToRatio"
  - "ATL.CRowset<TAccessor>.MoveToRatio"
  - "ATL::CRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio 方法"
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取从在行集的一部分位置开始的行。  
  
## 语法  
  
```  
  
      HRESULT MoveToRatio(   
   DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,   
   bool bForward = true    
) throw( );  
```  
  
#### 参数  
 `nNumerator`  
 \[in\] 分子用于确定从中提取数据的分数位置。  
  
 `nDenominator`  
 \[in\] 分母用于确定从中提取数据的分数位置。  
  
 `bForward`  
 \[in\] 指明是向前还是向后移动。  默认为向前。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 `MoveToRatio` 大致根据以下公式提取行：  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中 `RowsetSize` 指行集合的以行衡量大小。  该公式的准确性依赖特定的提供程序。  有关详细信息，请参阅 [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx)。  
  
 此方法要求可选接口 `IRowsetScroll`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  在对包含行集合中的 **打开** 表或命令之前，还必须设置 **DBPROP\_IRowsetScroll** 为 `VARIANT_TRUE` 。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)