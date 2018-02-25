---
title: "IDBPropertiesImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e1b1486d5eff73b4f868f5990ceb628cfb7dd20a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 类
提供的实现`IDBProperties`接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IDBPropertiesImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|返回当前设置数据源对象的当前设置在初始化属性组中的属性的值的数据源、 数据源信息和初始化属性组中的属性的值枚举器。|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|返回有关提供程序支持的所有属性的信息。|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|枚举器在数据源和初始化属性组的数据源对象或初始化属性组中，设置属性。|  
  
## <a name="remarks"></a>备注  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx)是数据源对象的必需接口和枚举器的可选接口。 但是，如果一个枚举器公开[IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx)，它必须公开`IDBProperties`。 `IDBPropertiesImpl` 实现`IDBProperties`使用通过定义的静态函数[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)