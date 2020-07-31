---
title: IRowsetImpl 类
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: f440bb891c30033962208c3e89648bd05ba3f81b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232139"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl 类

提供 `IRowset` 接口的实现。

## <a name="syntax"></a>语法

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>参数

*T*<br/>
派生自的类 `IRowsetImpl` 。

*RowsetInterface*<br/>
派生自的类 `IRowsetImpl` 。

*RowClass*<br/>
的存储单元 `HROW` 。

*MapClass*<br/>
提供程序所持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRows](#addrefrows)|向现有的行句柄添加引用数。|
|[CreateRow](#createrow)|由[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)调用，用于分配新的 `HROW` 。 不是由用户直接调用。|
|[GetData](#getdata)|从行的行集合副本中检索数据。|
|[GetDBStatus](#getdbstatus)|返回指定字段的状态。|
|[GetNextRows](#getnextrows)|按顺序获取行，同时记住以前的位置。|
|[IRowsetImpl](#irowsetimpl)|构造函数。 不是由用户直接调用。|
|[RefRows](#refrows)|由[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)调用。 不是由用户直接调用。|
|[ReleaseRows](#releaserows)|释放行。|
|[RestartPosition](#restartposition)|将下一个提取位置重新定位到其初始位置;也就是说，它是首次创建行集时的位置。|
|[SetDBStatus](#setdbstatus)|设置指定字段的状态标志。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|指示提供程序是否支持向后提取。|
|[m_bCanScrollBack](#bcanscrollback)|指示提供程序是否可以让其游标向后滚动。|
|[m_bReset](#breset)|指示提供程序是否重置其游标位置。 这在[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)中向后滚动或向后翻时具有特殊意义。|
|[m_iRowset](#irowset)|行集的索引，表示游标。|
|[m_rgRowHandles](#rgrowhandles)|行句柄的列表。|

## <a name="remarks"></a>备注

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))是基行集接口。

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a>IRowsetImpl：： AddRefRows

向现有的行句柄添加引用数。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 。

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a>IRowsetImpl：： CreateRow

[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)调用的帮助器方法，用于分配新的 `HROW` 。

### <a name="syntax"></a>语法

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>参数

*lRowsOffset*<br/>
要创建的行的游标位置。

*cRowsObtained*<br/>
一个引用，该引用传递回指示创建的行数的用户。

*rgRows*<br/>
`HROW`使用新创建的行句柄返回到调用方的的数组。

### <a name="remarks"></a>备注

如果该行存在，此方法将调用[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)并返回。 否则，它将分配 RowClass 模板变量的新实例，并将其添加到[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。

## <a name="irowsetimplgetdata"></a><a name="getdata"></a>IRowsetImpl：：

从行的行集合副本中检索数据。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：：：](/previous-versions/windows/desktop/ms716988(v=vs.85))

一些参数对应于不同名称*OLE DB 程序员引用*参数，如中所述 `IRowset::GetData` ：

|OLE DB 模板参数|*OLE DB 程序员引用*参数|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>备注

还使用 OLE DB 数据转换 DLL 处理数据转换。

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a>IRowsetImpl：： GetDBStatus

返回指定字段的 DBSTATUS 状态标志。

### <a name="syntax"></a>语法

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>参数

*currentRow*<br/>
中当前行。

columnNames**<br/>
中正在为其请求状态的列。

### <a name="return-value"></a>返回值

列的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))标志。

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a>IRowsetImpl：： GetNextRows

按顺序获取行，同时记住以前的位置。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：： GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) 。

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a>IRowsetImpl：： IRowsetImpl

构造函数。

### <a name="syntax"></a>语法

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>备注

通常不需要直接调用此方法。

## <a name="irowsetimplrefrows"></a><a name="refrows"></a>IRowsetImpl：： RefRows

由[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)调用，以增加或释放对现有行句柄的引用计数。

### <a name="syntax"></a>语法

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a>IRowsetImpl：： ReleaseRows

释放行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：： ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) 。

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a>IRowsetImpl：： RestartPosition

将下一个提取位置重新定位到其初始位置;也就是说，它是首次创建行集时的位置。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IRowset：： RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) 。

### <a name="remarks"></a>备注

在调用之前，行集位置未定义 `GetNextRow` 。 可以通过调用 `RestartPosition` 并随后提取或向后滚动，在 rowet 中向后移动。

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a>IRowsetImpl：： SetDBStatus

为指定的字段设置 DBSTATUS 状态标志。

### <a name="syntax"></a>语法

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>参数

*statusFlags*<br/>
要为列设置的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))标志。

*currentRow*<br/>
当前行。

*columnInfo*<br/>
正在为其设置状态的列。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

提供程序重写此函数，以便为 DBSTATUS_S_ISNULL 和 DBSTATUS_S_DEFAULT 提供特殊处理。

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a>IRowsetImpl：： m_bCanFetchBack

指示提供程序是否支持向后提取。

### <a name="syntax"></a>语法

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>备注

链接到 `DBPROP_CANFETCHBACKWARDS` 组中的属性 `DBPROPSET_ROWSET` 。 提供程序必须支持 `DBPROP_CANFETCHBACKWARDS` 为 `m_bCanFetchBackwards` **`true`** 。

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a>IRowsetImpl：： m_bCanScrollBack

指示提供程序是否可以让其游标向后滚动。

### <a name="syntax"></a>语法

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>备注

链接到 `DBPROP_CANSCROLLBACKWARDS` 组中的属性 `DBPROPSET_ROWSET` 。 提供程序必须支持 `DBPROP_CANSCROLLBACKWARDS` 为 `m_bCanFetchBackwards` **`true`** 。

## <a name="irowsetimplm_breset"></a><a name="breset"></a>IRowsetImpl：： m_bReset

用于确定游标位置是否在行集上定义的位标志。

### <a name="syntax"></a>语法

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>备注

如果使用者使用[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)负值 `lOffset` 或*cRows*调用 GetNextRows 且 `m_bReset` 为 true，则 `GetNextRows` 移动到行集的末尾。 如果 `m_bReset` 为 false，则使用者将接收错误代码，并符合 OLE DB 规范。 `m_bReset` **`true`** 首次创建行集时，以及当使用者调用[IRowsetImpl：： RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)时，该标志将设置为。 当你调用时，它会设置为 **`false`** `GetNextRows` 。

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a>IRowsetImpl：： m_iRowset

行集的索引，表示游标。

### <a name="syntax"></a>语法

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a>IRowsetImpl：： m_rgRowHandles

提供程序当前包含的行句柄的映射，以响应 `GetNextRows` 。

### <a name="syntax"></a>语法

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>备注

通过调用删除行句柄 `ReleaseRows` 。 有关*MapClass*的定义，请参阅[IRowsetImpl 概述](../../data/oledb/irowsetimpl-class.md)。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow 类](../../data/oledb/csimplerow-class.md)
