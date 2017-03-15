---
title: "IDBPropertiesImpl::SetProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBPropertiesImpl.SetProperties"
  - "SetProperties"
  - "IDBPropertiesImpl::SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties 方法"
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为枚举器，数据源对象，或者对象初始化属性组，在数据源和初始化属性组当中设置属性。  
  
## 语法  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### 参数  
 有关详细信息，请参阅[IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx)在*OLE DB 程序员参考*中。  
  
## 备注  
 如果提供程序被初始化，这个方法会为数据源对象设置 **DBPROPSET\_DATASOURCE DBPROPSET\_DATASOURCEINFO**，**DBPROPSET\_DBINIT** 这些属性组的属性。  如果提供程序尚未初始化，它将仅会设置**DBPROPSET\_DBINIT** 属性组的值。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IDBPropertiesImpl 类](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)