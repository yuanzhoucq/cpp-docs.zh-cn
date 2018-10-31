---
title: CMapPtrToWord 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
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
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
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
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6abca6c0cc467e2609de62b3b945a550ffe35b7b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074145"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord 类

支持 void 指针键控的 16 位的映射。

## <a name="syntax"></a>语法

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>成员

成员函数`CMapPtrToWord`类似于类的成员函数[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论您在何处`CObject`作为函数参数或返回值的指针替换词。 无论您在何处`CString`或**const**指针，指向**char**作为函数参数或返回值，替换为一个指向**void**。

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

例如，转换为

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

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
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此映射中移除所有元素。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::operator [ ]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射 — 运算符替换为`SetAt`。|

## <a name="remarks"></a>备注

`CMapWordToPtr` 集成了 IMPLEMENT_DYNAMIC 宏来支持运行时类型访问和转储到`CDumpContext`对象。 如果您需要单独的地图元素的转储，你必须将转储上下文的深度设置为 1 或更高版本。

指针到 word 映射可能会不序列化。

当`CMapPtrToWord`对象被删除，或移除其元素，当删除指针和单词。 不会删除的实体引用的关键要点。

有关详细信息`CMapPtrToWord`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>要求

**标头：** afxcoll.h

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

