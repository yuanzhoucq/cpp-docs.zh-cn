---
title: "IAccessorImpl::GetBindings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IAccessorImpl.GetBindings"
  - "ATL::IAccessorImpl::GetBindings"
  - "IAccessorImpl::GetBindings"
  - "GetBindings"
  - "ATL.IAccessorImpl.GetBindings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBindings 方法"
ms.assetid: eb550077-77ef-450b-89f1-a2930cee6ab8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IAccessorImpl::GetBindings
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回来自使用者的基本列绑定访问器。  
  
## 语法  
  
```  
  
      STDMETHOD(GetBindings)(  
   HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings   
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[IAccessor::GetBindings](https://msdn.microsoft.com/en-us/library/ms721253.aspx)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IAccessorImpl 类](../../data/oledb/iaccessorimpl-class.md)