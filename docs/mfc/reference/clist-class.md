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
ms.openlocfilehash: 7ba85445e3aba1df853d7d3666c92fdabdfa3970
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182871"
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
|[CList：： CList](#clist)|构造一个空的排序列表。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CList：： AddHead](#addhead)|将一个元素（或另一个列表中的所有元素）添加到列表的开头（构成一个新头）。|
|[CList：： AddTail](#addtail)|将一个元素（或另一个列表中的所有元素）添加到列表的尾部（生成新的尾部）。|
|[CList：： Find](#find)|获取由指针值指定的元素的位置。|
|[CList：： FindIndex](#findindex)|获取以零为基的索引指定的元素的位置。|
|[CList：： GetAt](#getat)|获取给定位置处的元素。|
|[CList：： GetCount](#getcount)|返回此列表中的元素数。|
|[CList：： GetHead](#gethead)|返回列表的 head 元素（不能为空）。|
|[CList：： GetHeadPosition](#getheadposition)|返回列表头元素的位置。|
|[CList：： GetNext](#getnext)|获取用于循环访问的下一个元素。|
|[CList：： GetPrev](#getprev)|获取用于循环访问的上一个元素。|
|[CList：： GetSize](#getsize)|返回此列表中的元素数。|
|[CList：： GetTail](#gettail)|返回列表的尾元素（不能为空）。|
|[CList：： GetTailPosition](#gettailposition)|返回列表的尾元素的位置。|
|[CList：： InsertAfter](#insertafter)|将新元素插入到给定位置之后。|
|[CList::InsertBefore](#insertbefore)|将新元素插入到给定位置之前。|
|[CList：： IsEmpty](#isempty)|测试空列表条件（无元素）。|
|[CList：： RemoveAll](#removeall)|从此列表中移除所有元素。|
|[CList：： RemoveAt](#removeat)|从此列表中移除按位置指定的元素。|
|[CList：： RemoveHead](#removehead)|从列表头中删除元素。|
|[CList：： RemoveTail](#removetail)|从列表的末尾移除元素。|
|[CList：： SetAt](#setat)|设置位于给定位置的元素。|

#### <a name="parameters"></a>参数

*TYPE*<br/>
列表中存储的对象的类型。

*ARG_TYPE*<br/>
用于引用存储在列表中的对象的类型。 可以是引用。

## <a name="remarks"></a>备注

`CList`列表的行为类似于双向链接列表。

POSITION 类型的变量是列表的键。 您可以使用 POSITION 变量作为迭代器来按顺序遍历列表，并将其作为书签来保存位置。 但位置不同于索引。

元素插入速度非常快，在列表头、尾部和已知位置。 需要顺序搜索按值或索引查找元素。 如果列表很长，则此搜索可能会很慢。

如果需要转储列表中的各个元素，则必须将转储上下文的深度设置为1或更大。

此类的某些成员函数调用全局 helper 函数，这些函数必须针对该类的大多数用途进行自定义 `CList` 。 请参阅 "宏和全局" 部分中的[集合类帮助](../../mfc/reference/collection-class-helpers.md)器。

有关使用的详细信息 `CList` ，请参阅文章[集合](../../mfc/collections.md)。

## <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList：： AddHead

将一个或一组新元素添加到此列表的开头。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*（Newelement*<br/>
新元素。

*pNewList*<br/>
指向其他列表的指针 `CList` 。 *PNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入元素的位置值。

### <a name="remarks"></a>备注

此列表在操作之前可以为空。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList：： AddTail

将一个或一组新元素添加到此列表的尾部。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*（Newelement*<br/>
要添加到此列表的元素。

*pNewList*<br/>
指向其他列表的指针 `CList` 。 *PNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入元素的位置值。

### <a name="remarks"></a>备注

此列表在操作之前可以为空。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList：： CList

构造一个空的排序列表。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
用于扩展列表的内存分配粒度。

### <a name="remarks"></a>备注

随着列表的增长，内存是以*nBlockSize*项的单位分配的。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList：： Find

按顺序搜索列表以查找与指定*searchValue*匹配的第一个元素。

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
搜索的起始位置。 如果未指定任何值，则搜索将以 head 元素开头。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果找不到该对象，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList：： FindIndex

使用*nIndex*的值作为列表中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要查找的列表元素的从零开始的索引。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果*nIndex*为负或过大，则为 NULL。

### <a name="remarks"></a>备注

它从列表的开头开始顺序扫描，在第*n*个元素处停止。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList：： GetAt

获取给定位置处的列表元素。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中的对象类型的模板参数。

*置于*<br/>
要获取的元素在列表中的位置。

### <a name="return-value"></a>返回值

请参阅的返回值说明 `GetHead` 。

### <a name="remarks"></a>备注

`GetAt`返回与给定位置关联的元素（或对元素的引用）。 它与索引不同，不能自行操作位置值。 POSITION 类型的变量是列表的键。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

### <a name="example"></a>示例

  请参阅[CList：： GetHeadPosition](#getheadposition)的示例。

## <a name="clistgetcount"></a><a name="getcount"></a>CList：： GetCount

获取此列表中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

一个包含元素计数的整数值。

### <a name="remarks"></a>备注

调用此方法将生成与[CList：： GetSize](#getsize)方法相同的结果。

### <a name="example"></a>示例

  请参阅[CList：： RemoveHead](#removehead)的示例。

## <a name="clistgethead"></a><a name="gethead"></a>CList：： GetHead

获取此列表的头元素（或对头元素的引用）。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中的对象类型的模板参数。

### <a name="return-value"></a>返回值

如果列表为 **`const`** ，则 `GetHead` 返回该列表头中的元素的副本。 这只允许将函数用于赋值语句右侧，并防止修改列表。

如果列表不为 **`const`** ，则 `GetHead` 返回对列表开头的元素的引用。 这允许将函数用于赋值语句的任意一侧，从而允许修改列表项。

### <a name="remarks"></a>备注

在调用之前，必须确保列表不为空 `GetHead` 。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList：： GetHeadPosition

获取此列表的头元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList：： GetNext

获取由*rPosition*标识的列表元素，然后将*rPosition*设置为列表中下一项的位置值。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中元素类型的模板参数。

*rPosition*<br/>
对由 previous `GetNext` 、 [GetHeadPosition](#getheadposition)或其他成员函数调用返回的位置值的引用。

### <a name="return-value"></a>返回值

如果列表为 **`const`** ，则 `GetNext` 返回列表中元素的副本。 这只允许将函数用于赋值语句右侧，并防止修改列表。

如果列表不为 **`const`** ，则 `GetNext` 返回对列表中元素的引用。 这允许将函数用于赋值语句的任意一侧，从而允许修改列表项。

### <a name="remarks"></a>备注

`GetNext`如果使用或调用建立初始位置，则可以在向前迭代循环中使用 `GetHeadPosition` `Find` 。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

如果检索到的元素是列表中的最后一个，则的新值将 `rPosition` 设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList：： GetPrev

获取由标识的列表元素 `rPosition` ，然后将设置 `rPosition` 为列表中上一项的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中元素类型的模板参数。

*rPosition*<br/>
对上一个 `GetPrev` 或其他成员函数调用返回的位置值的引用。

### <a name="return-value"></a>返回值

如果列表为 **`const`** ，则 `GetPrev` 返回该列表头中的元素的副本。 这只允许将函数用于赋值语句右侧，并防止修改列表。

如果列表不为 **`const`** ，则 `GetPrev` 返回对列表中元素的引用。 这允许将函数用于赋值语句的任意一侧，从而允许修改列表项。

### <a name="remarks"></a>备注

`GetPrev`如果使用或调用建立初始位置，则可以在反向迭代循环中使用 `GetTailPosition` `Find` 。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

如果检索到的元素是列表中的第一个元素，则*rPosition*的新值将设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList：： GetSize

返回列表元素的数目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

列表中的项数。

### <a name="remarks"></a>备注

调用此方法可检索列表中的元素数。  调用此方法将生成与[CList：： GetCount](#getcount)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList：： GetTail

获取 `CObject` 表示此列表的尾元素的指针。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

请参阅[GetHead](../../mfc/reference/coblist-class.md#gethead)的返回值说明。

### <a name="remarks"></a>备注

在调用之前，必须确保列表不为空 `GetTail` 。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList：： GetTailPosition

获取此列表的尾元素的位置;如果列表为空，则为 NULL。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList：： InsertAfter

将元素添加到此列表中位于指定位置的元素之后。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*置于*<br/>
先前的 `GetNext` 、 `GetPrev` 或 `Find` 成员函数调用返回的位置值。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数。

*（Newelement*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可以用于迭代或列表元素检索的位置值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList：： InsertBefore

将元素添加到此列表中指定位置处的元素之前。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*置于*<br/>
先前的 `GetNext` 、 `GetPrev` 或 `Find` 成员函数调用返回的位置值。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*（Newelement*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可以用于迭代或列表元素检索的位置值。

### <a name="remarks"></a>备注

如果*position*为 NULL，则将元素插入到列表的开头。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList：： IsEmpty

指示此列表是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此列表为空，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList：： RemoveAll

删除此列表中的所有元素并释放关联的内存。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果该列表已为空，则不会生成任何错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList：： RemoveAt

从此列表中移除指定的元素。

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>参数

*置于*<br/>
要从列表中移除的元素的位置。

### <a name="remarks"></a>备注

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList：： RemoveHead

从列表的开头移除元素，并返回指向它的指针。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

之前位于列表开头的元素。

### <a name="remarks"></a>备注

在调用之前，必须确保列表不为空 `RemoveHead` 。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList：： RemoveTail

删除列表末尾的元素，并返回指向它的指针。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

位于列表末尾的元素。

### <a name="remarks"></a>备注

在调用之前，必须确保列表不为空 `RemoveTail` 。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList：： SetAt

POSITION 类型的变量是列表的键。

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*位置*<br/>
要设置的元素的位置。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*（Newelement*<br/>
要添加到列表中的元素。

### <a name="remarks"></a>备注

它与索引不同，不能自行操作位置值。 `SetAt`将元素写入列表中的指定位置。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMap 类](../../mfc/reference/cmap-class.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)
