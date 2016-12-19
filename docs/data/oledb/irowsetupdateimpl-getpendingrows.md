---
title: "IRowsetUpdateImpl::GetPendingRows | Microsoft Docs"
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
  - "IRowsetUpdateImpl::GetPendingRows"
  - "GetPendingRows"
  - "IRowsetUpdateImpl.GetPendingRows"
  - "ATL::IRowsetUpdateImpl::GetPendingRows"
  - "ATL.IRowsetUpdateImpl.GetPendingRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPendingRows 方法"
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::GetPendingRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回有挂起的更改的行列表。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetPendingRows )(  
   HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus   
);  
```  
  
#### 参数  
 `hReserved`  
 \[in\] 对应于 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)的 `hChapter` 参数。  
  
 有关其他参数，请参阅*OLE DB 程序员参考手册*中的[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)。  
  
## 备注  
 有关更多信息，请参见*OLE DB 程序员参考手册*中的[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)。  
  
## 要求  
 **标头：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)