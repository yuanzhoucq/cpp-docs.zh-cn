---
title: CBulkRowset 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: e66a183c7bbafa16b3aefea8da1472255b507468
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212118"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 类

使用单个调用检索多个行句柄，以批量方式获取和操作行，以便对数据进行批量处理。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>parameters

*TAccessor*<br/>
一个访问器类。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddRefRows](#addrefrows)|递增引用计数。|
|[CBulkRowset](#cbulkrowset)|构造函数。|
|[MoveFirst](#movefirst)|检索第一行数据，如有必要，执行新的批量提取。|
|[MoveLast](#movelast)|移到最后一行。|
|[MoveNext](#movenext)|检索下一行数据。|
|[MovePrev](#moveprev)|移至前一行。|
|[MoveToBookmark](#movetobookmark)|提取书签所标记的行，或从该书签指定偏移量处的行。|
|[MoveToRatio](#movetoratio)|从行集中的小数位置开始提取行。|
|[ReleaseRows](#releaserows)|将当前行（`m_nCurrentRow`）设置为零并释放所有行。|
|[SetRows](#setrows)|设置通过一个调用检索的行句柄的数目。|

## <a name="example"></a>示例

下面的示例演示如何使用 `CBulkRowset` 类。

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a>CBulkRowset：： AddRefRows

调用[IRowset：： AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85))来递增当前从大容量行集中检索到的所有行的引用计数。

### <a name="syntax"></a>语法

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a>CBulkRowset：： CBulkRowset

创建一个新的 `CBulkRowset` 对象并将默认行数设置为 10。

### <a name="syntax"></a>语法

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a>CBulkRowset：： MoveFirst

检索第一行数据。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a>CBulkRowset：： MoveLast

移到最后一行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a>CBulkRowset：： MoveNext

检索下一行数据。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。 当到达行集的末尾时，将返回 DB_S_ENDOFROWSET。

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a>CBulkRowset：： MovePrev

移至前一行。

### <a name="syntax"></a>语法

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a>CBulkRowset：： MoveToBookmark

提取书签标记的行，或从该书签指定偏移量（*lSkip*）的行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>parameters

*书签*<br/>
[in] 标记要从其提取数据的位置的书签。

*lSkip*<br/>
[in] 从书签到目标行的行数。 如果*lSkip*为零，则提取的第一行是带有书签的行。 如果*lSkip*为1，则提取的第一行是位于书签的行之后的行。 如果*lSkip*为-1，则提取的第一行是位于书签的行前面的行。

### <a name="return-value"></a>返回值

请参阅*OLE DB 程序员参考*中的[IRowset：：：](/previous-versions/windows/desktop/ms716988(v=vs.85))

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a>CBulkRowset：： MoveToRatio

从行集中的小数位置开始提取行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>parameters

*nNumerator*<br/>
中用于确定从中提取数据的小数位置的分子。

*nDenominator*<br/>
中用于确定从中提取数据的分数的分母。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

`MoveToRatio` 根据以下公式大致提取行：

`(nNumerator *  RowsetSize ) / nDenominator`

其中 `RowsetSize` 是行集的大小，以行为单位。 此公式的准确性取决于特定的提供程序。 有关详细信息，请参阅*OLE DB 程序员参考*中的[IRowsetScroll：： GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) 。

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a>CBulkRowset：： ReleaseRows

调用[IRowset：： ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85))以递减当前从大容量行集中检索到的所有行的引用计数。

### <a name="syntax"></a>语法

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a>CBulkRowset：： SetRows

设置每个调用检索的行句柄数量。

### <a name="syntax"></a>语法

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>parameters

nRows<br/>
[in] 行集的新大小（行数）。

### <a name="remarks"></a>备注

如果调用此函数，则它必须在行集之前打开。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
