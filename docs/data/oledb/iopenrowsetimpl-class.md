---
title: IOpenRowsetImpl 类
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545905"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 类

提供 `IOpenRowset` 接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>parameters

*SessionClass*<br/>
派生自 `IOpenRowsetImpl`的类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CreateRowset](#createrowset)|创建行集对象。 不是由用户直接调用。|
|[OpenRowset](#openrowset)|打开并返回一个行集，其中包括单个基表或索引中的所有行。 （不在为 ATLDB.H 中。高|

## <a name="remarks"></a>备注

对于 session 对象， [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))接口是必需的。 它将打开并返回一个行集，其中包括单个基表或索引中的所有行。

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a>IOpenRowsetImpl：： CreateRowset

创建行集对象。 不是由用户直接调用。 请参阅*OLE DB 程序员参考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

### <a name="syntax"></a>语法

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>parameters

*RowsetClass*<br/>
表示用户的行集类的模板类成员。 通常由向导生成。

*pRowsetObj*<br/>
弄指向行集对象的指针。 通常不使用此参数，但如果必须在将其传递给 COM 对象之前对行集执行更多工作，则可以使用此参数。 *PRowsetObj*的生存期由*ppRowset*绑定。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a>IOpenRowsetImpl：： OpenRowset

打开并返回一个行集，其中包括单个基表或索引中的所有行。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

### <a name="remarks"></a>备注

在为 ATLDB.H 中找不到此方法。高. 它是在创建提供程序时由 ATL 对象向导创建的。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)