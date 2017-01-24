---
title: "CRowset::MoveNext | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>.MoveNext"
  - "ATL.CRowset.MoveNext"
  - "ATL::CRowset<TAccessor>::MoveNext"
  - "CRowset<TAccessor>.MoveNext"
  - "CRowset.MoveNext"
  - "CRowset<TAccessor>::MoveNext"
  - "CRowset::MoveNext"
  - "ATL::CRowset::MoveNext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveNext 方法"
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveNext
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将光标移动到下一条记录。  
  
## 语法  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### 参数  
 `lSkip`  
 \[in\] 跳过行数在读取前。  
  
 `bForward`  
 \[in\]  **true** 向前移动到下一记录， **false**向后移动。  
  
## 返回值  
 标准版`HRESULT`。  当处于行集合的末尾时，返回 **DB\_S\_ENDOFROWSET**。  
  
## 备注  
 从 `CRowset` 对象提取下一连续行，确保前一个位置。  或者，您可以选择跳过前 `lSkip` 行或向后移动。  
  
 此方法需要在对表的 **打开** 或命令之前设置以下属性，包含行集合：  
  
-   **DBPROP\_CANSCROLLBACKWARDS**必须是 `VARIANT_TRUE`，如果 `lSkip` \<  为 0  
  
-   **DBPROP\_CANFETCHBACKWARDS** 必须是 `VARIANT_TRUE`，如果 `bForward` \= false  
  
 否则 \(如果`lSkip` \>\= 0 和 `bForward` \= true\)，则不需要设置任何附加属性。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)