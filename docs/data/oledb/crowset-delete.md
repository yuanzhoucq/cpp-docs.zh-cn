---
title: "CRowset::Delete | Microsoft Docs"
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
  - "ATL::CRowset::Delete"
  - "CRowset.Delete"
  - "CRowset::Delete"
  - "ATL.CRowset.Delete"
  - "ATL::CRowset<TAccessor>::Delete"
  - "CRowset<TAccessor>.Delete"
  - "CRowset<TAccessor>::Delete"
  - "ATL.CRowset<TAccessor>.Delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Delete 方法"
ms.assetid: 4feb4f7e-139f-489a-b7d5-ea6ec0058e0f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Delete
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用从行集合中删除当前行的 [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx)。  
  
## 语法  
  
```  
  
HRESULT Delete( ) const throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)