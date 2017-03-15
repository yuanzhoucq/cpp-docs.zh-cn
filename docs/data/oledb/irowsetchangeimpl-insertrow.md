---
title: "IRowsetChangeImpl::InsertRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetChangeImpl.InsertRow"
  - "InsertRow"
  - "IRowsetChangeImpl.InsertRow"
  - "ATL::IRowsetChangeImpl::InsertRow"
  - "IRowsetChangeImpl::InsertRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InsertRow 方法"
ms.assetid: 93027be3-921e-438e-a19a-6e5aadb813eb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetChangeImpl::InsertRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建并初始化在行集合中的新行。  
  
## 语法  
  
```  
  
      STDMETHOD ( InsertRow )(  
   HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow   
);  
```  
  
#### 参数  
 有关更多信息，请参见[IRowsetChange::InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx) 在*OLE DB Programmer's Reference*中。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetChangeImpl 类](../../data/oledb/irowsetchangeimpl-class.md)