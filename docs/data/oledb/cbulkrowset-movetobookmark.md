---
title: "CBulkRowset::MoveToBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBulkRowset<TAccessor>::MoveToBookmark"
  - "CBulkRowset.MoveToBookmark"
  - "MoveToBookmark"
  - "ATL.CBulkRowset.MoveToBookmark"
  - "CBulkRowset::MoveToBookmark"
  - "ATL::CBulkRowset<TAccessor>::MoveToBookmark"
  - "ATL::CBulkRowset::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark 方法"
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CBulkRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提取书签标记的行按指定的偏移量 \(`lSkip`\) 从该书签。  
  
## 语法  
  
```  
  
      HRESULT MoveToBookmark(  
   const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0   
) throw( );  
```  
  
#### 参数  
 `bookmark`  
 \[in\] 指示要提取数据位置的书签。  
  
 `lSkip`  
 \[in\] 数字计算从书签的行目标行。  如果 `lSkip` 为零，提取的第一行是加书签的行。  如果 `lSkip` 为 1，会提取的第一行是行，则书签的行之后。  如果 `lSkip` 为 1，会提取的第一行是行，则书签的行之前。  
  
## 返回值  
 请参见 *OLE DB 程序员参考*中的[IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)