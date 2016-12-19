---
title: "IGetDataSourceImpl::GetDataSource | Microsoft Docs"
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
  - "GetDataSource"
  - "IGetDataSourceImpl.GetDataSource"
  - "IGetDataSourceImpl::GetDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDataSource 方法"
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IGetDataSourceImpl::GetDataSource
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回在创建会话的数据源对象的接口指针。  
  
## 语法  
  
```  
  
      STDMETHOD(GetDataSource)(   
   REFIID riid,   
   IUnknown ** ppDataSource    
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx)。  
  
## 备注  
 有用，则您需要访问数据源对象中的属性。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IGetDataSourceImpl 类](../../data/oledb/igetdatasourceimpl-class.md)