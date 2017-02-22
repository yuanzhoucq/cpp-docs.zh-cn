---
title: "CRowset::MoveToBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset::MoveToBookmark"
  - "ATL::CRowset<TAccessor>::MoveToBookmark"
  - "ATL.CRowset.MoveToBookmark"
  - "ATL.CRowset<TAccessor>.MoveToBookmark"
  - "MoveToBookmark"
  - "CRowset::MoveToBookmark"
  - "CRowset.MoveToBookmark"
  - "CRowset<TAccessor>::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark 方法"
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提取书签标记的行按指定的偏移量 \(`lSkip`\) 从该书签。  
  
## 语法  
  
```  
  
      HRESULT MoveToBookmark(   
   const CBookmarkBase& bookmark,   
   LONG lSkip = 0    
) throw( );  
```  
  
#### 参数  
 `bookmark`  
 \[in\] 指示要提取数据位置的书签。  
  
 `lSkip`  
 \[in\] 数字计算从书签的行目标行。  如果 `lSkip` 为零，提取的第一行是加书签的行。  如果 `lSkip` 为 1，会提取的第一行是行，则书签的行之后。  如果 `lSkip` 为 1，会提取的第一行是行，则书签的行之前。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetLocate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetLocate**。`VARIANT_TRUE` 和 **DBPROP\_CANFETCHBACKWARDS** `VARIANT_TRUE` 集合。在对包含行集合中的 **打开** 表或命令。  
  
 有关用法信息的使用者中书签，请参见 [使用书签](../../data/oledb/using-bookmarks.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)