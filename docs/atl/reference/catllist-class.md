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
ms.openlocfilehash: faed99197eb14da8ea095bef81d0d1a9845b18ad
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285498"
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

*ETraits*<br/>
用于复制或移动元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)的更多详细信息。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|构造函数。|
|[CAtlList::~CAtlList](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|调用此方法以将元素添加到了列表的开头。|
|[CAtlList::AddHeadList](#addheadlist)|调用此方法将现有的列表添加到了列表的开头。|
|[CAtlList::AddTail](#addtail)|调用此方法以将元素添加到此列表的末尾。|
|[CAtlList::AddTailList](#addtaillist)|调用此方法将现有的列表添加到此列表的结尾。|
|[CAtlList::AssertValid](#assertvalid)|调用此方法以确认该列表有效。|
|[CAtlList::Find](#find)|调用此方法搜索指定的元素的列表。|
|[CAtlList::FindIndex](#findindex)|调用此方法以获取给定的索引值的元素的位置。|
|[CAtlList::GetAt](#getat)|调用此方法以返回列表中指定位置处的元素。|
|[CAtlList::GetCount](#getcount)|调用此方法以在列表中返回的对象数。|
|[CAtlList::GetHead](#gethead)|调用此方法以返回了列表的开头处的元素。|
|[CAtlList::GetHeadPosition](#getheadposition)|调用此方法来获得了列表的开头的位置。|
|[CAtlList::GetNext](#getnext)|调用此方法以从列表中返回的下一个元素。|
|[CAtlList::GetPrev](#getprev)|调用此方法以从列表中返回上一个元素。|
|[CAtlList::GetTail](#gettail)|调用此方法以返回列表的结尾处的元素。|
|[CAtlList::GetTailPosition](#gettailposition)|调用此方法以获取列表的尾数据的位置。|
|[CAtlList::InsertAfter](#insertafter)|调用此方法来指定位置之后的新元素插入到列表。|
|[CAtlList::InsertBefore](#insertbefore)|调用此方法以将新元素插入到前面的指定位置的列表。|
|[CAtlList::IsEmpty](#isempty)|调用此方法以确定列表是否为空。|
|[CAtlList::MoveToHead](#movetohead)|调用此方法将指定的元素移动到了列表的开头。|
|[CAtlList::MoveToTail](#movetotail)|调用此方法将指定的元素移动到列表的结尾。|
|[CAtlList::RemoveAll](#removeall)|调用此方法以从列表中删除的所有元素。|
|[CAtlList::RemoveAt](#removeat)|调用此方法以从列表中删除单个元素。|
|[CAtlList::RemoveHead](#removehead)|调用此方法来删除了列表的开头处的元素。|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|调用此方法不返回值中删除了列表的开头处的元素。|
|[CAtlList::RemoveTail](#removetail)|调用此方法来删除列表的结尾处的元素。|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|调用此方法来删除而不返回值的列表的结尾处的元素。|
|[CAtlList::SetAt](#setat)|调用此方法以在列表中的给定位置设置元素的值。|
|[CAtlList::SwapElements](#swapelements)|调用此方法来交换列表中的元素。|

## <a name="remarks"></a>备注

`CAtlList`类有序列表的唯一，则对象可访问，按顺序或值的支持。 `CAtlList` 列表类似于双向链接列表。 每个列表具有头和尾，并可以添加到列表中，任一端或之前或之后的特定元素插入新元素 （或在某些情况下的列表）。

大多数的`CAtlList`方法进行使用的位置值。 此值的方法用于引用其中元素存储，并且不应计算或直接预测的实际内存位置。 如有必要访问*n*个元素，以在列表中，该方法[CAtlList::FindIndex](#findindex)将返回给定索引的相应位置值。 方法[CAtlList::GetNext](#getnext)并[CAtlList::GetPrev](#getprev)可用于循环访问列表中的对象。

有关可使用 ATL 的集合类的详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="addhead"></a>  CAtlList::AddHead

调用此方法以将元素添加到了列表的开头。

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>参数

*element*<br/>
新元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用的第一个版本，则使用其默认构造函数，而不是其复制构造函数创建一个空元素。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

##  <a name="addheadlist"></a>  CAtlList::AddHeadList

调用此方法将现有的列表添加到了列表的开头。

```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

指向列表*plNew*插入现有列表的开头。 在调试版本中，如果出现断言失败*plNew*等于 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

##  <a name="addtail"></a>  CAtlList::AddTail

调用此方法以将元素添加到此列表的末尾。

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>参数

*element*<br/>
要添加的元素。

### <a name="return-value"></a>返回值

返回新添加的元素的位置。

### <a name="remarks"></a>备注

如果使用的第一个版本，则使用其默认构造函数，而不是其复制构造函数创建一个空元素。 该元素添加到列表的末尾，因此它现在成为尾部。 此方法可以用于空列表。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

##  <a name="addtaillist"></a>  CAtlList::AddTailList

调用此方法将现有的列表添加到此列表的结尾。

```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>参数

*plNew*<br/>
要添加的列表。

### <a name="remarks"></a>备注

指向列表*plNew*之后插入的最后一个元素 （如果有） 的列表对象中。 中的最后一个元素*plNew*列表因此变得尾部。 在调试版本中，如果出现断言失败*plNew*等于 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

##  <a name="assertvalid"></a>  CAtlList::AssertValid

调用此方法以确认该列表有效。

```
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试版本中，如果列表对象不是有效，将发生断言失败。 若要使之有效，一个空列表必须具有头和尾部指向 NULL，并且不为空列表必须具有头和尾部指向有效的地址。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

##  <a name="catllist"></a>  CAtlList::CAtlList

构造函数。

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

构造函数`CAtlList`对象。 块大小为分配的新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

##  <a name="dtor"></a>  CAtlList::~CAtlList

析构函数。

```
~CAtlList() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，包括调用[CAtlList::RemoveAll](#removeall)若要从列表中删除所有元素。

在调试版本中，如果列表仍在调用后不包含某些元素发生断言失败`RemoveAll`。

##  <a name="find"></a>  CAtlList::Find

调用此方法搜索指定的元素的列表。

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>参数

*element*<br/>
要在列表中找到的元素。

*posStartAfter*<br/>
搜索起始位置。 如果未不指定任何值，搜索开始与头元素。

### <a name="return-value"></a>返回值

返回元素的位置值，如果找到，否则为返回 NULL。

### <a name="remarks"></a>备注

在调试版本中，如果列表对象不是有效的或者出现断言失败*posStartAfter*值超出了范围。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

##  <a name="findindex"></a>  CAtlList::FindIndex

调用此方法以获取给定的索引值的元素的位置。

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>参数

*iElement*<br/>
所需的列表元素的从零开始的索引。

### <a name="return-value"></a>返回值

如果返回的相应位置的值或为 NULL *iElement*不在范围。

### <a name="remarks"></a>备注

此方法返回对应于一个给定的索引值，允许访问的位置*n*个元素，以在列表中的。

在调试版本中，如果列表对象不是有效，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

##  <a name="getat"></a>  CAtlList::GetAt

调用此方法以返回列表中指定位置处的元素。

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
指定特定元素的位置值。

### <a name="return-value"></a>返回值

引用或元素的副本。

### <a name="remarks"></a>备注

如果列表为**const**，`GetAt`返回元素的副本。 这允许使用仅在赋值语句右侧的方法，并从修改保护列表。

如果该列表不是**const**，`GetAt`返回元素的引用。 这允许使用赋值语句的任何一侧的方法，并因此允许列表条目，以进行修改。

在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::FindIndex](#findindex)。

##  <a name="getcount"></a>  CAtlList::GetCount

调用此方法以在列表中返回的对象数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回列表中元素的数目。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::Find](#find)。

##  <a name="gethead"></a>  CAtlList::GetHead

调用此方法以返回了列表的开头处的元素。

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>返回值

返回的引用或位于列表的头元素的副本。

### <a name="remarks"></a>备注

如果列表为**const**，`GetHead`返回了列表的开头处的元素的副本。 这允许使用仅在赋值语句右侧的方法，并从修改保护列表。

如果该列表不是**const**，`GetHead`返回对列表的开头处的元素的引用。 这允许使用赋值语句的任何一侧的方法，并因此允许列表条目，以进行修改。

在调试版本中，如果列表的开头点为 NULL，将出现断言失败。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::AddHead](#addhead)。

##  <a name="getheadposition"></a>  CAtlList::GetHeadPosition

调用此方法来获得了列表的开头的位置。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>返回值

返回对应于列表的开头处的元素的位置值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

##  <a name="getnext"></a>  CAtlList::GetNext

调用此方法以从列表中返回的下一个元素。

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
返回上次调用的位置值`GetNext`， [CAtlList::GetHeadPosition](#getheadposition)，或其他`CAtlList`方法。

### <a name="return-value"></a>返回值

如果列表为**const**，`GetNext`返回列表的下一个元素的副本。 这允许使用仅在赋值语句右侧的方法，并从修改保护列表。

如果该列表不是**const**，`GetNext`返回列表的下一个元素的引用。 这允许使用赋值语句的任何一侧的方法，并因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

位置计数器*pos*，会更新以指向下一个元素在列表中，或如果没有更多元素，则为 NULL。 在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::GetHeadPosition](#getheadposition)。

##  <a name="getprev"></a>  CAtlList::GetPrev

调用此方法以从列表中返回上一个元素。

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
返回上次调用的位置值`GetPrev`， [CAtlList::GetTailPosition](#gettailposition)，或其他`CAtlList`方法。

### <a name="return-value"></a>返回值

如果列表为**const**，`GetPrev`返回列表的元素的副本。 这允许使用仅在赋值语句右侧的方法，并从修改保护列表。

如果该列表不是**const**，`GetPrev`返回对列表的元素的引用。 这允许使用赋值语句的任何一侧的方法，并因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

位置计数器*pos*，会更新以指向上一个元素在列表中，或如果没有更多元素，则为 NULL。 在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::GetTailPosition](#gettailposition)。

##  <a name="gettail"></a>  CAtlList::GetTail

调用此方法以返回列表的结尾处的元素。

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>返回值

返回的引用或位于列表的结尾的元素的副本。

### <a name="remarks"></a>备注

如果列表为**const**，`GetTail`返回了列表的开头处的元素的副本。 这允许使用仅在赋值语句右侧的方法，并从修改保护列表。

如果该列表不是**const**，`GetTail`返回对列表的开头处的元素的引用。 这允许使用赋值语句的任何一侧的方法，并因此允许列表条目，以进行修改。

在调试版本中，如果列表的尾点为 NULL，将出现断言失败。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::AddTail](#addtail)。

##  <a name="gettailposition"></a>  CAtlList::GetTailPosition

调用此方法以获取列表的尾数据的位置。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>返回值

返回对应于列表的结尾处的元素的位置值。

### <a name="remarks"></a>备注

如果列表为空，则返回的值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

##  <a name="inargtype"></a>  CAtlList::INARGTYPE

作为输入参数传递一个元素时所使用的类型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertafter"></a>  CAtlList::InsertAfter

调用此方法来指定位置之后的新元素插入到列表。

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*pos*<br/>
将在其后插入新元素的位置值。

*element*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的位置值。

### <a name="remarks"></a>备注

在调试版本中，如果列表不是有效的如果插入失败，或尝试之后尾部插入该元素，将出现断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

##  <a name="insertbefore"></a>  CAtlList::InsertBefore

调用此方法以将新元素插入到前面的指定位置的列表。

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*pos*<br/>
新元素将插入到此位置的值前面的列表。

*element*<br/>
要插入的元素。

### <a name="return-value"></a>返回值

返回新元素的位置值。

### <a name="remarks"></a>备注

在调试版本中，如果列表不是有效的如果插入失败，或尝试头之前插入该元素，将出现断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

##  <a name="isempty"></a>  CAtlList::IsEmpty

调用此方法以确定列表是否为空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果列表不包含的对象，否则为 false，则返回 true。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

##  <a name="movetohead"></a>  CAtlList::MoveToHead

调用此方法将指定的元素移动到了列表的开头。

```
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
要移动的元素的位置值。

### <a name="remarks"></a>备注

指定的元素从其当前位置移动到了列表的开头。 在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

##  <a name="movetotail"></a>  CAtlList::MoveToTail

调用此方法将指定的元素移动到列表的结尾。

```
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
要移动的元素的位置值。

### <a name="remarks"></a>备注

指定的元素从其当前位置移动到列表的结尾。 在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::MoveToHead](#movetohead)。

##  <a name="removeall"></a>  CAtlList::RemoveAll

调用此方法以从列表中删除的所有元素。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

此方法从列表中移除所有元素，并释放已分配的内存。 在调试版本中将引发 ATLASSERT 如果所有元素不会都删除或已损坏列表结构。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::IsEmpty](#isempty)。

##  <a name="removeat"></a>  CAtlList::RemoveAt

调用此方法以从列表中删除单个元素。

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
要移除的元素位置的值。

### <a name="remarks"></a>备注

引用的元素*pos*被删除，并且将释放内存。 它是可接受使用`RemoveAt`若要删除的头部或尾部的列表。

在调试版本中，如果该列表不是有效或删除该元素会导致访问内存，这并不是列表结构的一部分的列表，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

##  <a name="removehead"></a>  CAtlList::RemoveHead

调用此方法来删除了列表的开头处的元素。

```
E RemoveHead();
```

### <a name="return-value"></a>返回值

返回列表的开头处的元素。

### <a name="remarks"></a>备注

从列表中，删除该头元素和释放内存。 返回元素的副本。 在调试版本中，如果列表为空，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

##  <a name="removeheadnoreturn"></a>  CAtlList::RemoveHeadNoReturn

调用此方法不返回值中删除了列表的开头处的元素。

```
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>备注

从列表中，删除该头元素和释放内存。 在调试版本中，如果列表为空，将发生断言失败。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::IsEmpty](#isempty)。

##  <a name="removetail"></a>  CAtlList::RemoveTail

调用此方法来删除列表的结尾处的元素。

```
E RemoveTail();
```

### <a name="return-value"></a>返回值

返回列表的结尾处的元素。

### <a name="remarks"></a>备注

从列表中，删除结尾元素，并且将释放内存。 返回元素的副本。 在调试版本中，如果列表为空，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

##  <a name="removetailnoreturn"></a>  CAtlList::RemoveTailNoReturn

调用此方法来删除而不返回值的列表的结尾处的元素。

```
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>备注

从列表中，删除结尾元素，并且将释放内存。 在调试版本中，如果列表为空，将发生断言失败。

### <a name="example"></a>示例

有关示例，请参阅[CAtlList::IsEmpty](#isempty)。

##  <a name="setat"></a>  CAtlList::SetAt

调用此方法以在列表中的给定位置设置元素的值。

```
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>参数

*pos*<br/>
对应于要更改的元素的位置值。

*element*<br/>
新的元素值。

### <a name="remarks"></a>备注

替换现有值与*元素*。 在调试版本中，如果出现断言失败*pos*等于 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

##  <a name="swapelements"></a>  CAtlList::SwapElements

调用此方法来交换列表中的元素。

```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>参数

*pos1*<br/>
第一个位置值。

*pos2*<br/>
第二个位置值。

### <a name="remarks"></a>备注

交换在指定的两个位置的元素。 在调试版本中，如果任一位置的值等于 NULL，将发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>请参阅

[CList 类](../../mfc/reference/clist-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
