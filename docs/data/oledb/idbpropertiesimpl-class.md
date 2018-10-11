---
title: IDBPropertiesImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7f7662fabc53054b7a6712d271d89c2c3451067e
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083020"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 类

提供一个实现`IDBProperties`接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
### <a name="parameters"></a>参数  

*T*<br/>
您的类，派生自`IDBPropertiesImpl`。  

## <a name="requirements"></a>要求  

**标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|返回当前设置的数据源对象或当前设置初始化属性组中的属性值的数据源、 数据源信息和初始化属性组中的属性的值枚举器。|  
|[GetPropertyInfo](#getpropertyinfo)|返回有关提供程序支持的所有属性的信息。|  
|[SetProperties](#setproperties)|枚举器中的数据源和初始化的属性组，为数据源对象或初始化属性组中，设置属性。|  
  
## <a name="remarks"></a>备注  

[IDBProperties](/previous-versions/windows/desktop/ms719607)是数据源对象的必需接口和枚举器的可选接口。 但是，如果一个枚举器公开[IDBInitialize](/previous-versions/windows/desktop/ms713706)，则它必须公开`IDBProperties`。 `IDBPropertiesImpl` 实现`IDBProperties`通过使用定义的一个静态函数[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

## <a name="getproperties"></a> Idbpropertiesimpl:: Getproperties

返回当前设置的数据源对象或当前设置初始化属性组中的属性值的数据源、 数据源信息和初始化属性组中的属性的值枚举器。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[idbproperties:: Getproperties](/previous-versions/windows/desktop/ms714344)中*OLE DB 程序员参考*。  
  
某些参数对应于*OLE DB 程序员参考*中所述的不同名称的参数`IDBProperties::GetProperties`:  
  
|OLE DB 模板参数|*OLE DB 程序员参考*参数|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
### <a name="remarks"></a>备注  

如果在初始化提供程序时，此方法返回属性的值在 DBPROPSET_DATASOURCE，DBPROPSET_DATASOURCEINFO，当前在数据源对象设置的 DBPROPSET_DBINIT 属性组。 如果未初始化提供程序，则返回 DBPROPSET_DBINIT 组属性。 
  
## <a name="getpropertyinfo"></a> Idbpropertiesimpl:: Getpropertyinfo

返回支持的数据源的属性信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[idbproperties:: Getpropertyinfo](/previous-versions/windows/desktop/ms718175)中*OLE DB 程序员参考*。  
  
某些参数对应于*OLE DB 程序员参考*中所述的不同名称的参数`IDBProperties::GetPropertyInfo`:  
  
|OLE DB 模板参数|*OLE DB 程序员参考*参数|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
  
### <a name="remarks"></a>备注  

使用[idbinitializeimpl:: M_pcutlpropinfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)来实现此功能。 

## <a name="setproperties"></a> Idbpropertiesimpl:: Setproperties

枚举器中的数据源和初始化的属性组，为数据源对象或初始化属性组中，设置属性。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[idbproperties:: Setproperties](/previous-versions/windows/desktop/ms723049)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  

如果在初始化提供程序时，此方法设置属性的值中 DBPROPSET_DATASOURCE，DBPROPSET_DATASOURCEINFO，DBPROPSET_DBINIT 属性组中的数据源对象。 如果未初始化提供程序，它会设置 DBPROPSET_DBINIT 组属性。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)