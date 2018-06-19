---
title: 'Idbpropertiesimpl:: Getproperties |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
dev_langs:
- C++
helpviewer_keywords:
- GetProperties method
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ee384683d83845b88cb4026f8ff67f6bb69ba8b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103338"
---
# <a name="idbpropertiesimplgetproperties"></a>IDBPropertiesImpl::GetProperties
返回当前设置数据源对象的当前设置在初始化属性组中的属性的值的数据源、 数据源信息和初始化属性组中的属性的值枚举器。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetProperties)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx)中*OLE DB 程序员参考*。  
  
 某些参数都对应于*OLE DB 程序员参考*参数不同的名称中, 所述**IDBProperties::GetProperties**:  
  
|OLE DB 模板参数|*OLE DB 程序员参考*参数|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## <a name="remarks"></a>备注  
 如果在初始化提供程序时，此方法将返回中的属性的值**DBPROPSET_DATASOURCE**， **DBPROPSET_DATASOURCEINFO**， **DBPROPSET_DBINIT**当前设置对数据源对象的属性组。 如果未初始化提供程序，它将返回**DBPROPSET_DBINIT**组仅属性。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBPropertiesImpl 类](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)