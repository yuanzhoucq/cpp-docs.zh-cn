---
title: CMapPtrToPtr 类
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: f8fc69007d35927daaa7128de1bc0ceb0b44c746
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223039"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr 类

支持 void 指针键控的 void 指针的映射。

## <a name="syntax"></a>语法

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>成员

的成员函数 `CMapPtrToPtr` 类似于类[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论你在何处看到 `CObject` 作为函数参数或返回值的指针，都要将指针替换为 **`void`** 。 无论你在何处看到 `CString` **`const`** **`char`** 作为函数参数或返回值的指针，都可以将指针替换为 **`void`** 。

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

例如，转换为

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMapPtrToPtr::CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMapPtrToPtr：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|返回此映射中的元素数。|
|[CMapPtrToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定哈希表中元素的当前数目。|
|[CMapPtrToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取用于循环访问的下一个元素。|
|[CMapPtrToPtr：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|返回此映射中的元素数。|
|[CMapPtrToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一个元素的位置。|
|[CMapPtrToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定键的哈希值。|
|[CMapPtrToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapPtrToPtr：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|测试空映射条件（无元素）。|
|[CMapPtrToPtr：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|基于 void 指针键查找 void 指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapPtrToPtr：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapPtrToPtr：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|从此映射中移除所有元素。|
|[CMapPtrToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|
|[CMapPtrToPtr：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMapPtrToPtr：： operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射中-的运算符替换 `SetAt` 。|

## <a name="remarks"></a>备注

`CMapPtrToPtr`合并了 IMPLEMENT_DYNAMIC 宏，以支持运行时类型访问和转储到 `CDumpContext` 对象。 如果需要单独的地图元素（指针值）的转储，则必须将转储上下文的深度设置为1或更大。

指针到指针的映射不能序列化。

当删除 `CMapPtrToPtr` 对象或其元素时，仅删除指针而不是指针引用的实体。

有关的详细信息 `CMapPtrToPtr` ，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
