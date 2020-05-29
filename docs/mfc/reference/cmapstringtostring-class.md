---
title: CMapStringtoString 类
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
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370120"
---
# <a name="cmapstringtostring-class"></a>CMapStringtoString 类

支持 `CString` 对象键控的 `CString` 对象的映射。

## <a name="syntax"></a>语法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>成员

的成员`CMapStringToString`函数类似于类[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 只要将`CObject`指针视为返回值或"输出"函数参数，请替换指向**char**的指针。 无论将`CObject`指针视为"输入"函数参数，请替换指向**char**的指针。

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

例如，转换为

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>公共结构

|名称|说明|
|----------|-----------------|
|[CMapStringtoString：：CPair](#cpair)|包含键值和关联字符串对象值的嵌套结构。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CmapStringtoString：：CmapStringtoString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMapStringtoString：：获取计数](../../mfc/reference/cmapstringtoob-class.md#getcount)|返回此映射中的元素数。|
|[CMapStringtoString：：获取哈希表大小](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定哈希表中的当前元素数。|
|[CMapStringtoString：：获取NextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取下一个迭代元素。|
|[CMapStringtoString：：获取大小](../../mfc/reference/cmapstringtoob-class.md#getsize)|返回此映射中的元素数。|
|[CMapStringtoString：：获取起始位置](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一个元素的位置。|
|[CMapStringtoString：：哈希键](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定键的哈希值。|
|[CMapStringtostring：：inithashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapStringtoString：：空](../../mfc/reference/cmapstringtoob-class.md#isempty)|测试空映射条件（无元素）。|
|[CMapStringtoString：：查找](../../mfc/reference/cmapstringtoob-class.md#lookup)|根据空指针键查找空指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapStringtoString：：查找键](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapStringtoString：:P获取第一assoc](#pgetfirstassoc)|获取指向地图中第一`CString`个指针的指针。|
|[CMapStringtoString：:P获取Nextassoc](#pgetnextassoc)|获取指向下`CString`一个迭代的指针。|
|[CMapStringtoString：:P查找](#plookup)|返回指向 其值`CString`与指定值匹配的 指针。|
|[CMapStringtoString：：删除所有](../../mfc/reference/cmapstringtoob-class.md#removeall)|从此映射中删除所有元素。|
|[CMapStringtoString：：删除键](../../mfc/reference/cmapstringtoob-class.md#removekey)|删除由键指定的元素。|
|[CMapStringtoString：：Setat](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到地图中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMapStringtoString：：运算符\[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射中 ， 运算符替换`SetAt`。|

## <a name="remarks"></a>备注

`CMapStringToString` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果将地图存储到存档中（使用重载插入 （ **<<**） 运算符或使用`Serialize`成员函数，则依次序列化每个元素。

如果需要单个`CString`- `CString`元素的转储，则必须将转储上下文的深度设置为 1 或更大。

删除`CMapStringToString`对象或删除其元素时，将根据需要删除对象`CString`。

有关 的详细信息`CMapStringToString`，请参阅文章["集合](../../mfc/collections.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringtoString：：CPair

包含键值和关联的字符串对象的值。

### <a name="remarks"></a>备注

这是类[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)中的嵌套结构。

结构由两个字段组成：

- `key`键类型的实际值。

- `value`关联对象的值。

它用于存储从[CMapStringToString：:P 查找](#plookup)[、CMapStringToString：:PGetFirstAssoc](#pgetfirstassoc)和[CMapStringToString：:P获取NextAssoc](#pgetnextassoc)的返回值。

### <a name="example"></a>示例

  有关使用情况的示例，请参阅[CMapStringToString：:P 查找](#plookup)"的示例。

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringtoString：:P获取第一assoc

返回地图对象的第一个条目。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>返回值

指向地图中第一个条目的指针;请参阅[CmapStringtoString：：CPair](#cpair)。 如果地图为空，则值为 NULL。

### <a name="remarks"></a>备注

调用此函数以返回地图对象中第一个元素的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringtoString：:P获取Nextassoc

检索*由 pAssocRec*指向的地图元素。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>参数

*帕索克*<br/>
指向以前[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)调用返回的地图条目。

### <a name="return-value"></a>返回值

指向地图中下一个条目的指针;请参阅[CmapStringtoString：：CPair](#cpair)。 如果元素是地图中的最后一个元素，则该值为 NULL。

### <a name="remarks"></a>备注

调用此方法以迭代地图中的所有元素。 使用 调用`PGetFirstAssoc`检索第一个元素，然后通过映射遍历对`PGetNextAssoc`的调用来迭代。

### <a name="example"></a>示例

  请参阅[CMapStringToString：:P获取第一Assoc](#pgetfirstassoc)的示例。

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringtoString：:P查找

查找映射到给定键的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>参数

*关键*<br/>
指向要搜索的元素的键的指针。

### <a name="return-value"></a>返回值

指向指定键的指针。

### <a name="remarks"></a>备注

调用此方法以搜索具有与给定键完全匹配的键的地图元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
