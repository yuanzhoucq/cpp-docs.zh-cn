---
title: CSimpleRow 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: 19b90f4454e784907366ef6cf7e3e7e1b9ada799
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023836"
---
# <a name="csimplerow-class"></a>CSimpleRow 类

提供的行控点，在中使用的默认实现[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)类。

## <a name="syntax"></a>语法

```cpp
class CSimpleRow
```

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRow](#addrefrow)|将引用计数添加到现有的行控点。|
|[比较](#compare)|比较两个行，以查看它们是否引用同一个行实例。|
|[CSimpleRow](#csimplerow)|构造函数。|
|[ReleaseRow](#releaserow)|释放行。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_dwRef](#dwref)|为现有的行句柄的引用计数。|
|[m_iRowset](#irowset)|表示光标的行集的索引。|

## <a name="remarks"></a>备注

行控点在逻辑上就结果行的唯一标记。 `IRowsetImpl` 创建一个新`CSimpleRow`为每个行中请求[irowsetimpl:: Getnextrows](../../data/oledb/irowsetimpl-getnextrows.md)。 `CSimpleRow` 因为它的默认模板自变量也可以使用的行控点，您自己的实现替换`IRowsetImpl`。 到替换此类的唯一要求是能够提供接受类型的单个参数的构造函数替换类**长**。

## <a name="addrefrow"></a> CSimpleRow::AddRefRow

将引用计数添加到现有的行控点，以线程安全的方式。

### <a name="syntax"></a>语法

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a> CSimpleRow::Compare

比较两个行，以查看它们是否引用同一个行实例。

### <a name="syntax"></a>语法

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>参数

*pRow*<br/>
指向 `CSimpleRow` 对象的指针。

### <a name="return-value"></a>返回值

HRESULT 值，通常为 S_OK，指示两个行是相同的行实例，或 S_FALSE，指示两个行都不同。 请参阅[IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85))中*OLE DB 程序员参考*有关其他可能的返回值。

## <a name="csimplerow"></a> Csimplerow:: Csimplerow

构造函数。

### <a name="syntax"></a>语法

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>参数

*iRowsetCur*<br/>
[in]当前行集的索引。

### <a name="remarks"></a>备注

集[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)到*iRowsetCur*。

## <a name="releaserow"></a> CSimpleRow::ReleaseRow

释放行以线程安全的方式。

### <a name="syntax"></a>语法

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a> CSimpleRow::m_dwRef

为现有的行句柄的引用计数。

### <a name="syntax"></a>语法

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a> CSimpleRow::m_iRowset

表示光标的行集的索引。

### <a name="syntax"></a>语法

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)