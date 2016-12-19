---
title: "IRowsetInfoImpl::GetProperties | Microsoft Docs"
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
  - "ATL.IRowsetInfoImpl.GetProperties"
  - "IRowsetInfoImpl.GetProperties"
  - "ATL::IRowsetInfoImpl::GetProperties"
  - "IRowsetInfoImpl::GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties 方法"
ms.assetid: 62c12063-28e0-4a06-ad4d-21c5c1e9ccea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetInfoImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回属性的当前设置。**DBPROPSET\_ROWSET** 组中。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetProperties )(  
   const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets   
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB Programmer's Reference*中的[IRowsetInfo::GetProperties](https://msdn.microsoft.com/en-us/library/ms719611.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetInfoImpl 类](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)   
 [IRowsetInfoImpl::GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)