---
title: "CBulkRowset::MoveNext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CBulkRowset<TAccessor>.MoveNext"
  - "ATL::CBulkRowset::MoveNext"
  - "CBulkRowset::MoveNext"
  - "ATL.CBulkRowset.MoveNext"
  - "CBulkRowset.MoveNext"
  - "ATL::CBulkRowset<TAccessor>::MoveNext"
  - "CBulkRowset<TAccessor>.MoveNext"
  - "CBulkRowset<TAccessor>::MoveNext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveNext 方法"
ms.assetid: 788f3344-cf60-4af1-8f5f-0098c8d1a3f0
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CBulkRowset::MoveNext
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据检索下一行。  
  
## 语法  
  
```  
  
HRESULT MoveNext( ) throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  当处于行集合的末尾时，返回 **DB\_S\_ENDOFROWSET**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)