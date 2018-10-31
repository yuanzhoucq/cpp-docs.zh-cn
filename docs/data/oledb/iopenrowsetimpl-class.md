---
title: IOpenRowsetImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72ca35ad6f2246a517c8a8d103c1a7f37e142534
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063427"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 类

提供了实现`IOpenRowset`接口。

## <a name="syntax"></a>语法

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>参数

*SessionClass*<br/>
您的类，派生自`IOpenRowsetImpl`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CreateRowset](#createrowset)|创建一个行集对象。 不直接由用户调用。|
|[OpenRowset](#openrowset)|打开并返回包含来自单个基表或索引的所有行的行集。 （不在 ATLDB。H)|

## <a name="remarks"></a>备注

[IOpenRowset](/previous-versions/windows/desktop/ms716946)接口是必需的会话对象。 打开，并返回包含来自单个基表或索引的所有行的行集。

## <a name="createrowset"></a> Iopenrowsetimpl:: Createrowset

创建一个行集对象。 不直接由用户调用。 请参阅[iopenrowset:: Openrowset](/previous-versions/windows/desktop/ms716724)中*OLE DB 程序员参考。*

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

#### <a name="parameters"></a>参数

*RowsetClass*<br/>
模板类成员表示用户的行集类。 通常由向导生成。

*pRowsetObj*<br/>
[out]指向行集对象的指针。 通常不使用此参数，但如果必须传递给 COM 对象之前在行集上执行更多的工作，可以使用它。 生存期*pRowsetObj*受*ppRowset*。

其他参数，请参阅[iopenrowset:: Openrowset](/previous-versions/windows/desktop/ms716724)中*OLE DB 程序员参考。*

## <a name="openrowset"></a> Iopenrowsetimpl:: Openrowset

打开并返回包含来自单个基表或索引的所有行的行集。

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

#### <a name="parameters"></a>参数

请参阅[iopenrowset:: Openrowset](/previous-versions/windows/desktop/ms716724)中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

ATLDB 中找不到此方法。H. 它由 ATL 对象向导时创建提供程序创建。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)