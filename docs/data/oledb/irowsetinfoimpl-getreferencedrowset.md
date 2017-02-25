---
title: "IRowsetInfoImpl::GetReferencedRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetInfoImpl::GetReferencedRowset"
  - "GetReferencedRowset"
  - "ATL.IRowsetInfoImpl.GetReferencedRowset"
  - "IRowsetInfoImpl.GetReferencedRowset"
  - "IRowsetInfoImpl::GetReferencedRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetReferencedRowset 方法"
ms.assetid: 94d2155c-9da0-4c19-a37c-bc35716359fd
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetInfoImpl::GetReferencedRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回指向对其应用书签或章节的行集合的接口指针。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetReferencedRowset )(  
   DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset   
);  
```  
  
#### 参数  
 有关更多信息，请参见[IRowsetInfo::GetReferencedRowset](https://msdn.microsoft.com/en-us/library/ms721145.aspx) in the *OLE DB Programmer's Reference*。  参数必须是 *iOrdinal* 书签列。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetInfoImpl 类](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)