---
title: "CRowset::GetApproximatePosition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset::GetApproximatePosition"
  - "ATL::CRowset<TAccessor>::GetApproximatePosition"
  - "CRowset.GetApproximatePosition"
  - "CRowset::GetApproximatePosition"
  - "GetApproximatePosition"
  - "ATL.CRowset.GetApproximatePosition"
  - "CRowset<TAccessor>::GetApproximatePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetApproximatePosition 方法"
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetApproximatePosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回行的位置大概与书签的。  
  
## 语法  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### 参数  
 `pBookmark`  
 \[in\] 为标识行位置找到的书签的指针。  **NULL**，如果仅需要行计数。  
  
 *pPosition*  
 \[out\] 为返回 `GetApproximatePosition` 的行位置的位置的指针。  **NULL**，则不需位置。  
  
 `pcRows`  
 \[out\] 设置为 `GetApproximatePosition` 以返回总行数位置的指针。  **NULL**，如果不需要行计数。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetScroll`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  在对包含行集合中的 **打开** 表或命令之前，还必须设置 **DBPROP\_IRowsetScroll** 为 `VARIANT_TRUE` 。  
  
 有关用法信息的使用者中书签，请参见 [使用书签](../../data/oledb/using-bookmarks.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)