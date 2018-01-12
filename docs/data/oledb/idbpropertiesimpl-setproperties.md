---
title: "Idbpropertiesimpl:: Setproperties |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs: C++
helpviewer_keywords: SetProperties method
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d835810a2ca14c8e0631ed7dda8fcaddeb859d71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="idbpropertiesimplsetproperties"></a>IDBPropertiesImpl::SetProperties
枚举器在数据源和初始化属性组的数据源对象或初始化属性组中，设置属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 如果在初始化提供程序时，此方法会设置中的属性的值**DBPROPSET_DATASOURCE**， **DBPROPSET_DATASOURCEINFO**， **DBPROPSET_DBINIT**属性数据源对象的的组。 如果不初始化提供程序，则将设置**DBPROPSET_DBINIT**组仅属性。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBPropertiesImpl 类](../../data/oledb/idbpropertiesimpl-class.md)   
 [Idbpropertiesimpl:: Getproperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)