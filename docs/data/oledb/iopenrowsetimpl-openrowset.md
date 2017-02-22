---
title: "IOpenRowsetImpl::OpenRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OpenRowset"
  - "IOpenRowsetImpl::OpenRowset"
  - "IOpenRowsetImpl.OpenRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenRowset 方法"
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IOpenRowsetImpl::OpenRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开并返回一个包含基表或索引中所有行的行集合。  
  
## 语法  
  
```  
  
      HRESULT OpenRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset   
);  
```  
  
#### 参数  
 有关更多信息，请参见 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中的*OLE DB 程序员参考* 。  
  
## 备注  
 ATLDB.H 中没有此方法。  它会由“ATL对象向导”创建，当你创建一个提供程序时。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IOpenRowsetImpl 类](../../data/oledb/iopenrowsetimpl-class.md)