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
- SetData
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
ms.openlocfilehash: dacf9de0835108ae946e7523472a0adf12e7e222
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556720"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 类

OLE DB 模板实现[IRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715790(v=vs.85)) OLE DB 规范中的接口。

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
一个类派生自`IRowsetChangeImpl`。

*存储*<br/>
用户记录中。

*BaseInterface*<br/>
基类接口，如`IRowsetChange`。

*RowClass*<br/>
行句柄存储单元。

*MapClass*<br/>
持有的提供程序的所有行句柄存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods-used-with-irowsetchange"></a>接口方法 （用于 IRowsetChange）

|||
|-|-|
|[DeleteRows](#deleterows)|删除行集中的行。|
|[InsertRow](#insertrow)|将行插入到行集中。|
|[SetData](#setdata)|设置一个或多个列中的数据值。|

### <a name="implementation-method-callback"></a>实现方法 （回调）

|||
|-|-|
|[FlushData](#flushdata)|要将数据提交到其存储区提供程序的入口。|

## <a name="remarks"></a>备注

此接口是负责向数据存储区直接写入操作。 "即时"意味着，当最终用户 （使用使用者的人员） 进行任何更改，这些更改立即传输到数据存储 （并不能撤消）。

`IRowsetChangeImpl` 实现 OLE DB`IRowsetChange`接口，可更新的现有行，删除行，并将插入新行中列的值。

OLE DB 模板实现支持所有基方法 (`SetData`， `InsertRow`，和`DeleteRows`)。

> [!IMPORTANT]
>  强烈建议您阅读以下文档，再尝试实现您的提供程序：

- [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)

- 第 6 章*OLE DB 程序员参考*

- 另请参阅如何`RUpdateRowset`中使用类[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例。

## <a name="deleterows"></a> Irowsetchangeimpl:: Deleterows

删除行集中的行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetChange::DeleteRows](https://docs.microsoft.com/previous-versions/windows/desktop/ms724362(v=vs.85)(v%3dvs.85))中*OLE DB 程序员参考*。

## <a name="insertrow"></a> Irowsetchangeimpl:: Insertrow

创建并初始化新行集中的一行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>参数

请参阅[irowsetchange:: Insertrow](https://docs.microsoft.com/previous-versions/windows/desktop/ms716921(v=vs.85))中*OLE DB 程序员参考*。

## <a name="setdata"></a> Irowsetchangeimpl:: Setdata

设置一个或多个列中的数据值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>参数

请参阅[irowsetchange:: Setdata](https://docs.microsoft.com/previous-versions/windows/desktop/ms721232(v=vs.85))中*OLE DB 程序员参考*。

## <a name="flushdata"></a> Irowsetchangeimpl:: Flushdata

要将数据提交到其存储区提供程序的入口。

### <a name="syntax"></a>语法

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>参数

*hRowToFlush*<br/>
[in]数据行的句柄。 此行的类型由*RowClass*的模板参数`IRowsetImpl`类 (`CSimpleRow`默认情况下)。

*hAccessorToFlush*<br/>
[in]句柄的访问器，其中包含绑定信息和类型信息在其`PROVIDER_MAP`(请参阅[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md))。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)