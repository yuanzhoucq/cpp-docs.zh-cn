---
title: "IRowsetUpdateImpl::GetRowStatus | Microsoft Docs"
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
  - "ATL.IRowsetUpdateImpl.GetRowStatus"
  - "IRowsetUpdateImpl::GetRowStatus"
  - "IRowsetUpdateImpl.GetRowStatus"
  - "ATL::IRowsetUpdateImpl::GetRowStatus"
  - "GetRowStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowStatus 方法"
ms.assetid: ce57e8be-5891-44d9-b3c5-59ffd3913678
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::GetRowStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回中指定的行状态。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetRowStatus )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]   
);  
```  
  
#### 参数  
 `hReserved`  
 \[in\] 对应于 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)的 `hChapter` 参数。  
  
 有关其他参数，请参阅《*OLE DB 程序员参考》\) 中的*[IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)