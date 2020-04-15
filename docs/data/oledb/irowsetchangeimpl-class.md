---
title: IRowsetChangeImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376949"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 类

OLE DB 模板在 OLE DB 规范中的[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>参数

*T*<br/>
派生自`IRowsetChangeImpl`的类。

*存储*<br/>
用户记录。

*基本接口*<br/>
接口的基类，如`IRowsetChange`。

*行类*<br/>
行句柄的存储单元。

*地图类*<br/>
提供程序持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods-used-with-irowsetchange"></a>接口方法（与 IRowsetChange 一起使用）

|||
|-|-|
|[删除行](#deleterows)|从行集中删除行。|
|[InsertRow](#insertrow)|将行插入行。|
|[设置数据](#setdata)|在一个或多个列中设置数据值。|

### <a name="implementation-method-callback"></a>实现方法（回拨）

|||
|-|-|
|[刷新数据](#flushdata)|由提供程序重写以将数据提交到其存储。|

## <a name="remarks"></a>备注

此接口负责立即写入数据存储。 "立即"是指当最终用户（使用使用者的人）进行任何更改时，这些更改将立即传输到数据存储（并且无法撤消）。

`IRowsetChangeImpl`实现 OLE `IRowsetChange` DB 接口，该接口支持更新现有行中的列值、删除行和插入新行。

OLE 数据库模板实现支持所有基本方法 （`SetData`和`InsertRow`。 `DeleteRows`

> [!IMPORTANT]
> 强烈建议您在尝试实现提供程序之前阅读以下文档：

- [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)

- OLE DB*程序员参考*第 6 章

- 另请参阅在`RUpdateRowset`[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例中如何使用该类。

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChange：:DeleteRows

从行集中删除行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetChange：:DEleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85))在*OLE DB 程序员的参考*中。

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowset 更改：：插入行

在行集中创建和初始化新行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>参数

请参阅[IRowset 更改：在](/previous-versions/windows/desktop/ms716921(v=vs.85)) *OLE DB 程序员参考*中插入行。

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChange：：集数据

在一个或多个列中设置数据值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>参数

请参阅[IRowset 更改：在](/previous-versions/windows/desktop/ms721232(v=vs.85)) *OLE DB 程序员参考*中设置数据。

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChange：：FlushData

由提供程序重写以将数据提交到其存储。

### <a name="syntax"></a>语法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>参数

*h罗托弗什*<br/>
[在]处理数据的行。 此行的类型是从`IRowsetImpl`类`CSimpleRow`的*RowClass*模板参数（默认情况下）确定的。

*h访问器*<br/>
[在]句柄访问器，其中包含绑定信息和键入其`PROVIDER_MAP`中的信息（请参阅[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)）。

### <a name="return-value"></a>返回值

标准 HRESULT。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
