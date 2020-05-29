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
ms.openlocfilehash: 2b08e0e8f3b5b43f79019c70e3fe32ae9064dee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211115"
---
# <a name="csimplerow-class"></a>CSimpleRow 类

提供行句柄的默认实现，该实现在[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)类中使用。

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
|[AddRefRow](#addrefrow)|向现有的行句柄添加引用数。|
|[比较](#compare)|比较两行，看它们是否引用相同的行实例。|
|[CSimpleRow](#csimplerow)|构造函数。|
|[ReleaseRow](#releaserow)|释放行。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_dwRef](#dwref)|对现有行句柄的引用计数。|
|[m_iRowset](#irowset)|表示游标的行集的索引。|

## <a name="remarks"></a>备注

行句柄以逻辑方式为结果行的唯一标记。 `IRowsetImpl` 将为[IRowsetImpl：： GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)中请求的每一行创建一个新的 `CSimpleRow`。 还可以将 `CSimpleRow` 替换为您自己的行句柄实现，因为它是 `IRowsetImpl`的默认模板参数。 替换此类的唯一要求是让替换类提供接受**长**类型的单个参数的构造函数。

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a>CSimpleRow：： AddRefRow

以线程安全的方式将引用计数添加到现有行句柄。

### <a name="syntax"></a>语法

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a>CSimpleRow：： Compare

比较两行，看它们是否引用相同的行实例。

### <a name="syntax"></a>语法

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>parameters

*pRow*<br/>
一个指向 `CSimpleRow` 对象的指针。

### <a name="return-value"></a>返回值

HRESULT 值通常为 S_OK，指示两行是同一行实例，或 S_FALSE，指示两行不同。 有关其他可能的返回值，请参阅*OLE DB 程序员参考*中的[IRowsetIdentity：： IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 。

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a>CSimpleRow：： CSimpleRow

构造函数。

### <a name="syntax"></a>语法

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>parameters

*iRowsetCur*<br/>
中当前行集的索引。

### <a name="remarks"></a>备注

将[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)设置为*iRowsetCur*。

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a>CSimpleRow：： ReleaseRow

以线程安全的方式发布行。

### <a name="syntax"></a>语法

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a>CSimpleRow：： m_dwRef

对现有行句柄的引用计数。

### <a name="syntax"></a>语法

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a>CSimpleRow：： m_iRowset

表示游标的行集的索引。

### <a name="syntax"></a>语法

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)
