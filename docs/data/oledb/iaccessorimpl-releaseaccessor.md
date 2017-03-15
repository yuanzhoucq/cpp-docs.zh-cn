---
title: "IAccessorImpl::ReleaseAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReleaseAccessor"
  - "IAccessorImpl::ReleaseAccessor"
  - "ATL.IAccessorImpl.ReleaseAccessor"
  - "ATL::IAccessorImpl::ReleaseAccessor"
  - "IAccessorImpl.ReleaseAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAccessor 方法"
ms.assetid: 1526e360-bd9c-4ecd-967e-5afdd7506d2a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IAccessorImpl::ReleaseAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放访问器。  
  
## 语法  
  
```  
  
      STDMETHOD(ReleaseAccessor)(  
   HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount   
);  
```  
  
#### 参数  
 有关更多信息，请参见*OLE DB 程序员参考*中的  [IAccessor::ReleaseAccessor](https://msdn.microsoft.com/en-us/library/ms719717.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IAccessorImpl 类](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)   
 [IAccessorImpl::AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)