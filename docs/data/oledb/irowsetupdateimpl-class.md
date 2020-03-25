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
ms.openlocfilehash: 79d85e7d1c849bcaa7c2aa1b3f6d9d50a20d1b2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210309"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 类

[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))接口的 OLE DB 模板实现。

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

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetUpdateImpl`的类。

*存储*<br/>
用户记录。

*UpdateArray*<br/>
一个数组，其中包含用于更新行集的缓存数据。

*RowClass*<br/>
`HROW`的存储单元。

*MapClass*<br/>
提供程序所持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods-used-with-irowsetchange"></a>接口方法（与 IRowsetChange 一起使用）

|||
|-|-|
|[SetData](#setdata)|设置一个或多个列中的数据值。|

### <a name="interface-methods-used-with-irowsetupdate"></a>接口方法（与 IRowsetUpdate 一起使用）

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|获取最近传输到数据源或从数据源获取的数据，忽略挂起的更改。|
|[GetPendingRows](#getpendingrows)|返回具有挂起更改的行的列表。|
|[GetRowStatus](#getrowstatus)|返回指定行的状态。|
|[撤消](#undo)|撤消上次提取或更新后对行所做的任何更改。|
|[Update](#update)|传输自上次提取或更新以来对行所做的任何更改。|

### <a name="implementation-methods-callback"></a>实现方法（回调）

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|用于在允许更新之前检查安全性、完整性等。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|包含延迟操作的原始数据。|

## <a name="remarks"></a>备注

你应该首先阅读并了解有关[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))的文档，因为此处所述的所有内容也都适用。 还应阅读有关设置数据的*OLE DB 程序员参考*的第6章。

`IRowsetUpdateImpl` 实现 OLE DB `IRowsetUpdate` 接口，使用者可使使用者延迟向数据源所 `IRowsetChange` 做的更改的传输，并在传输前撤消更改。

> [!IMPORTANT]
>  强烈建议在尝试实现提供程序之前先阅读以下文档：

- [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)

- *OLE DB 程序员参考*的第6章

- 另请参阅[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例中如何使用 `RUpdateRowset` 类

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl：： SetData

设置一个或多个列中的数据值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetChange：： SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 。

### <a name="remarks"></a>备注

此方法重写[IRowsetChangeImpl：： SetData](../../data/oledb/irowsetchangeimpl-setdata.md)方法，但包括对原始数据进行缓存，以允许立即或延迟处理操作。

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl：： GetOriginalData

获取最近传输到数据源或从数据源获取的数据，忽略挂起的更改。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) 。

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl：： GetPendingRows

返回具有挂起更改的行的列表。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85))中的*hChapter*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 。

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) 。

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl：： GetRowStatus

返回指定行的状态。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetUpdate：： GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85))中的*hChapter*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) 。

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl：： Undo

撤消上次提取或更新后对行所做的任何更改。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*hChapter*参数。

*pcRowsUndone*<br/>
弄对应于[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*pcRows*参数。

*prgRowsUndone*<br/>
中对应于[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85))中的*prgRows*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) 。

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl：： Update

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

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetUpdate：： Update](/previous-versions/windows/desktop/ms719709(v=vs.85))中的*hChapter*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetUpdate：： Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) 。

### <a name="remarks"></a>备注

通过调用[IRowsetChangeImpl：： FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)传输更改。 使用者必须调用[CRowset：： Update](../../data/oledb/crowset-update.md)才能使所做的更改生效。 将*prgRowstatus*设置为相应的值，如*OLE DB 程序员参考*中的[行状态](/previous-versions/windows/desktop/ms722752(v=vs.85))中所述。

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl：： IsUpdateAllowed

重写此方法以在更新之前检查安全性、完整性等。

### <a name="syntax"></a>语法

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>parameters

*status*<br/>
中对行的挂起操作的状态。

*hRowUpdate*<br/>
中用户要更新的行的句柄。

*pRowStatus*<br/>
弄返回给用户的状态。

### <a name="remarks"></a>备注

如果确定应该允许更新，则返回 S_OK;否则，将返回 E_FAIL。 如果允许更新，还需要将[IRowsetUpdateImpl：： update](../../data/oledb/irowsetupdateimpl-update.md)中的 `DBROWSTATUS` 设置为相应的[行状态](/previous-versions/windows/desktop/ms722752(v=vs.85))。

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl：： m_mapCachedData

包含延迟操作的原始数据的映射。

### <a name="syntax"></a>语法

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>parameters

*hRow*<br/>
数据行的句柄。

*pData*<br/>
指向要缓存的数据的指针。 数据的类型为*存储*（用户记录类）。 请参阅[IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)中的*存储*模板参数。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)
