---
title: "CRowset::MoveLast | Microsoft Docs"
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
  - "ATL::CRowset<TAccessor>::MoveLast"
  - "CRowset<TAccessor>::MoveLast"
  - "ATL.CRowset.MoveLast"
  - "ATL::CRowset::MoveLast"
  - "CRowset<TAccessor>.MoveLast"
  - "MoveLast"
  - "CRowset::MoveLast"
  - "ATL.CRowset<TAccessor>.MoveLast"
  - "CRowset.MoveLast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveLast 方法"
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveLast
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将光标移动到最后一行。  
  
## 语法  
  
```  
  
HRESULT MoveLast( ) throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 调用 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) 重新定位 NeXT Fetch 位置到最后位置检索并最后一行。  
  
 此方法在调用**Open**之前需要将表或包含行集合中 **DBPROP\_CANSCROLLBACKWARDS**为`VARIANT_TRUE`。\(有关更好的性能，则还可能将 **DBPROP\_QUICKRESTART** 设置为 `VARIANT_TRUE`。\)  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)