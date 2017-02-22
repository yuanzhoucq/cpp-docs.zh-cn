---
title: "IRowsetUpdateImpl::GetOriginalData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetUpdateImpl.GetOriginalData"
  - "IRowsetUpdateImpl.GetOriginalData"
  - "GetOriginalData"
  - "ATL::IRowsetUpdateImpl::GetOriginalData"
  - "IRowsetUpdateImpl::GetOriginalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOriginalData 方法"
ms.assetid: 7477b3b7-6b1b-49a7-8167-b34323f0fdcc
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::GetOriginalData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从数据源获取数据传输，忽略挂起的更改。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetOriginalData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData   
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB 程序员参考* 中 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)