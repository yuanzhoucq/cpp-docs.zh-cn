---
title: IDBSchemaRowsetImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 960f28538763331affdab0ef4e2e2aca831a82d4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058839"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 类

提供架构行集的实现。

## <a name="syntax"></a>语法

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>参数

*SessionClass*<br/>
继承 `IDBSchemaRowsetImpl` 的类。 通常情况下，此类将是用户的会话类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CheckRestrictions](#checkrestrictions)|检查针对架构行集的限制的有效性。|
|[CreateSchemaRowset](#createschemarowset)|对模板参数指定的对象实现 COM 对象创建程序函数。|
|[SetRestrictions](#setrestrictions)|指定在特定架构行集上支持哪些限制。|

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetRowset](#getrowset)|返回架构行集。|
|[GetSchemas](#getschemas)|返回可由 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)访问的架构行集的列表。|

## <a name="remarks"></a>备注

此类实现 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) 接口和模板化创建程序函数 [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)。

OLE DB 使用架构行集返回与提供程序中的数据有关的数据。 此类数据通常称为“元数据”。 默认情况下，提供程序必须始终支持`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，并`DBSCHEMA_PROVIDER_TYPES`，如中所述[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程序员参考*。 架构行集在架构映射中指定。 有关架构映射项的信息，请参阅 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)。

ATL 对象向导中的 OLE DB 提供程序向导自动生成项目中的架构行集的代码。 （默认情况下，该向导支持前面提到的必需的架构行集。）当你使用 ATL 对象向导创建使用者时，该向导使用架构行集将正确数据绑定到提供程序。 如果未实现架构行集来提供正确的元数据，向导将不会绑定正确的数据。

有关如何支持提供程序中的架构行集的信息，请参阅 [支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。

有关架构行集的详细信息，请参阅 [OLE DB 程序员参考](/previous-versions/windows/desktop/ms712921) 中的 *架构行集*。

## <a name="checkrestrictions"></a> Idbschemarowsetimpl:: Checkrestrictions

检查针对架构行集的限制的有效性。

### <a name="syntax"></a>语法

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>参数

*rguidSchema*<br/>
[in] 对所请求架构行集 GUID（例如， `DBSCHEMA_TABLES`）的引用。

*cRestrictions*<br/>
[in] 使用者为架构行集传入的限制数目。

*rgRestrictions*<br/>
[in] 要设置的限制值的长度 *cRestrictions* 数组。 有关详细信息，请参阅的说明*rgRestrictions*中的参数[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。

### <a name="remarks"></a>备注

使用 `CheckRestrictions` 可对架构行集检查限制的有效性。 它将检查限制`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`架构行集。 调用它可确定使用者的调用`IDBSchemaRowset::GetRowset`正确无误。 如果要支持上面所列架构行集以外的架构行集，应当创建自己的函数来执行此任务。

`CheckRestrictions` 确定是否调用使用者[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)正确限制和正确限制类型 (例如，字符串 VT_BSTR) 提供程序支持。 它还确定是否支持正确的限制数目。 默认情况下， `CheckRestrictions` 将通过 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 调用询问提供程序其在给定行集上支持的限制。 然后，它会将使用者提供的限制与提供程序支持的限制进行比较，并且要么成功要么失败。

有关架构行集的详细信息，请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程序员参考*Windows SDK 中。

## <a name="createschemarowset"></a> Idbschemarowsetimpl:: Createschemarowset

对模板参数指定的对象实现 COM 对象创建程序函数。

### <a name="syntax"></a>语法

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[in]为外部[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)聚合，否则为 NULL 时。

*cRestrictions*<br/>
[in] 要应用于架构行集的限制的计数。

*rgRestrictions*<br/>
[in]一个数组`cRestrictions`**变体**要应用于行集。

*riid*<br/>
[in]接口[QueryInterface](../../atl/queryinterface.md)的输出`IUnknown`。

*cPropertySets*<br/>
[in] 要设置的属性集数目。

*rgPropertySets*<br/>
[in] 指定要设置的属性的 [DBPROPSET](/previous-versions/windows/desktop/ms714367) 结构的数组。

*ppRowset*<br/>
[out]传出`IUnknown`请求*riid*。 这`IUnknown`是架构行集对象上的接口。

*pSchemaRowset*<br/>
[out] 指向架构行集类的实例的指针。 通常不使用此参数，但如果你在将架构行集交给 COM 对象前必须在其上进行较多工作，则可使用此参数。 生存期*pSchemaRowset*受*ppRowset*。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此函数对所有类型的架构行集实现泛型创建程序。 通常情况下，用户不调用此函数。 它由架构映射的实现调用。

## <a name="setrestrictions"></a> Idbschemarowsetimpl:: Setrestrictions

指定在特定架构行集上支持哪些限制。

### <a name="syntax"></a>语法

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>参数

*cRestrictions*<br/>
[in]中的限制数目*rgRestrictions*数组和中的 Guid 数目*rguidSchema*数组。

*rguidSchema*<br/>
[in] 要为其提取限制的架构行集的 GUID 数组。 每个数组元素均包含一个架构行集的 GUID（例如， `DBSCHEMA_TABLES`）。

*rgRestrictions*<br/>
[in] 要设置的限制值的长度 *cRestrictions* 数组。 各元素对应于由 GUID 标识的架构行集上的限制。 如果某个架构行集不受提供程序支持，则该元素设置为零。 否则， **ULONG** 值将包含一个表示该架构行集上支持的限制的位掩码。 有关相对应的限制为特定架构行集的详细信息，请查阅上表的架构行集 Guid 中[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程序员参考*在 Windows 中SDK。

### <a name="remarks"></a>备注

`IDBSchemaRowset`对象调用`SetRestrictions`来确定哪些限制支持上的特定架构行集 (它由调用[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)通过一个向上转换的指针)。 限制允许使用者只提取匹配行（例如，查找表“MyTable”中的所有列）。 限制是可选的，如果不支持任何限制（默认设置），则始终返回所有数据。

此方法的默认实现设置*rgRestrictions*数组为 0 的元素。 在会话类中重写默认设置，以设置默认限制以外的限制。

有关实现架构行集支持的信息，请参阅 [支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。

有关支持架构行集的提供程序的示例，请参阅 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 示例。

有关架构行集的详细信息，请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程序员参考*Windows SDK 中。

## <a name="getrowset"></a> Idbschemarowsetimpl:: Getrowset

返回架构行集。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[in]为外部`IUnknown`时聚合; 否则为 NULL。

*rguidSchema*<br/>
[in] 对所请求架构行集 GUID（例如， `DBSCHEMA_TABLES`）的引用。

*cRestrictions*<br/>
[in] 要应用于行集的限制计数。

*rgRestrictions*<br/>
[in] 一个表示限制的 `cRestrictions`**VARIANT**数组。

*riid*<br/>
[in] 新建架构行集请求的 IID。

*cPropertySets*<br/>
[in] 要设置的属性集数目。

*rgPropertySets*<br/>
[in/out] 要在新建架构行集上设置的 [DBPROPSET](/previous-versions/windows/desktop/ms714367) 结构数组。

*ppRowset*<br/>
[out] 一个指针，指向新建架构行集上所请求的接口。

### <a name="remarks"></a>备注

此方法要求用户在会话类中有架构映射。 使用架构映射信息，`GetRowset`创建一个给定行集对象，如果*rguidSchema*参数等于其中一个映射条目 Guid。 有关映射条目的描述，请参阅 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) 。

请参阅[idbschemarowset:: Getrowset](/previous-versions/windows/desktop/ms722634) Windows SDK 中。

## <a name="getschemas"></a> Idbschemarowsetimpl:: Getschemas

返回可由 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)访问的架构行集的列表。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>参数

*pcSchemas*<br/>
[out] 一个指针，指向使用架构数目填充的 **ULONG** 。

*prgSchemas*<br/>
[out] 一个指向 GUID 数组的指针，该数组用指向架构行集 GUID 数组的指针填充。

*prgRest*<br/>
[out] 一个指针，指向要使用限制数组填充的 **ULONG**数组。

### <a name="remarks"></a>备注

此方法返回提供程序支持的所有架构行集的数组。 请参阅[idbschemarowset:: Getschemas](/previous-versions/windows/desktop/ms719605) Windows SDK 中。

若要实现此函数，用户在会话类中必须有架构映射。 然后，该函数会利用架构映射信息，使用映射中架构的 GUID 数组进行响应。 这表示提供程序支持的架构。

## <a name="see-also"></a>请参阅

[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[支持架构行集](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)