---
title: IRowsetLocateImpl 类
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: 06e860425215d9fde268b780c001301b14a1caa1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210426"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 类

实现 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))接口，该接口从行集中提取任意行。

## <a name="syntax"></a>语法

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetLocateImpl`的类。

*RowsetInterface*<br/>
派生自 `IRowsetImpl`的类。

*RowClass*<br/>
`HROW`的存储单元。

*MapClass*<br/>
提供程序所持有的所有行句柄的存储单元。

*BookmarkKeyType*<br/>
书签的类型，如 LONG 或 string。 普通书签的长度必须至少为两个字节。 （为 OLE DB[标准书签](/previous-versions/windows/desktop/ms712954(v=vs.85))保留单字节长度`DBBMK_FIRST`、`DBBMK_LAST`和 `DBBMK_INVALID`。）

*BookmarkType*<br/>
用于维护书签到数据关系的映射机制。

*BookmarkMapClass*<br/>
书签所持有的所有行句柄的存储单元。

## <a name="requirements"></a>要求

**标头**：为 atldb。h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[比较](#compare)|比较两个书签。|
|[GetRowsAt](#getrowsat)|从书签的偏移量指定的行开始提取行。|
|[GetRowsByBookmark](#getrowsbybookmark)|提取与指定书签匹配的行。|
|[哈希](#hash)|返回指定书签的哈希值。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|书签的数组。|

## <a name="remarks"></a>备注

`IRowsetLocateImpl` 是[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))接口的 OLE DB 模板实现。 `IRowsetLocate` 用于从行集中提取任意行。 不实现此接口的行集是 `sequential` 行集。 当行集上存在 `IRowsetLocate` 时，列0是行的书签;读取此列将获取可用于重新定位到相同行的书签值。

`IRowsetLocateImpl` 用于在提供程序中实现书签支持。 书签是占位符（行集上的索引），可让使用者快速返回到行，从而实现数据的高速访问。 提供程序确定哪些书签可以唯一地标识行。 使用 `IRowsetLocateImpl` 方法，你可以比较书签、按偏移量提取行、按书签提取行并返回书签的哈希值。

若要支持在行集中 OLE DB 书签，请将行集继承此类。

有关实现书签支持的信息，请参阅适用于*Visual C++程序员指南*中的[书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)和平台 SDK 中*OLE DB 程序员参考*中的[书签](/previous-versions/windows/desktop/ms709728(v=vs.85))。

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a>IRowsetLocateImpl：： Compare

比较两个书签。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetLocate：： Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) 。

### <a name="remarks"></a>备注

书签都可以是标准的 OLE DB 定义的[标准书签](/previous-versions/windows/desktop/ms712954(v=vs.85))（`DBBMK_FIRST`、`DBBMK_LAST`或 `DBBMK_INVALID`）。 在 `pComparison` 中返回的值表示两个书签之间的关系：

- DBCOMPARE_LT （`cbBookmark1` 在 `cbBookmark2`之前。）

- DBCOMPARE_EQ （`cbBookmark1` 等于 `cbBookmark2`。）

- DBCOMPARE_GT （`cbBookmark1` 在 `cbBookmark2`之后。）

- DBCOMPARE_NE （书签相等且未排序。）

- DBCOMPARE_NOTCOMPARABLE （无法比较书签。）

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a>IRowsetLocateImpl：： GetRowsAt

从书签的偏移量指定的行开始提取行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetLocate：： GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) 。

### <a name="remarks"></a>备注

若要改为从游标位置提取，请使用[IRowset：： GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85))。

`IRowsetLocateImpl::GetRowsAt` 不会更改光标位置。

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a>IRowsetLocateImpl：： GetRowsByBookmark

获取一个或多个与指定书签匹配的行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetLocate：： GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85))的*hChapter*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetLocate：： GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) 。

### <a name="remarks"></a>备注

书签可以是你定义的值，也可以是 OLE DB[标准书签](/previous-versions/windows/desktop/ms712954(v=vs.85))（`DBBMK_FIRST` 或 `DBBMK_LAST`）。 不会更改光标位置。

## <a name="irowsetlocateimplhash"></a><a name="hash"></a>IRowsetLocateImpl：： Hash

返回指定书签的哈希值。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>parameters

*hReserved*<br/>
中对应于[IRowsetLocate：： Hash](/previous-versions/windows/desktop/ms709697(v=vs.85))的*hChapter*参数。

有关其他参数，请参阅*OLE DB 程序员参考*中的[IRowsetLocate：： Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) 。

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a>IRowsetLocateImpl：： m_rgBookmarks

书签的数组。

### <a name="syntax"></a>语法

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate： IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85))
[提供程序支持书签](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[书签](/previous-versions/windows/desktop/ms709728(v=vs.85))
