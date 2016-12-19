---
title: "CRowset::Compare | Microsoft Docs"
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
  - "CRowset<TAccessor>.Compare"
  - "CRowset<TAccessor>::Compare"
  - "ATL.CRowset<TAccessor>.Compare"
  - "ATL::CRowset<TAccessor>::Compare"
  - "CRowset.Compare"
  - "ATL::CRowset::Compare"
  - "ATL.CRowset.Compare"
  - "CRowset::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“比较”方法"
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)，比较两个书签。  
  
## 语法  
  
```  
  
      HRESULT Compare(   
   const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison    
) const throw( );  
```  
  
#### 参数  
 *Bookmark1*  
 \[in\] 要比较的第一个书签对象。  
  
 *Bookmark2*  
 \[in\] 要比较 的第二个书签对象。  
  
 `pComparison`  
 \[out\] 给比较结果的指针。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetLocate`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置 **DBPROP\_IRowsetUpdate**。`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
 有关用法信息的使用者中书签，请参见 [使用书签](../../data/oledb/using-bookmarks.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)