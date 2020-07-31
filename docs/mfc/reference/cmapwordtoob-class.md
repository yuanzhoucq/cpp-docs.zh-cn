---
title: CMapWordToOb 类
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: f360760bb5c04400ed77ef49c5968f8e9e7a6e59
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222987"
---
# <a name="cmapwordtoob-class"></a>CMapWordToOb 类

支持 16 位键控的 `CObject` 指针的映射。

## <a name="syntax"></a>语法

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>成员

的成员函数 `CMapWordToOb` 类似于类[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论你在何处看到 `CString` **`const`** **`char`** 作为函数参数或返回值的指针，都可以替换为 WORD。

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

例如，转换为

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMapWordToOb：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|返回此映射中的元素数。|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定哈希表中元素的当前数目。|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取用于循环访问的下一个元素。|
|[CMapWordToOb：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|返回此映射中的元素数。|
|[CMapWordToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一个元素的位置。|
|[CMapWordToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定键的哈希值。|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapWordToOb：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|测试空映射条件（无元素）。|
|[CMapWordToOb：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|基于 void 指针键查找 void 指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapWordToOb：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapWordToOb：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|从此映射中移除所有元素。|
|[CMapWordToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|
|[CMapWordToOb：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMapWordToOb：： operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射中-的运算符替换 `SetAt` 。|

## <a name="remarks"></a>备注

`CMapWordToOb`合并 IMPLEMENT_SERIAL 宏，以支持其元素的序列化和转储。 如果使用重载的插入（ **<<** ）运算符或成员函数将映射存储到存档中，则将依次序列化每个元素 `Serialize` 。

如果需要单独的单词元素的转储 `CObject` ，则必须将转储上下文的深度设置为1或更大。

`CMapWordToOb`删除对象时，或删除其元素时，将 `CObject` 删除指针。 指针引用的对象 `CObject` 不会被销毁。

有关的详细信息 `CMapWordToOb` ，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
