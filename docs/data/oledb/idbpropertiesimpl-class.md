---
title: "IDBPropertiesImpl 类 | Microsoft Docs"
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
  - "IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBPropertiesImpl 类"
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IDBProperties` 接口的实现。  
  
## 语法  
  
```  
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### 参数  
 `T`  
 类是从`IDBPropertiesImpl` 中派生的。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[获得属性](../../data/oledb/idbpropertiesimpl-getproperties.md)|在数据源对象或值。初始化属性组中当前设置在枚举数当前设置的数据源、数据源的信息初始化和属性组中返回属性值。|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|提供程序返回有关支持的所有属性的信息。|  
|[设置属性](../../data/oledb/idbpropertiesimpl-setproperties.md)|为枚举器，数据源对象，或者对象初始化属性组，在数据源和初始化属性组当中设置属性。|  
  
## 备注  
 [oledbIDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) 是数据源的对象强制接口和枚举器的可选接口。  但是，公开 [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx)，则枚举器，必须公开 `IDBProperties`。  `IDBPropertiesImpl` 实现 `IDBProperties` 可通过使用 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)定义的静态函数。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)