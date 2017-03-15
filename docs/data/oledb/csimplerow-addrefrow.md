---
title: "CSimpleRow::AddRefRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSimpleRow::AddRefRow"
  - "AddRefRow"
  - "ATL.CSimpleRow.AddRefRow"
  - "ATL::CSimpleRow::AddRefRow"
  - "CSimpleRow.AddRefRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRow 方法"
ms.assetid: 9bb5b7a5-79f2-4de5-852c-e9918fe67665
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSimpleRow::AddRefRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将引用计数设置为现有行句柄。一种线程安全的方式。  
  
## 语法  
  
```  
  
DWORD AddRefRow( );  
  
```  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)