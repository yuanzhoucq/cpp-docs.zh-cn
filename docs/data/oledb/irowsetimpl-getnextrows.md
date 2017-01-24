---
title: "IRowsetImpl::GetNextRows | Microsoft Docs"
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
  - "GetNextRows"
  - "ATL.IRowsetImpl.GetNextRows"
  - "ATL::IRowsetImpl::GetNextRows"
  - "IRowsetImpl::GetNextRows"
  - "IRowsetImpl.GetNextRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetNextRows 方法"
ms.assetid: 1c0975d6-d770-4884-830b-6986c6fa8e65
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::GetNextRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

按顺序获取行，同时记住以前的位置。  
  
## 语法  
  
```  
  
      STDMETHOD( GetNextRows )(  
   HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows   
);  
```  
  
#### 参数  
 请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms709827.aspx)（在  中）。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)