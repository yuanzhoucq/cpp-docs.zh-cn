---
title: "CBulkRowset::MoveToRatio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBulkRowset.MoveToRatio"
  - "ATL::CBulkRowset::MoveToRatio"
  - "MoveToRatio"
  - "CBulkRowset::MoveToRatio"
  - "ATL.CBulkRowset<TAccessor>.MoveToRatio"
  - "ATL::CBulkRowset<TAccessor>::MoveToRatio"
  - "ATL.CBulkRowset.MoveToRatio"
  - "CBulkRowset<TAccessor>::MoveToRatio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToRatio 方法"
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CBulkRowset::MoveToRatio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取从在行集的一部分位置开始的行。  
  
## 语法  
  
```  
  
      HRESULT MoveToRatio(  
   DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator   
) throw( );  
```  
  
#### 参数  
 `nNumerator`  
 \[in\] 分子用于确定从中提取数据的分数位置。  
  
 `nDenominator`  
 \[in\] 分母用于确定从中提取数据的分数位置。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 `MoveToRatio` 大致根据以下公式提取行：  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中 `RowsetSize` 指行集合的以行衡量大小。  该公式的准确性依赖特定的提供程序。  有关详细信息，请参阅《*OLE DB 程序员参考》\) 中的*[IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)