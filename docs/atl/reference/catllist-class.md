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
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748733"
---
# <a name="catllist-class"></a>CAtlList 类

此类提供用于创建和管理列表对象的方法。

## <a name="syntax"></a>语法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>参数

*E*<br/>
元素类型。

*埃特格*<br/>
用于复制或移动元素的代码。 有关详细信息[，请参阅 CElementTraits 类](../../atl/reference/celementtraits-class.md)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[列表：：INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlList：CAtlList](#catllist)|构造函数。|
|[CAtlList：_CAtlList](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlList：：添加头](#addhead)|调用此方法以向列表的头部添加元素。|
|[CAtlList：：添加头列表](#addheadlist)|调用此方法以将现有列表添加到列表的头部。|
|[CAtlList：：添加尾](#addtail)|调用此方法以将元素添加到此列表的尾部。|
|[CAtlList：：添加尾号](#addtaillist)|调用此方法以将现有列表添加到此列表的尾部。|
|[CAtlList：：断言有效](#assertvalid)|调用此方法以确认列表有效。|
|[CAtlList：查找](#find)|调用此方法以搜索指定元素的列表。|
|[CAtlList：查找索引](#findindex)|调用此方法以获取元素的位置，给定索引值。|
|[CAtlList：GetAt](#getat)|调用此方法以返回列表中指定位置的元素。|
|[CAtlList：获取计数](#getcount)|调用此方法以返回列表中的对象数。|
|[CAtlList：获取头](#gethead)|调用此方法以返回列表头的元素。|
|[CAtlList：获取头位置](#getheadposition)|调用此方法以获取列表头的位置。|
|[CAtlList：获取下一个](#getnext)|调用此方法以从列表中返回下一个元素。|
|[CAtlList：GetPrev](#getprev)|调用此方法以从列表中返回以前的元素。|
|[CAtlList：GetTail](#gettail)|调用此方法以返回列表尾部的元素。|
|[CAtlList：获取尾部位置](#gettailposition)|调用此方法以获取列表尾部的位置。|
|[CAtlList：插入后](#insertafter)|调用此方法以在指定位置后将新元素插入列表中。|
|[CAtlList：：插入之前](#insertbefore)|调用此方法在指定位置之前将新元素插入列表中。|
|[CAtlList：：空](#isempty)|调用此方法以确定列表是否为空。|
|[Catllist：：移动头](#movetohead)|调用此方法将指定元素移动到列表的头部。|
|[Catllist：：移动到尾](#movetotail)|调用此方法将指定元素移动到列表的尾部。|
|[CAtlList：：删除所有](#removeall)|调用此方法以从列表中删除所有元素。|
|[CAtlList：：删除At](#removeat)|调用此方法从列表中删除单个元素。|
|[CAtlList：：删除头](#removehead)|调用此方法以删除列表头的元素。|
|[CAtlList：：删除头无返回](#removeheadnoreturn)|调用此方法以删除列表头的元素，而不返回值。|
|[CAtlList：：删除尾](#removetail)|调用此方法以删除列表尾部的元素。|
|[CAtllist：：删除尾号不返回](#removetailnoreturn)|调用此方法以删除列表尾部的元素，而不返回值。|
|[CAtlList：：Setat](#setat)|调用此方法以在列表中的给定位置设置元素的值。|
|[CAtlList：：交换元素](#swapelements)|调用此方法以交换列表中的元素。|

## <a name="remarks"></a>备注

该`CAtlList`类支持按顺序或按值访问的非唯一对象的有序列表。 `CAtlList`列表类似于双重链接列表。 每个列表都有一个头和一个尾，新元素（或在某些情况下的列表）可以添加到列表的任一端，或插入特定元素之前或之后。

大多数`CAtlList`方法都使用仓位值。 方法使用此值来引用存储元素的实际内存位置，不应直接计算或预测此值。 如果需要访问列表中的第*n*个元素，方法[CAtlList：findIndex](#findindex)将返回给定索引的相应位置值。 方法[CAtlList：GetNext](#getnext)和[CAtlList：GetPrev](#getprev)可用于迭代列表中的对象。

有关 ATL 提供的收集类的详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList：：添加头

调用此方法以向列表的头部添加元素。

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>参数

*元素*<br/>
新元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用第一个版本，则使用其默认构造函数而不是其复制构造函数创建空元素。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList：：添加头列表

调用此方法以将现有列表添加到列表的头部。

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

*plNew*指向的列表将插入到现有列表的开头。 在调试生成中，如果*plNew*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList：：添加尾

调用此方法以将元素添加到此列表的尾部。

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>参数

*元素*<br/>
要添加的元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用第一个版本，则使用其默认构造函数而不是其复制构造函数创建空元素。 元素将添加到列表的末尾，因此它现在成为尾部。 此方法可与空列表一起使用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList：：添加尾号

调用此方法以将现有列表添加到此列表的尾部。

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

*plNew*指向的列表在列表对象中的最后一个元素（如果有）之后插入。 因此 *，plNew*列表中的最后一个元素成为尾部。 在调试生成中，如果*plNew*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList：：断言有效

调用此方法以确认列表有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试生成中，如果列表对象无效，将发生断言失败。 要有效，空列表必须同时显示头部和尾部指向 NULL，并且不为空的列表必须同时显示头部和尾部指向有效地址。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList：CAtlList

构造函数。

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

`CAtlList`对象的构造函数。 块大小是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList：_CAtlList

析构函数。

```
~CAtlList() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，包括调用[CAtlList：：删除所有](#removeall)内容以从列表中删除所有元素。

在调试生成中，如果列表在调用`RemoveAll`后仍包含某些元素，则将发生断言失败。

## <a name="catllistfind"></a><a name="find"></a>CAtlList：查找

调用此方法以搜索指定元素的列表。

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>参数

*元素*<br/>
要在列表中找到的元素。

*位置启动后*<br/>
搜索的开始位置。 如果未指定值，则搜索从头元素开始。

### <a name="return-value"></a>返回值

如果找到元素，则返回元素的"位置"值，否则返回 NULL。

### <a name="remarks"></a>备注

在调试生成中，如果列表对象无效，或者*posStartAfter*值不在范围范围内，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList：查找索引

调用此方法以获取元素的位置，给定索引值。

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>参数

*i元素*<br/>
所需列表元素的零基索引。

### <a name="return-value"></a>返回值

返回相应的位置值，如果*iElement*不在范围范围内，则返回 NULL。

### <a name="remarks"></a>备注

此方法返回与给定索引值对应的"位置"，允许访问列表中的第*n*个元素。

在调试生成中，如果列表对象无效，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList：GetAt

调用此方法以返回列表中指定位置的元素。

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
指定特定元素的定位值。

### <a name="return-value"></a>返回值

对元素的引用或副本。

### <a name="remarks"></a>备注

如果列表是**const** `GetAt` ，则返回元素的副本。 这允许仅在赋值语句的右侧使用该方法，并保护列表免受修改。

如果列表不是**const**，`GetAt`则返回对元素的引用。 这允许在赋值语句的任意一侧使用该方法，从而允许修改列表条目。

在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：查找索引](#findindex)。

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList：获取计数

调用此方法以返回列表中的对象数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回列表中元素的数目。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：查找](#find)。

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList：获取头

调用此方法以返回列表头的元素。

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>返回值

返回对列表头的元素的引用或副本。

### <a name="remarks"></a>备注

如果列表是**const，**`GetHead`则返回列表头的元素的副本。 这允许仅在赋值语句的右侧使用该方法，并保护列表免受修改。

如果列表不是**const，**`GetHead`则返回对列表头的元素的引用。 这允许在赋值语句的任意一侧使用该方法，从而允许修改列表条目。

在调试生成中，如果列表的主管指向 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：addHead](#addhead)。

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList：获取头位置

调用此方法以获取列表头的位置。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>返回值

返回与列表头的元素对应的"位置"值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList：获取下一个

调用此方法以从列表中返回下一个元素。

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
由上一个调用返回的"位置"`GetNext`值[，CAtlList：：getHeadposition](#getheadposition)或其他`CAtlList`方法。

### <a name="return-value"></a>返回值

如果列表是**const** `GetNext` ，则返回列表的下一个元素的副本。 这允许仅在赋值语句的右侧使用该方法，并保护列表免受修改。

如果列表不是**const**，`GetNext`则返回对列表下一个元素的引用。 这允许在赋值语句的任意一侧使用该方法，从而允许修改列表条目。

### <a name="remarks"></a>备注

位置计数器*将更新*以指向列表中的下一个元素，如果不再有元素，则为 NULL。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：获取头位置](#getheadposition)。

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList：GetPrev

调用此方法以从列表中返回以前的元素。

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
由上一个调用返回的"位置"`GetPrev`值[，CAtlList：：GetTailposition](#gettailposition)或其他`CAtlList`方法。

### <a name="return-value"></a>返回值

如果列表是**const** `GetPrev` ，则返回列表元素的副本。 这允许仅在赋值语句的右侧使用该方法，并保护列表免受修改。

如果列表不是**const**，`GetPrev`则返回对列表元素的引用。 这允许在赋值语句的任意一侧使用该方法，从而允许修改列表条目。

### <a name="remarks"></a>备注

位置计数器*将更新*以指向列表中的前一个元素，如果没有更多元素，则为 NULL。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：获取尾部位置](#gettailposition)。

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList：GetTail

调用此方法以返回列表尾部的元素。

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>返回值

返回对列表末尾的元素的引用或副本。

### <a name="remarks"></a>备注

如果列表是**const，**`GetTail`则返回列表头的元素的副本。 这允许仅在赋值语句的右侧使用该方法，并保护列表免受修改。

如果列表不是**const，**`GetTail`则返回对列表头的元素的引用。 这允许在赋值语句的任意一侧使用该方法，从而允许修改列表条目。

在调试生成中，如果列表的尾部指向 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：添加尾数](#addtail)。

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList：获取尾部位置

调用此方法以获取列表尾部的位置。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>返回值

返回与列表尾部的元素对应的"位置"值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>列表：：INARGTYPE

当元素作为输入参数传递时使用的类型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList：插入后

调用此方法以在指定位置后将新元素插入列表中。

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*Pos*<br/>
将插入新元素的"位置"值。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的"位置"值。

### <a name="remarks"></a>备注

在调试生成中，如果列表无效、插入失败或尝试在尾部后插入元素，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList：：插入之前

调用此方法在指定位置之前将新元素插入列表中。

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*Pos*<br/>
新元素将插入到列表中，然后在此位置值之前。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的"位置"值。

### <a name="remarks"></a>备注

在调试生成中，如果列表无效、插入失败或尝试将元素插入到头之前，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList：：空

调用此方法以确定列表是否为空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果列表不包含任何对象，则返回 true，否则为 false。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>Catllist：：移动头

调用此方法将指定元素移动到列表的头部。

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
要移动的元素的定位值。

### <a name="remarks"></a>备注

指定元素从其当前位置移动到列表的头部。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>Catllist：：移动到尾

调用此方法将指定元素移动到列表的尾部。

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
要移动的元素的定位值。

### <a name="remarks"></a>备注

指定元素从其当前位置移动到列表的尾部。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：移动头](#movetohead)。

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList：：删除所有

调用此方法以从列表中删除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

此方法从列表中删除所有元素并释放分配的内存。 在调试生成中，如果未删除所有元素或列表结构已损坏，则将引发 ATLASSERT。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：是空的](#isempty)。

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList：：删除At

调用此方法从列表中删除单个元素。

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
要删除的元素的定位值。

### <a name="remarks"></a>备注

*删除 pos*引用的元素，并释放内存。 可以使用`RemoveAt`来移除列表的头部或尾部。

在调试生成中，如果列表无效，或者删除该元素导致列表访问不属于列表结构的内存，则将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList：：删除头

调用此方法以删除列表头的元素。

```
E RemoveHead();
```

### <a name="return-value"></a>返回值

返回列表头的元素。

### <a name="remarks"></a>备注

头元素将从列表中删除，并释放内存。 返回元素的副本。 在调试生成中，如果列表为空，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList：：删除头无返回

调用此方法以删除列表头的元素，而不返回值。

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>备注

头元素将从列表中删除，并释放内存。 在调试生成中，如果列表为空，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：是空的](#isempty)。

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList：：删除尾

调用此方法以删除列表尾部的元素。

```
E RemoveTail();
```

### <a name="return-value"></a>返回值

返回列表尾部的元素。

### <a name="remarks"></a>备注

尾元素将从列表中删除，并释放内存。 返回元素的副本。 在调试生成中，如果列表为空，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtllist：：删除尾号不返回

调用此方法以删除列表尾部的元素，而不返回值。

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>备注

尾元素将从列表中删除，并释放内存。 在调试生成中，如果列表为空，则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAtlList 的示例：：是空的](#isempty)。

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList：：Setat

调用此方法以在列表中的给定位置设置元素的值。

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*Pos*<br/>
与要更改的元素对应的位置值。

*元素*<br/>
新元素值。

### <a name="remarks"></a>备注

将现有值替换为*元素*。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList：：交换元素

调用此方法以交换列表中的元素。

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>参数

*位置1*<br/>
第一个位置值。

*pos2*<br/>
第二个位置值。

### <a name="remarks"></a>备注

交换指定两个位置的元素。 在调试生成中，如果任一位置值等于 NULL，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>另请参阅

[CList 类](../../mfc/reference/clist-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
