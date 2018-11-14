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
ms.openlocfilehash: e43f9c1761e92120a577f097fb3303a6641f5b5f
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556954"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 类

实现 OLE DB [IRowsetLocate](https://docs.microsoft.com/previous-versions/windows/desktop/ms721190(v=vs.85))接口，从行集提取任意行。

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

### <a name="parameters"></a>参数

*T*<br/>
一个类派生自`IRowsetLocateImpl`。

*RowsetInterface*<br/>
一个类派生自`IRowsetImpl`。

*RowClass*<br/>
为存储单元`HROW`。

*MapClass*<br/>
持有的提供程序的所有行句柄存储单元。

*BookmarkKeyType*<br/>
书签 long 类型的值或字符串之类的类型。 普通的书签必须具有至少两个字节的长度。 (OLE DB 的保留单字节长度[标准书签](https://docs.microsoft.com/previous-versions/windows/desktop/ms712954(v=vs.85))`DBBMK_FIRST`， `DBBMK_LAST`，和`DBBMK_INVALID`。)

*BookmarkType*<br/>
用于维护书签数据关系的映射机制。

*BookmarkMapClass*<br/>
所有持有的书签的行句柄存储单元。

## <a name="requirements"></a>要求

**标头**: atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[Compare](#compare)|比较两个的书签。|
|[GetRowsAt](#getrowsat)|提取从指定的偏移量从书签的行开始的行。|
|[GetRowsByBookmark](#getrowsbybookmark)|提取匹配指定的书签的行。|
|[哈希](#hash)|返回哈希值用于指定书签。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|书签的数组。|

## <a name="remarks"></a>备注

`IRowsetLocateImpl` 是的 OLE DB 模板实现[IRowsetLocate](https://docs.microsoft.com/previous-versions/windows/desktop/ms721190(v=vs.85))接口。 `IRowsetLocate` 用于从行集提取任意行。 不实现此接口的行集是`sequential`行集。 当`IRowsetLocate`存在对行集列 0 进行的书签的行; 阅读本专栏将获得可用于重新定位到同一行的书签值。

`IRowsetLocateImpl` 用于实现提供程序中的书签的支持。 书签是占位符 （索引行集上），使使用者可以快速返回到某一行，允许对数据的高速访问。 提供程序确定书签可以唯一地标识一行。 使用`IRowsetLocateImpl`方法，您可以比较书签、 提取行的偏移量提取行的书签，并返回用于书签的哈希值。

若要在行集中支持 OLE DB 的书签，请从此类继承的行集。

实现书签支持的信息，请参阅[提供程序支持书签](../../data/oledb/provider-support-for-bookmarks.md)中*Visual c + + 程序员指南*并[书签](https://docs.microsoft.com/previous-versions/windows/desktop/ms709728(v=vs.85))中*OLE DB 程序员参考*平台 SDK 中。

## <a name="compare"></a> Irowsetlocateimpl:: Compare

比较两个的书签。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetLocate::Compare](https://docs.microsoft.com/previous-versions/windows/desktop/ms709539(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

任一书签可以是一种标准 OLE DB 定义[标准书签](https://docs.microsoft.com/previous-versions/windows/desktop/ms712954(v=vs.85))(`DBBMK_FIRST`， `DBBMK_LAST`，或`DBBMK_INVALID`)。 中返回的值`pComparison`指示两个书签之间的关系：

- DBCOMPARE_LT (`cbBookmark1`早`cbBookmark2`。)

- DBCOMPARE_EQ (`cbBookmark1`等同于`cbBookmark2`。)

- DBCOMPARE_GT (`cbBookmark1`晚`cbBookmark2`。)

- DBCOMPARE_NE （书签是等于和不排序。）

- DBCOMPARE_NOTCOMPARABLE （不能比较书签）。

## <a name="getrowsat"></a> Irowsetlocateimpl:: Getrowsat

提取从指定的偏移量从书签的行开始的行。

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

#### <a name="parameters"></a>参数

请参阅[irowsetlocate:: Getrowsat](https://docs.microsoft.com/previous-versions/windows/desktop/ms723031(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

若要改为提取从光标位置，使用[IRowset::GetRowsAt](https://docs.microsoft.com/previous-versions/windows/desktop/ms723031(v=vs.85))。

`IRowsetLocateImpl::GetRowsAt` 不会更改游标位置。

## <a name="getrowsbybookmark"></a> Irowsetlocateimpl:: Getrowsbybookmark

获取一个或多个匹配指定的书签的行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>参数

*hReserved*<br/>
[in]对应于*hChapter*参数[IRowsetLocate::GetRowsByBookmark](https://docs.microsoft.com/previous-versions/windows/desktop/ms725420(v=vs.85))。

其他参数，请参阅[IRowsetLocate::GetRowsByBookmark](https://docs.microsoft.com/previous-versions/windows/desktop/ms725420(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

书签可以为您定义的值或 OLE DB[标准书签](https://docs.microsoft.com/previous-versions/windows/desktop/ms712954(v=vs.85))(`DBBMK_FIRST`或`DBBMK_LAST`)。 不会更改游标位置。

## <a name="hash"></a> Irowsetlocateimpl:: Hash

返回哈希值用于指定书签。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>参数

*hReserved*<br/>
[in]对应于*hChapter*参数[IRowsetLocate::Hash](https://docs.microsoft.com/previous-versions/windows/desktop/ms709697(v=vs.85))。

其他参数，请参阅[IRowsetLocate::Hash](https://docs.microsoft.com/previous-versions/windows/desktop/ms709697(v=vs.85))中*OLE DB 程序员参考*。

## <a name="rgbookmarks"></a> Irowsetlocateimpl:: M_rgbookmarks

书签的数组。

### <a name="syntax"></a>语法

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms721190(v=vs.85))
[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[定位标记](https://docs.microsoft.com/previous-versions/windows/desktop/ms709728(v=vs.85))