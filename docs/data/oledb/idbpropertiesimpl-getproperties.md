---
title: "IDBPropertiesImpl::GetProperties | Microsoft Docs"
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
  - "IDBPropertiesImpl::GetProperties"
  - "IDBPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties 方法"
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在数据源对象或值。初始化属性组中当前设置在枚举数当前设置的数据源、数据源的信息初始化和属性组中返回属性值。  
  
## 语法  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties    
);  
```  
  
#### 参数  
 有关详细信息，请参阅[IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx)在*OLE DB 程序员参考*中。  
  
 在**IDBProperties::GetPropertyInfo**中，有些参数对应于不同的名称的 *OLE DB 程序员参考* 参数：  
  
|OLE DB 模板参数|*OLE DB 程序员引用*参数|  
|-----------------|----------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*$1...$9 属性*|*nPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## 备注  
 如果提供程序被初始化，这个方法会为数据源对象设置 **DBPROPSET\_DATASOURCE DBPROPSET\_DATASOURCEINFO**，**DBPROPSET\_DBINIT** 这些属性组的属性。  如果提供程序尚未初始化，它将仅会设置**DBPROPSET\_DBINIT** 属性组的值。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IDBPropertiesImpl 类](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)