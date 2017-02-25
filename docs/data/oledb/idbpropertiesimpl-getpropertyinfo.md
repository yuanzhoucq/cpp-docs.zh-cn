---
title: "IDBPropertiesImpl::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBPropertiesImpl::GetPropertyInfo"
  - "IDBPropertiesImpl.GetPropertyInfo"
  - "GetPropertyInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPropertyInfo 方法"
ms.assetid: 170e9640-5010-4e0d-8a54-f50b23af08ad
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBPropertiesImpl::GetPropertyInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回数据源支持的属性信息。  
  
## 语法  
  
```  
  
      STDMETHOD(GetPropertyInfo)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer    
);  
```  
  
#### 参数  
 请参见 *OLE DB 程序员参考*中的 [IDBProperties::GetPropertyInfo](https://msdn.microsoft.com/en-us/library/ms718175.aspx)。  
  
 在**IDBProperties::GetPropertyInfo**中，有些参数对应于不同的名称的 *OLE DB 程序员参考* 参数：  
  
|OLE DB 模板参数|*OLE DB 程序员引用*参数|  
|-----------------|----------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
  
## 备注  
 使用 [IDBInitializeImpl::m\_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) 实现此功能。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IDBPropertiesImpl 类](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)