---
title: IRowsetInfoImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: ca22f16cf22cabc4c508df053d49d862fef70bce
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414611"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 类

提供一个实现[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))接口。

## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IRowsetInfoImpl`。

*PropClass*<br/>
用户可定义属性类，默认值为*T*。

## <a name="requirements"></a>要求

**标头：** altdb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetProperties](#getproperties)|返回由行集支持的所有属性的当前设置。|
|[GetReferencedRowset](#getreferencedrowset)|一个书签所应用于行集返回的接口指针。|
|[GetSpecification](#getspecification)|返回的接口指针上创建一个行集合的对象 （命令或会话）。|

## <a name="remarks"></a>备注

行集上的必需接口。 此类实现使用行集属性[属性集映射](../../data/oledb/begin-propset-map.md)命令类中定义。 虽然行集类将显示要使用命令类的属性设置，命令或会话对象创建时具有其自己副本的运行时属性，提供行集。

## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties

返回中的属性的当前设置`DBPROPSET_ROWSET`组。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>参数

请参阅[irowsetinfo:: Getproperties](/previous-versions/windows/desktop/ms719611(v=vs.85))中*OLE DB 程序员参考*。

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset

一个书签所应用于行集返回的接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85))中*OLE DB 程序员参考*。 *IOrdinal*参数必须为书签列。

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification

返回的接口指针上创建一个行集合的对象 （命令或会话）。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

将此方法用于[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)来从数据源对象检索属性。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)