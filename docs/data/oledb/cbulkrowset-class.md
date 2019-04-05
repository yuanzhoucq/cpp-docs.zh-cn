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
- AddRefRows
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
- CBulkRowset
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
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
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
ms.openlocfilehash: ba6b41a708cd854e398cbaa80609472ebbe167e8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023225"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 类

提取和操作将通过检索一次调用多个行句柄中大容量的数据处理的行。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>参数

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
|[MoveFirst](#movefirst)|检索数据、 执行新的大容量提取必要的第一行。|
|[MoveLast](#movelast)|将移动到最后一个行。|
|[MoveNext](#movenext)|检索下的一行数据。|
|[MovePrev](#moveprev)|移动到上一行。|
|[MoveToBookmark](#movetobookmark)|从该书签提取用书签标记的行或指定的偏移量处的行。|
|[MoveToRatio](#movetoratio)|提取从行集中的小数位置开始的行。|
|[ReleaseRows](#releaserows)|设置当前行 (`m_nCurrentRow`) 为零，并发布的所有行。|
|[SetRows](#setrows)|设置一次调用要检索的行句柄数。|

## <a name="example"></a>示例

下面的示例说明如何使用`CBulkRowset`类。

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a> CBulkRowset::AddRefRows

调用[irowset:: Addrefrows](/previous-versions/windows/desktop/ms719619(v=vs.85))来增加当前从 bulk 行集检索到的所有行的引用计数。

### <a name="syntax"></a>语法

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset

创建一个新的 `CBulkRowset` 对象并将默认行数设置为 10。

### <a name="syntax"></a>语法

```cpp
CBulkRowset();
```

## <a name="movefirst"></a> CBulkRowset::MoveFirst

检索数据的第一行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="movelast"></a> CBulkRowset::MoveLast

将移动到最后一个行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="movenext"></a> CBulkRowset::MoveNext

检索下的一行数据。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。 当已达到行集末尾时，返回 DB_S_ENDOFROWSET。

## <a name="moveprev"></a> CBulkRowset::MovePrev

移动到上一行。

### <a name="syntax"></a>语法

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark

提取标记的书签或指定的偏移量处的行的行 (*lSkip*) 从该书签。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>参数

*bookmark（书签）*<br/>
[in] 标记要从其提取数据的位置的书签。

*lSkip*<br/>
[in] 从书签到目标行的行数。 如果*lSkip*为零，则提取的第一行是书签的行。 如果*lSkip*为 1，提取的第一行是标有书签的行后的行。 如果*lSkip*为-1，提取的第一行是标有书签的行前的行。

### <a name="return-value"></a>返回值

请参阅[irowset:: Getdata](/previous-versions/windows/desktop/ms716988(v=vs.85))中*OLE DB 程序员参考*。

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio

提取从行集中的小数位置开始的行。

### <a name="syntax"></a>语法

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>参数

*nNumerator*<br/>
[in]用于确定从其提取数据的小数位置分子。

*nDenominator*<br/>
[in]用于确定从其提取数据的小数位置分母。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

`MoveToRatio` 提取大致依据的公式如下行：

`(nNumerator *  RowsetSize ) / nDenominator`

其中`RowsetSize`是行集，以行为单位的大小。 此公式的准确性取决于特定的提供程序。 有关详细信息，请参阅[irowsetscroll:: Getrowsatratio](/previous-versions/windows/desktop/ms709602(v=vs.85))中*OLE DB 程序员参考*。

## <a name="releaserows"></a> CBulkRowset::ReleaseRows

调用[irowset:: Releaserows](/previous-versions/windows/desktop/ms719771(v=vs.85))要递减当前从 bulk 行集检索到的所有行的引用计数。

### <a name="syntax"></a>语法

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="setrows"></a> CBulkRowset::SetRows

设置每个调用检索的行句柄数量。

### <a name="syntax"></a>语法

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>参数

*nRows*<br/>
[in] 行集的新大小（行数）。

### <a name="remarks"></a>备注

如果调用此函数，则它必须在行集之前打开。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)