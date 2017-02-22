---
title: "IOpenRowsetImpl::CreateRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOpenRowsetImpl.CreateRowset"
  - "IOpenRowsetImpl::CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset 方法"
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IOpenRowsetImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个行集合对象。  未直接由用户调用。  有关更多信息，请参见  [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) in the *OLE DB Programmer's Reference.* 。  
  
## 语法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### 参数  
 `RowsetClass`  
 表示用户的行集合类的模板类的成员。  通常会通过向导产生。  
  
 `pRowsetObj`  
 \[out\] 指向行集合对象的指针。  通常不使用此参数，但是如果在传递到COM 对象之前必须对行集合进行更多的工作，它可以被使用。   `pRowsetObj` 的生存期由 `ppRowset`绑定。  
  
 有关其他参数，请参阅 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) 在《*OLE DB 程序员参考》中。*  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IOpenRowsetImpl 类](../../data/oledb/iopenrowsetimpl-class.md)