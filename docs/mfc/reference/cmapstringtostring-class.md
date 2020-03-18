---
title: CMapStringToString 类
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442596"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 类

支持 `CString` 对象键控的 `CString` 对象的映射。

## <a name="syntax"></a>语法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Members

`CMapStringToString` 的成员函数类似于类[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论你在何处看到作为返回值或 "output" 函数参数的 `CObject` 指针，都需要用一个指向**char**的指针代替。 无论你在何处看到作为 "input" 函数参数的 `CObject` 指针，都可以用指向**char**的指针代替。

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

例如，转换为

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>公共结构

|名称|说明|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|一个嵌套结构，其中包含键值和关联的字符串对象的值。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMapStringToString：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|返回此映射中的元素数。|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定哈希表中元素的当前数目。|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取用于循环访问的下一个元素。|
|[CMapStringToString：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|返回此映射中的元素数。|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一个元素的位置。|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定键的哈希值。|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapStringToString：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|测试空映射条件（无元素）。|
|[CMapStringToString：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|基于 void 指针键查找 void 指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapStringToString：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapStringToString：:P GetFirstAssoc](#pgetfirstassoc)|获取一个指针，该指针指向映射中的第一个 `CString`。|
|[CMapStringToString：:P GetNextAssoc](#pgetnextassoc)|获取一个指针，该指针指向用于迭代的下一个 `CString`。|
|[CMapStringToString：:P 查找](#plookup)|返回一个指向 `CString` 的指针，其值与指定的值匹配。|
|[CMapStringToString：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|从此映射中移除所有元素。|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|
|[CMapStringToString：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CMapStringToString：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射中-用于 `SetAt`的运算符替换。|

## <a name="remarks"></a>备注

`CMapStringToString` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果使用重载的插入（ **<<** ）运算符或使用 `Serialize` 成员函数，则会依次序列化每个元素。

如果需要转储单个 `CString`- `CString` 元素，则必须将转储上下文的深度设置为1或更大。

删除 `CMapStringToString` 对象或删除其元素时，将根据需要删除 `CString` 的对象。

有关 `CMapStringToString`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

##  <a name="cpair"></a>CMapStringToString::CPair

包含一个键值和关联的字符串对象的值。

### <a name="remarks"></a>备注

这是[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)类中的嵌套结构。

结构由以下两个字段组成：

- `key` 键类型的实际值。

- `value` 关联对象的值。

它用于存储来自[CMapStringToString：:P lookup](#plookup)、 [CMapStringToString：:P getfirstassoc](#pgetfirstassoc)和[CMapStringToString：:P getnextassoc](#pgetnextassoc)的返回值。

### <a name="example"></a>示例

  有关用法示例，请参阅[CMapStringToString：:P lookup](#plookup)的示例。

##  <a name="pgetfirstassoc"></a>CMapStringToString：:P GetFirstAssoc

返回 map 对象的第一个条目。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>返回值

指向映射中第一项的指针;请参阅[CMapStringToString：： CPair](#cpair)。 如果映射为空，则该值为 NULL。

### <a name="remarks"></a>备注

调用此函数可返回指向 map 对象中第一个元素的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>CMapStringToString：:P GetNextAssoc

检索由*pAssocRec*指向的地图元素。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>参数

*pAssoc*<br/>
指向由上一个[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)调用返回的映射项。

### <a name="return-value"></a>返回值

指向映射中下一项的指针;请参阅[CMapStringToString：： CPair](#cpair)。 如果该元素是映射中的最后一个，则该值为 NULL。

### <a name="remarks"></a>备注

调用此方法可循环访问映射中的所有元素。 使用对 `PGetFirstAssoc` 的调用检索第一个元素，然后通过连续调用 `PGetNextAssoc`来循环访问该映射。

### <a name="example"></a>示例

  请参阅[CMapStringToString：:P getfirstassoc](#pgetfirstassoc)的示例。

##  <a name="plookup"></a>CMapStringToString：:P 查找

查找映射到给定键的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>参数

*key*<br/>
一个指针，指向要搜索的元素的键。

### <a name="return-value"></a>返回值

指向指定键的指针。

### <a name="remarks"></a>备注

调用此方法以搜索其键与给定键完全匹配的地图元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
