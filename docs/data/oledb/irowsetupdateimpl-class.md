---
title: IRowsetUpdateImpl 类
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370751"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 类

[IRowset 更新](/previous-versions/windows/desktop/ms714401(v=vs.85))接口的 OLE 数据库模板实现。

## <a name="syntax"></a>语法

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>参数

*T*<br/>
派生自`IRowsetUpdateImpl`的类。

*存储*<br/>
用户记录。

*更新阵列*<br/>
包含用于更新行集的缓存数据的数组。

*行类*<br/>
的`HROW`存储单元。

*地图类*<br/>
提供程序持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods-used-with-irowsetchange"></a>接口方法（与 IRowsetChange 一起使用）

|||
|-|-|
|[设置数据](#setdata)|在一个或多个列中设置数据值。|

### <a name="interface-methods-used-with-irowsetupdate"></a>接口方法（与 IRowset 更新一起使用）

|||
|-|-|
|[获取原始数据](#getoriginaldata)|获取最近传输到数据源或从数据源获取的数据，而忽略挂起的更改。|
|[获取挂起的行](#getpendingrows)|返回具有挂起更改的行的列表。|
|[获取罗维状态](#getrowstatus)|返回指定行的状态。|
|[撤消](#undo)|撤消自上次提取或更新以来对行的任何更改。|
|[更新](#update)|传输自上次提取或更新以来对行所做的任何更改。|

### <a name="implementation-methods-callback"></a>实现方法（回拨）

|||
|-|-|
|[已更新允许](#isupdateallowed)|用于在允许更新之前检查安全性、完整性等。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|包含延迟操作的原始数据。|

## <a name="remarks"></a>备注

您应该首先阅读并理解[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))的文档，因为此处描述的所有内容也适用于此处。 您还应阅读 OLE DB 程序员关于设置数据的*参考的第*6 章。

`IRowsetUpdateImpl`实现 OLE `IRowsetUpdate` DB 接口，使使用者能够延迟对`IRowsetChange`数据源所做的更改的传输，并在传输之前撤消更改。

> [!IMPORTANT]
> 强烈建议您在尝试实现提供程序之前阅读以下文档：

- [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB*程序员参考*第 6 章

- 另请参阅在`RUpdateRowset`[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例中如何使用类

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowset 更新：：集数据

在一个或多个列中设置数据值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>参数

请参阅[IRowset 更改：在](/previous-versions/windows/desktop/ms721232(v=vs.85)) *OLE DB 程序员参考*中设置数据。

### <a name="remarks"></a>备注

此方法重写[IRowsetChangeImpl：setData](../../data/oledb/irowsetchangeimpl-setdata.md)方法，但包括原始数据的缓存，以允许立即或延迟处理操作。

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowset 更新：：获取原始数据

获取最近传输到数据源或从数据源获取的数据，而忽略挂起的更改。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>参数

请参阅[IRowset 更新：在](/previous-versions/windows/desktop/ms709947(v=vs.85))OLE *DB 程序员的参考*中获取原始数据。

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowset 更新：：获取待定行

返回具有挂起更改的行的列表。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>参数

*h保留*<br/>
[在]对应于 IRowset 更新中的*h 章节*参数[：：获取挂起的行。](/previous-versions/windows/desktop/ms719626(v=vs.85))

有关其他参数，请参阅[IRowset 更新：：在](/previous-versions/windows/desktop/ms719626(v=vs.85))OLE *DB 程序员的参考*中获取待定行。

### <a name="remarks"></a>备注

有关详细信息，请参阅[IRowset 更新：在](/previous-versions/windows/desktop/ms719626(v=vs.85))OLE DB*程序员的参考*中获取待定行。

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowset 更新：：获取行罗状态

返回指定行的状态。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>参数

*h保留*<br/>
[在]对应于 IRowset 更新中的*h 章*参数[：getRow 状态](/previous-versions/windows/desktop/ms724377(v=vs.85))。

有关其他参数，请参阅[IRowset 更新：在](/previous-versions/windows/desktop/ms724377(v=vs.85)) *OLE DB 程序员的参考*中获取罗维状态。

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowset 更新：：撤消

撤消自上次提取或更新以来对行的任何更改。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>参数

*h保留*<br/>
[在]对应于[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*h 章*参数：：撤消 。

*pcRowsUndone*<br/>
[出]对应于[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*pcRows*参数：：撤消 。

*prgRowsUndone*<br/>
[在]对应于[IRowsetUpdate](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*prgRows*参数：：撤消 。

有关其他参数，请参阅[IRowsetUpdate：：](/previous-versions/windows/desktop/ms719655(v=vs.85))在 OLE *DB 程序员的参考*中撤消。

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowset 更新：：更新

传输自上次提取或更新以来对行所做的任何更改。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>参数

*h保留*<br/>
[在]对应于 IRowset 更新中的*h 章*参数[：：更新](/previous-versions/windows/desktop/ms719709(v=vs.85))。

有关其他参数，请参阅[IRowsetUpdate：：](/previous-versions/windows/desktop/ms719709(v=vs.85))*在 OLE DB 程序员参考*中更新。

### <a name="remarks"></a>备注

更改通过调用[IRowsetChangeImpl：：flushData](../../data/oledb/irowsetchangeimpl-flushdata.md)传输。 使用者必须调用[CRowset：：更新](../../data/oledb/crowset-update.md)，以便更改生效。 将*prgRow 状态*设置为适当的值，如*OLE DB 程序员参考*中的[行状态](/previous-versions/windows/desktop/ms722752(v=vs.85))中所述。

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowset 更新：：是否已更新允许

重写此方法以在更新之前检查安全性、完整性等。

### <a name="syntax"></a>语法

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>参数

*状态*<br/>
[在]行上挂起操作的状态。

*h罗更新*<br/>
[在]处理用户要更新的行。

*p罗状态*<br/>
[出]状态返回给用户。

### <a name="remarks"></a>备注

如果确定应允许更新，请返回S_OK;否则返回E_FAIL。 如果允许更新，还需要`DBROWSTATUS`在[IRowsetUpdateImpl：：更新](../../data/oledb/irowsetupdateimpl-update.md)到适当的[行状态](/previous-versions/windows/desktop/ms722752(v=vs.85))。

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowset 更新：：m_mapCachedData

包含延迟操作的原始数据的映射。

### <a name="syntax"></a>语法

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>参数

*hRow*<br/>
处理数据的行。

*pData*<br/>
指向要缓存的数据的指针。 数据的类型为*存储*（用户记录类）。 请参阅[IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)中的*存储*模板参数。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)
