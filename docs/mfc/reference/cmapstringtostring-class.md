---
title: CMapStringToString 类
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: ed717497866076681e39cdee7803a45eb8e097d3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780361"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 类

支持 `CString` 对象键控的 `CString` 对象的映射。

## <a name="syntax"></a>语法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>成员

成员函数`CMapStringToString`类似于类的成员函数[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论您在何处`CObject`指针为返回值或"输出"函数参数，将替换为指针**char**。 无论您在何处`CObject`作为"输入"函数参数的指针替换为指向的指针**char**。

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

例如，转换为

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

### <a name="public-structures"></a>公共结构

|名称|描述|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|包含密钥值和关联的字符串对象的值的嵌套的结构。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|此映射中返回元素的数。|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定当前的哈希表中的元素数。|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取用于循环的下一个元素。|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|此映射中返回元素的数。|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一个元素的位置。|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定的键的哈希值。|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|空映射条件 （元素） 的测试。|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查找的 void 指针关键字的 void 指针。 指针值，而不是它指向的实体用于关键的比较。|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回具有指定的密钥值相关联的密钥对的引用。|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|获取一个指针指向第一个`CString`映射中。|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|获取一个指针指向下一个`CString`用于循环访问。|
|[CMapStringToString::PLookup](#plookup)|返回一个指向`CString`其值与指定的值匹配。|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此映射中移除所有元素。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射 — 运算符替换为`SetAt`。|

## <a name="remarks"></a>备注

`CMapStringToString` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果映射存储到存档，使用重载插入反过来序列的每个元素 ( **<<**) 运算符或`Serialize`成员函数。

如果你需要个人的转储`CString` -  `CString`元素，必须将转储上下文的深度设置为 1 或更高版本。

当`CMapStringToString`删除对象，或删除它的元素时，`CString`根据需要删除对象。

有关详细信息`CMapStringToString`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>要求

**标头：** afxcoll.h

##  <a name="cpair"></a>  CMapStringToString::CPair

包含密钥值和关联的字符串对象的值。

### <a name="remarks"></a>备注

这是一个类中的嵌套的结构[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)。

该结构由两个字段组成：

- `key` 密钥类型的实际值。

- `value` 关联的对象的值。

它用于存储中的返回值[CMapStringToString::PLookup](#plookup)， [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)，并[CMapStringToString::PGetNextAssoc](#pgetnextassoc)。

### <a name="example"></a>示例

  有关用法的示例，请参阅示例[CMapStringToString::PLookup](#plookup)。

##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc

返回 map 对象的第一个条目。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>返回值

指向映射中的第一个条目请参阅[CMapStringToString::CPair](#cpair)。 如果映射为空，则该值为 NULL。

### <a name="remarks"></a>备注

调用此函数可返回 map 对象中的第一个元素的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc

检索指向的位置的地图元素*pAssocRec*。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>参数

*pAssoc*<br/>
指向返回先前的映射条目[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)调用。

### <a name="return-value"></a>返回值

指向映射中，则在下一个条目请参阅[CMapStringToString::CPair](#cpair)。 如果该元素为在映射中的最后一个，该值为 NULL。

### <a name="remarks"></a>备注

调用此方法来循环访问映射中的所有元素。 检索的第一个元素通过调用`PGetFirstAssoc`，然后循环访问具有连续调用映射`PGetNextAssoc`。

### <a name="example"></a>示例

  有关示例，请参阅[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)。

##  <a name="plookup"></a>  CMapStringToString::PLookup

查找映射到给定键的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>参数

*key*<br/>
指向要在其中搜索的元素的键的指针。

### <a name="return-value"></a>返回值

指向指定键的指针。

### <a name="remarks"></a>备注

调用此方法搜索的地图元素与给定的键完全匹配的密钥。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
