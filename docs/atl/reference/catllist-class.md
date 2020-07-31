---
title: CAtlList 类
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 15830a30e8236a13f3911d1b84d3727d3246fc0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226667"
---
# <a name="catllist-class"></a>CAtlList 类

此类提供用于创建和管理列表对象的方法。

## <a name="syntax"></a>语法

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>参数

*电邮*<br/>
元素类型。

*ETraits*<br/>
用于复制或移动元素的代码。 有关更多详细信息，请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|构造函数。|
|[CAtlList：： ~ CAtlList](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|调用此方法可将元素添加到列表的开头。|
|[CAtlList::AddHeadList](#addheadlist)|调用此方法可将现有列表添加到列表的开头。|
|[CAtlList：： AddTail](#addtail)|调用此方法可将元素添加到此列表的尾部。|
|[CAtlList::AddTailList](#addtaillist)|调用此方法可将现有列表添加到此列表的尾部。|
|[CAtlList::AssertValid](#assertvalid)|调用此方法以确认列表是否有效。|
|[CAtlList：： Find](#find)|调用此方法可在列表中搜索指定的元素。|
|[CAtlList：： FindIndex](#findindex)|如果给定索引值，则调用此方法以获取元素的位置。|
|[CAtlList：： GetAt](#getat)|调用此方法以返回列表中指定位置的元素。|
|[CAtlList：： GetCount](#getcount)|调用此方法以返回列表中的对象数。|
|[CAtlList::GetHead](#gethead)|调用此方法以返回列表开头的元素。|
|[CAtlList::GetHeadPosition](#getheadposition)|调用此方法可获取列表头的位置。|
|[CAtlList：： GetNext](#getnext)|调用此方法以返回列表中的下一个元素。|
|[CAtlList::GetPrev](#getprev)|调用此方法以从列表返回上一个元素。|
|[CAtlList::GetTail](#gettail)|调用此方法以返回位于列表末尾的元素。|
|[CAtlList::GetTailPosition](#gettailposition)|调用此方法可获取列表尾部的位置。|
|[CAtlList：： InsertAfter](#insertafter)|调用此方法可将新元素插入到列表中的指定位置之后。|
|[CAtlList：： InsertBefore](#insertbefore)|调用此方法可将新元素插入到列表中的指定位置之前。|
|[CAtlList：： IsEmpty](#isempty)|调用此方法以确定列表是否为空。|
|[CAtlList::MoveToHead](#movetohead)|调用此方法可将指定的元素移动到列表的开头。|
|[CAtlList::MoveToTail](#movetotail)|调用此方法可将指定的元素移动到列表的末尾。|
|[CAtlList：： RemoveAll](#removeall)|调用此方法以从列表中移除所有元素。|
|[CAtlList：： RemoveAt](#removeat)|调用此方法以从列表中删除单个元素。|
|[CAtlList::RemoveHead](#removehead)|调用此方法可移除列表开头的元素。|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|调用此方法可删除列表头中的元素，而不返回值。|
|[CAtlList::RemoveTail](#removetail)|调用此方法可删除列表末尾处的元素。|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|调用此方法可删除列表尾部的元素，而不返回值。|
|[CAtlList：： SetAt](#setat)|调用此方法可在列表中的给定位置设置元素的值。|
|[CAtlList::SwapElements](#swapelements)|调用此方法可交换列表中的元素。|

## <a name="remarks"></a>备注

`CAtlList`类支持按顺序或值访问的不唯一对象的有序列表。 `CAtlList`列表的行为类似于双重链接列表。 每个列表都有一个头和尾部，新元素（或在某些情况下为列表）可以添加到列表的任意一端，或插入到特定元素的前面或后面。

大多数 `CAtlList` 方法使用位置值。 方法使用此值来引用存储元素的实际内存位置，而不应直接计算或预测元素。 如果需要访问列表中的第*n*个元素，则方法[CAtlList：： FindIndex](#findindex)将返回给定索引的相应位置值。 方法[CAtlList：： GetNext](#getnext)和[CAtlList：： GetPrev](#getprev)可用于循环访问列表中的对象。

有关 ATL 提供的集合类的详细信息，请参阅[Atl Collection 类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

调用此方法可将元素添加到列表的开头。

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>参数

*element*<br/>
新元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用第一个版本，则将使用其默认构造函数而不是其复制构造函数创建一个空元素。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

调用此方法可将现有列表添加到列表的开头。

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

*PlNew*所指向的列表将插入到现有列表的开头。 在调试版本中，如果*plNew*等于 NULL，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList：： AddTail

调用此方法可将元素添加到此列表的尾部。

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>参数

*element*<br/>
要添加的元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用第一个版本，则将使用其默认构造函数而不是其复制构造函数创建一个空元素。 元素添加到列表的末尾，因此它现在变成尾部。 此方法可用于空列表。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

调用此方法可将现有列表添加到此列表的尾部。

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

*PlNew*所指向的列表将插入到列表对象中最后一个元素（如果有）的后面。 因此， *plNew*列表中的最后一个元素将成为尾部。 在调试版本中，如果*plNew*等于 NULL，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

调用此方法以确认列表是否有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试版本中，如果列表对象无效，则会发生断言失败。 为有效，空列表必须同时包含头和尾指向 NULL，并且不为空的列表必须同时具有指向有效地址的头和尾。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

构造函数。

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

对象的构造函数 `CAtlList` 。 块大小是在需要新元素时分配的内存量的度量值。 较大的块大小可减少对内存分配例程的调用，但会占用更多资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList：： ~ CAtlList

析构函数。

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，包括对[CAtlList：： RemoveAll](#removeall)的调用，以从列表中删除所有元素。

在调试版本中，如果列表在调用后仍包含某些元素，则会发生断言失败 `RemoveAll` 。

## <a name="catllistfind"></a><a name="find"></a>CAtlList：： Find

调用此方法可在列表中搜索指定的元素。

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>参数

*element*<br/>
要在列表中找到的元素。

*posStartAfter*<br/>
搜索的起始位置。 如果未指定任何值，则搜索将以 head 元素开头。

### <a name="return-value"></a>返回值

如果找到，则返回该元素的位置值，否则返回 NULL。

### <a name="remarks"></a>备注

在调试版本中，如果列表对象无效，或者*posStartAfter*值超出范围，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList：： FindIndex

如果给定索引值，则调用此方法以获取元素的位置。

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>参数

*iElement*<br/>
必需 list 元素的从零开始的索引。

### <a name="return-value"></a>返回值

返回相应的位置值; 如果*iElement*超出范围，则返回 NULL。

### <a name="remarks"></a>备注

此方法返回与给定索引值相对应的位置，允许访问列表中的第*n*个元素。

在调试版本中，如果列表对象无效，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList：： GetAt

调用此方法以返回列表中指定位置的元素。

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
指定特定元素的位置值。

### <a name="return-value"></a>返回值

元素的引用或副本。

### <a name="remarks"></a>备注

如果列表为 **`const`** ，则 `GetAt` 返回元素的副本。 这允许方法仅用于赋值语句右侧，并保护列表不被修改。

如果列表不为 **`const`** ，则 `GetAt` 返回对元素的引用。 这允许在赋值语句的两侧使用方法，从而允许修改列表项。

在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： FindIndex](#findindex)的示例。

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList：： GetCount

调用此方法以返回列表中的对象数。

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回列表中元素的数目。

### <a name="example"></a>示例

请参阅[CAtlList：： Find](#find)的示例。

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

调用此方法以返回列表开头的元素。

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>返回值

返回对列表开头的元素的引用或副本。

### <a name="remarks"></a>备注

如果列表为 **`const`** ，则 `GetHead` 返回该列表头中的元素的副本。 这允许方法仅用于赋值语句右侧，并保护列表不被修改。

如果列表不为 **`const`** ，则 `GetHead` 返回对列表开头的元素的引用。 这允许在赋值语句的两侧使用方法，从而允许修改列表项。

在调试版本中，如果列表的开头指向 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： AddHead](#addhead)的示例。

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

调用此方法可获取列表头的位置。

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>返回值

返回与列表头中的元素相对应的位置值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList：： GetNext

调用此方法以返回列表中的下一个元素。

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
一个位置值，由先前对的调用 `GetNext` 、 [CAtlList：： GetHeadPosition](#getheadposition)或其他方法返回 `CAtlList` 。

### <a name="return-value"></a>返回值

如果列表为 **`const`** ，则 `GetNext` 返回列表中下一个元素的副本。 这允许方法仅用于赋值语句右侧，并保护列表不被修改。

如果列表不为 **`const`** ，则 `GetNext` 返回对列表中下一个元素的引用。 这允许在赋值语句的两侧使用方法，从而允许修改列表项。

### <a name="remarks"></a>备注

位置计数器（ *pos*）将更新为指向列表中的下一个元素; 如果没有更多元素，则为 NULL。 在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： GetHeadPosition](#getheadposition)的示例。

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

调用此方法以从列表返回上一个元素。

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
一个位置值，由先前对的调用 `GetPrev` 、 [CAtlList：： GetTailPosition](#gettailposition)或其他方法返回 `CAtlList` 。

### <a name="return-value"></a>返回值

如果列表为 **`const`** ，则 `GetPrev` 返回列表中元素的副本。 这允许方法仅用于赋值语句右侧，并保护列表不被修改。

如果列表不为 **`const`** ，则 `GetPrev` 返回对列表中元素的引用。 这允许在赋值语句的两侧使用方法，从而允许修改列表项。

### <a name="remarks"></a>备注

位置计数器、位置更新为指向列表中的上一个元素，如果没有更多*元素，则*为 NULL。 在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： GetTailPosition](#gettailposition)的示例。

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

调用此方法以返回位于列表末尾的元素。

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>返回值

返回对列表尾部的元素的引用或副本。

### <a name="remarks"></a>备注

如果列表为 **`const`** ，则 `GetTail` 返回该列表头中的元素的副本。 这允许方法仅用于赋值语句右侧，并保护列表不被修改。

如果列表不为 **`const`** ，则 `GetTail` 返回对列表开头的元素的引用。 这允许在赋值语句的两侧使用方法，从而允许修改列表项。

在调试版本中，如果列表的尾部指向 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： AddTail](#addtail)的示例。

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

调用此方法可获取列表尾部的位置。

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>返回值

返回与列表尾部的元素相对应的位置值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

将元素作为输入参数传递时使用的类型。

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList：： InsertAfter

调用此方法可将新元素插入到列表中的指定位置之后。

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*位置*<br/>
要在其后插入新元素的位置值。

*element*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的位置值。

### <a name="remarks"></a>备注

在调试版本中，如果列表无效、插入失败或者尝试在结尾处插入元素，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList：： InsertBefore

调用此方法可将新元素插入到列表中的指定位置之前。

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*位置*<br/>
新元素将插入到列表中此位置值之前。

*element*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的位置值。

### <a name="remarks"></a>备注

在调试版本中，如果列表无效、插入失败或者尝试在头前面插入元素，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList：： IsEmpty

调用此方法以确定列表是否为空。

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果列表中不包含任何对象，则返回 true; 否则返回 false。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

调用此方法可将指定的元素移动到列表的开头。

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
要移动的元素的位置值。

### <a name="remarks"></a>备注

指定元素从其当前位置移动到列表的开头。 在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

调用此方法可将指定的元素移动到列表的末尾。

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
要移动的元素的位置值。

### <a name="remarks"></a>备注

指定元素从其当前位置移动到列表尾。 在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： MoveToHead](#movetohead)的示例。

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList：： RemoveAll

调用此方法以从列表中移除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

此方法从列表中删除所有元素并释放已分配的内存。 在调试版本中，如果未删除所有元素或者列表结构已损坏，则会引发 ATLASSERT。

### <a name="example"></a>示例

请参阅[CAtlList：： IsEmpty](#isempty)的示例。

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList：： RemoveAt

调用此方法以从列表中删除单个元素。

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
要移除的元素的位置值。

### <a name="remarks"></a>备注

删除*pos*引用的元素，并释放内存。 可以使用 `RemoveAt` 删除列表的开头或结尾。

在调试版本中，如果列表无效，或者如果删除元素导致列表访问不属于列表结构的内存，则断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

调用此方法可移除列表开头的元素。

```cpp
E RemoveHead();
```

### <a name="return-value"></a>返回值

返回列表开头的元素。

### <a name="remarks"></a>备注

将从列表中删除 head 元素，并释放内存。 返回元素的副本。 在调试版本中，如果列表为空，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

调用此方法可删除列表头中的元素，而不返回值。

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>备注

将从列表中删除 head 元素，并释放内存。 在调试版本中，如果列表为空，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： IsEmpty](#isempty)的示例。

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

调用此方法可删除列表末尾处的元素。

```cpp
E RemoveTail();
```

### <a name="return-value"></a>返回值

返回位于列表末尾的元素。

### <a name="remarks"></a>备注

将从列表中删除 tail 元素，并释放内存。 返回元素的副本。 在调试版本中，如果列表为空，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

调用此方法可删除列表尾部的元素，而不返回值。

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>备注

将从列表中删除 tail 元素，并释放内存。 在调试版本中，如果列表为空，则将发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList：： IsEmpty](#isempty)的示例。

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList：： SetAt

调用此方法可在列表中的给定位置设置元素的值。

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*位置*<br/>
要更改的与元素相对应的位置值。

*element*<br/>
新的元素值。

### <a name="remarks"></a>备注

将现有值替换为*元素*。 在调试版本中，如果*pos*等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

调用此方法可交换列表中的元素。

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>参数

*pos1*<br/>
第一个位置值。

*pos2*<br/>
第二个位置值。

### <a name="remarks"></a>备注

交换两个指定位置的元素。 在调试版本中，如果某一位置值等于 NULL，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>另请参阅

[CList 类](../../mfc/reference/clist-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
