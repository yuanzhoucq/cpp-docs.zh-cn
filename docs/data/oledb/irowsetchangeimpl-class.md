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
ms.openlocfilehash: b069cd08814855a0528806ac6d19ed8f5beb6f37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210452"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 类

OLE DB 规范中[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))接口的 OLE DB 模板实现。

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

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetChangeImpl`的类。

*存储*<br/>
用户记录。

*BaseInterface*<br/>
接口的基类，如 `IRowsetChange`。

*RowClass*<br/>
行句柄的存储单元。

*MapClass*<br/>
提供程序所持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods-used-with-irowsetchange"></a>接口方法（与 IRowsetChange 一起使用）

|||
|-|-|
|[DeleteRows](#deleterows)|删除行集中的行。|
|[InsertRow](#insertrow)|向行集中插入行。|
|[SetData](#setdata)|设置一个或多个列中的数据值。|

### <a name="implementation-method-callback"></a>实现方法（回调）

|||
|-|-|
|[FlushData](#flushdata)|由提供程序重写，以将数据提交到其存储区。|

## <a name="remarks"></a>备注

此接口负责向数据存储区进行立即写入操作。 "即时" 表示当最终用户（使用使用者的人员）进行了任何更改时，这些更改将立即传输到数据存储区（不能撤消）。

`IRowsetChangeImpl` 实现了 OLE DB `IRowsetChange` 接口，该接口允许更新现有行中列的值、删除行和插入新行。

OLE DB 模板实现支持所有基方法（`SetData`、`InsertRow`和 `DeleteRows`）。

> [!IMPORTANT]
>  强烈建议在尝试实现提供程序之前先阅读以下文档：

- [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)

- *OLE DB 程序员参考*的第6章

- 另请参阅[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例中使用 `RUpdateRowset` 类的方式。

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl：:D eleteRows

删除行集中的行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetChange：:D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) 。

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl：： InsertRow

创建并初始化行集中的新行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetChange：： InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) 。

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl：： SetData

设置一个或多个列中的数据值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetChange：： SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) 。

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl：： FlushData

由提供程序重写，以将数据提交到其存储区。

### <a name="syntax"></a>语法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>parameters

*hRowToFlush*<br/>
中数据行的句柄。 此行的类型由 `IRowsetImpl` 类（默认`CSimpleRow`）的*RowClass*模板自变量确定。

*hAccessorToFlush*<br/>
中访问器的句柄，其中包含绑定信息和 `PROVIDER_MAP` 中的类型信息（请参见[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)）。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
