---
title: CList 类
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 383222e4892bccc653f010ce4939bca23f2adc93
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780946"
---
# <a name="clist-class"></a>CList 类

支持可按顺序或值访问的不唯一对象的有序列表。

## <a name="syntax"></a>语法

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CList::CList](#clist)|构造一个空的有序列的表。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （使新头） 了列表的开头。|
|[CList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到列表 （使新结尾） 的尾部。|
|[CList::Find](#find)|获取指针值所指定的元素的位置。|
|[CList::FindIndex](#findindex)|获取指定的从零开始的索引的元素的位置。|
|[CList::GetAt](#getat)|获取位于给定位置的元素。|
|[CList::GetCount](#getcount)|返回此列表中的元素数。|
|[CList::GetHead](#gethead)|返回的列表 （不能为空） 的头元素。|
|[CList::GetHeadPosition](#getheadposition)|返回列表的头元素的位置。|
|[CList::GetNext](#getnext)|获取用于循环的下一个元素。|
|[CList::GetPrev](#getprev)|获取循环访问的上一个元素。|
|[CList::GetSize](#getsize)|返回此列表中的元素数。|
|[CList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|
|[CList::GetTailPosition](#gettailposition)|返回列表的结尾元素的位置。|
|[CList::InsertAfter](#insertafter)|在给定位置后插入一个新元素。|
|[CList::InsertBefore](#insertbefore)|将插入新元素之前的给定位置。|
|[CList::IsEmpty](#isempty)|对于空列表条件 （元素） 的测试。|
|[CList::RemoveAll](#removeall)|此列表中移除所有元素。|
|[CList::RemoveAt](#removeat)|从此列表中，指定位置移除一个元素。|
|[CList::RemoveHead](#removehead)|从列表的开头移除的元素。|
|[CList::RemoveTail](#removetail)|从列表的结尾移除的元素。|
|[CList::SetAt](#setat)|设置给定位置处的元素。|

#### <a name="parameters"></a>参数

*类型*<br/>
在列表中存储的对象的类型。

*ARG_TYPE*<br/>
用于引用存储在列表中的对象的类型。 可以为引用。

## <a name="remarks"></a>备注

`CList` 列表类似于双向链接列表。

位置类型的变量是列表的键。 可以使用作为的迭代器位置变量要遍历列表，按顺序和作为用于保存一个位置的书签。 位置不是相同的索引，但是。

元素插入速度非常快列表头、 尾和已知位置。 按值或索引查找元素所需顺序搜索。 此搜索可能较慢，如果列表太长。

如果你需要在列表中的各个元素的转储，你必须将转储上下文的深度设置为 1 或更高版本。

全局帮助器函数的此类调用的某些成员函数必须进行自定义的大部分使用`CList`类。 请参阅[集合类帮助器](../../mfc/reference/collection-class-helpers.md)"宏和全局变量"部分中。

有关使用的详细信息`CList`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

将新元素的列表添加到此列表的开头。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*newElement*<br/>
新元素。

*pNewList*<br/>
指向另一个`CList`列表。 中的元素*pNewList*将添加到此列表。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的位置值。

### <a name="remarks"></a>备注

列表可以为空操作之前。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

将新元素的列表添加到此列表的结尾。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*newElement*<br/>
要添加到此列表的元素。

*pNewList*<br/>
指向另一个`CList`列表。 中的元素*pNewList*将添加到此列表。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的位置值。

### <a name="remarks"></a>备注

列表可以为空操作之前。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

构造一个空的有序列的表。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
扩展列表的内存分配粒度。

### <a name="remarks"></a>备注

随着在列表中的单元分配内存*nBlockSize*条目。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

按顺序来查找与指定的第一个元素在列表中搜索*searchValue*。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*searchValue*<br/>
要在列表中找到的值。

*startAfter*<br/>
搜索起始位置。 如果未不指定任何值，搜索开始与头元素。

### <a name="return-value"></a>返回值

可用于迭代或检索对象指针; 一个位置值如果未找到该对象为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

使用的值*nIndex*作为列表中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要找的列表元素的从零开始的索引。

### <a name="return-value"></a>返回值

可用于迭代或检索对象指针; 一个位置值则为 NULL *nIndex*为负或过大。

### <a name="remarks"></a>备注

从列表中，停止对的开头开始顺序扫描*n*个元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

获取位于给定位置列表元素。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定对象的类型。

*position*<br/>
要获取的元素的列表中的位置。

### <a name="return-value"></a>返回值

请参阅的返回值说明`GetHead`。

### <a name="remarks"></a>备注

`GetAt` 返回与给定位置相关的元素 （或元素的引用）。 不是索引，请与相同和您无法对位置值自己。 位置类型的变量是列表的键。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

  有关示例，请参阅[CList::GetHeadPosition](#getheadposition)。

##  <a name="getcount"></a>  CList::GetCount

获取此列表中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

一个包含元素计数的整数值。

### <a name="remarks"></a>备注

调用此方法将生成相同的结果[CList::GetSize](#getsize)方法。

### <a name="example"></a>示例

  有关示例，请参阅[CList::RemoveHead](#removehead)。

##  <a name="gethead"></a>  CList::GetHead

获取此列表的头元素 （或与头元素的引用）。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定对象的类型。

### <a name="return-value"></a>返回值

如果列表为**const**，`GetHead`返回了列表的开头处的元素的副本。 这允许使用仅在赋值语句右侧的函数，并从修改保护列表。

如果该列表不是**const**，`GetHead`返回对列表的开头处的元素的引用。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

获取此列表的头元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::GetNext

获取标识的列表元素*rPosition*，然后设置*rPosition*到列表中的下一个条目的位置值。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定元素的类型。

*rPosition*<br/>
对先前返回的位置值的引用`GetNext`， [GetHeadPosition](#getheadposition)，或其他成员函数调用。

### <a name="return-value"></a>返回值

如果列表为**const**，`GetNext`返回列表的元素的副本。 这允许使用仅在赋值语句右侧的函数，并从修改保护列表。

如果该列表不是**const**，`GetNext`返回对列表的元素的引用。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

可以使用`GetNext`中如果建立调用一次的初始位置的向前迭代循环`GetHeadPosition`或`Find`。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

如果检索的元素的是在列表中，最后再的新值`rPosition`设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

获取标识的列表元素`rPosition`，然后设置`rPosition`列表的上一项的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定元素的类型。

*rPosition*<br/>
对先前返回的位置值的引用`GetPrev`或其他成员函数调用。

### <a name="return-value"></a>返回值

如果列表为**const**，`GetPrev`返回了列表的开头处的元素的副本。 这允许使用仅在赋值语句右侧的函数，并从修改保护列表。

如果该列表不是**const**，`GetPrev`返回对列表的元素的引用。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

可以使用`GetPrev`在反向迭代循环中，如果建立初始位置通过调用`GetTailPosition`或`Find`。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

如果检索的元素的为第一个在列表中，则新值的*rPosition*设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

返回列表的元素数。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

列表中的项数。

### <a name="remarks"></a>备注

调用此方法以检索列表中的元素数。  调用此方法将生成相同的结果[CList::GetCount](#getcount)方法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

获取`CObject`表示此列表的结尾元素的指针。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定元素的类型。

### <a name="return-value"></a>返回值

请参阅的返回值描述[GetHead](../../mfc/reference/coblist-class.md#gethead)。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

获取此列表; 结尾元素的位置如果列表为空，则为 NULL。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

在指定位置处的元素后添加到此列表的一个元素。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*position*<br/>
返回先前的位置值`GetNext`， `GetPrev`，或`Find`成员函数调用。

*ARG_TYPE*<br/>
指定列表元素的类型的模板参数。

*newElement*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可用于迭代或列表元素检索的位置值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

将元素添加到此列表中指定位置处的元素之前。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*position*<br/>
返回先前的位置值`GetNext`， `GetPrev`，或`Find`成员函数调用。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*newElement*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可用于迭代或列表元素检索的位置值。

### <a name="remarks"></a>备注

如果*位置*为 NULL，该元素插入到列表的开头。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

指示此列表是否包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此列表为空，则为非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

从此列表中移除所有元素，并释放关联的内存。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

如果列表已为空，则会不生成任何错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

此列表中移除指定的元素。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>参数

*position*<br/>
若要从列表中移除的元素的位置。

### <a name="remarks"></a>备注

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

从列表的开头移除的元素并返回的指针。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定元素的类型。

### <a name="return-value"></a>返回值

以前位于列表的开头处的元素。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

从列表的结尾移除的元素并返回的指针。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数列表中的指定元素的类型。

### <a name="return-value"></a>返回值

已在列表的结尾元素。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

位置类型的变量是列表的键。

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*pos*<br/>
若要设置的元素的位置。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*newElement*<br/>
要添加到列表的元素。

### <a name="remarks"></a>备注

不是索引，请与相同和您无法对位置值自己。 `SetAt` 将元素写入到列表中的指定位置。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMap 类](../../mfc/reference/cmap-class.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)
