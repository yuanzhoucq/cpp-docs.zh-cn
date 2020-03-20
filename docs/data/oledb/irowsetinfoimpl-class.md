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
ms.openlocfilehash: 7389ba689fb1f371b5fbf73045dcdc78cd465d88
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545839"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 类

提供[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetInfoImpl`的类。

*PropClass*<br/>
用户可定义的属性类，默认值为*T*。

## <a name="requirements"></a>要求

**标头：** altdb

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetProperties](#getproperties)|返回行集合支持的所有属性的当前设置。|
|[GetReferencedRowset](#getreferencedrowset)|返回一个接口指针，该指针指向应用书签的行集。|
|[GetSpecification](#getspecification)|返回对象（命令或会话）上用于创建此行集合的接口指针。|

## <a name="remarks"></a>备注

行集的必需接口。 此类通过使用在命令类中定义的[属性集](../../data/oledb/begin-propset-map.md)来实现行集属性。 尽管行集类看起来是使用 command 类的属性集，但在通过命令或会话对象创建行集时，将使用其自己的运行时属性副本来提供行集。

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a>IRowsetInfoImpl：： GetProperties

返回 `DBPROPSET_ROWSET` 组中属性的当前设置。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetInfo：： GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) 。

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a>IRowsetInfoImpl：： GetReferencedRowset

返回一个接口指针，该指针指向应用书签的行集。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetInfo：： GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) 。 *IOrdinal*参数必须是 bookmark 列。

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a>IRowsetInfoImpl：： GetSpecification

返回对象（命令或会话）上用于创建此行集合的接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetInfo：： GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) 。

### <a name="remarks"></a>备注

将此方法与[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)一起使用可从数据源对象检索属性。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)