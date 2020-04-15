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
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372234"
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

|名称|说明|
|----------|-----------------|
|[CList：CList](#clist)|构造一个空有序的列表。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CList：：添加头](#addhead)|将元素（或其他列表中的所有元素）添加到列表的头部（制作新头）。|
|[CList：：添加尾数](#addtail)|将元素（或其他列表中的所有元素）添加到列表的尾部（制作新尾部）。|
|[C列表：：查找](#find)|获取指针值指定的元素的位置。|
|[C 列表：查找索引](#findindex)|获取由零基索引指定的元素的位置。|
|[CList：获取At](#getat)|获取给定位置的元素。|
|[C 列表：获取计数](#getcount)|返回此列表中的元素数。|
|[C列表：获取头](#gethead)|返回列表的头元素（不能为空）。|
|[CList：获取头位置](#getheadposition)|返回列表头元素的位置。|
|[CList：获取下一个](#getnext)|获取下一个迭代元素。|
|[CList：GetPrev](#getprev)|获取用于迭代的前一个元素。|
|[C 列表：获取大小](#getsize)|返回此列表中的元素数。|
|[C列表：：获取尾数](#gettail)|返回列表的尾部元素（不能为空）。|
|[C 列表：：获取尾部位置](#gettailposition)|返回列表尾部元素的位置。|
|[CList：：插入后](#insertafter)|在给定位置后插入新元素。|
|[CList::InsertBefore](#insertbefore)|在给定位置之前插入新元素。|
|[CList：：空](#isempty)|测试空列表条件（无元素）。|
|[CList：：全部删除](#removeall)|从此列表中删除所有元素。|
|[CList：：删除AT](#removeat)|从此列表中删除由位置指定的元素。|
|[C 列表：：删除头](#removehead)|从列表的头部中删除元素。|
|[C 列表：：删除尾数](#removetail)|从列表尾部中删除元素。|
|[CList：：Setat](#setat)|将元素设置在给定位置。|

#### <a name="parameters"></a>参数

*类型*<br/>
存储在列表中的对象的类型。

*ARG_TYPE*<br/>
类型用于引用存储在列表中的对象。 可以是参考。

## <a name="remarks"></a>备注

`CList`列表类似于双链接列表。

位置类型的变量是列表的键。 可以使用位置变量作为迭代器按顺序遍历列表，也可以用作保留位置的书签。 但是，位置与索引不同。

元素插入在列表头、尾部和已知位置非常快速。 需要按值或索引查找元素的顺序搜索。 如果列表很长，则此搜索速度可能会很慢。

如果需要列表中单个元素的转储，则必须将转储上下文的深度设置为 1 或更大。

此类的某些成员函数调用全局帮助器函数，这些函数必须针对`CList`类的大多数用途进行自定义。 请参阅"宏和全局"部分中的[收集类帮助器](../../mfc/reference/collection-class-helpers.md)。

有关使用`CList`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList：：添加头

将新元素或元素列表添加到此列表的主管。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*新元素*<br/>
新元素。

*pNewlist*<br/>
指向另一个`CList`列表的指针。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>备注

在操作之前，列表可以为空。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList：：添加尾数

将新元素或元素列表添加到此列表的尾部。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*新元素*<br/>
要添加到此列表的元素。

*pNewlist*<br/>
指向另一个`CList`列表的指针。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>备注

在操作之前，列表可以为空。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList：CList

构造一个空有序的列表。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
用于扩展列表的内存分配粒度。

### <a name="remarks"></a>备注

随着列表的增长，内存以*nBlockSize*条目的单位分配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>C列表：：查找

按顺序搜索列表，以查找与指定*搜索值*匹配的第一个元素。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*搜索价值*<br/>
要在列表中找到的值。

*启动后*<br/>
搜索的开始位置。 如果未指定值，则搜索从头元素开始。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果未找到对象，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>C 列表：查找索引

将*nIndex*的值用作列表中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要找到的列表元素的零基索引。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果*nIndex*为负或太大，则为 NULL。

### <a name="remarks"></a>备注

它从列表的头部开始顺序扫描，在第*n*个元素上停止。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList：获取At

获取给定位置的列表元素。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定列表中的对象类型。

*位置*<br/>
要获取的元素列表中的位置。

### <a name="return-value"></a>返回值

请参阅`GetHead`的返回值说明。

### <a name="remarks"></a>备注

`GetAt`返回与给定位置关联的元素（或对元素的引用）。 它与索引不同，并且不能自己对位置值进行操作。 位置类型的变量是列表的键。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

  请参阅[CList 示例：获取头位置](#getheadposition)。

## <a name="clistgetcount"></a><a name="getcount"></a>C 列表：获取计数

获取此列表中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

包含元素计数的整数值。

### <a name="remarks"></a>备注

调用此方法将生成与[CList：getSize](#getsize)方法相同的结果。

### <a name="example"></a>示例

  请参阅[CList 示例：：删除头](#removehead)。

## <a name="clistgethead"></a><a name="gethead"></a>C列表：获取头

获取此列表的头元素（或对头元素的引用）。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定列表中的对象类型。

### <a name="return-value"></a>返回值

如果列表是**const，**`GetHead`则返回列表头的元素的副本。 这允许函数仅在赋值语句的右侧使用，并保护列表不进行修改。

如果列表不是**const，**`GetHead`则返回对列表头的元素的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

在调用`GetHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList：获取头位置

获取此列表头元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList：获取下一个

获取*r定位*标识的列表元素，然后将*r定位*设置到列表中下一个条目的"位置"值。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定列表中元素的类型。

*r定位*<br/>
对前`GetNext`一个[（GetHead定位](#getheadposition)） 或其他成员函数调用返回的定位值的引用。

### <a name="return-value"></a>返回值

如果列表是**const** `GetNext` ，则返回列表元素的副本。 这允许函数仅在赋值语句的右侧使用，并保护列表不进行修改。

如果列表不是**const**，`GetNext`则返回对列表元素的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

如果使用`GetNext`调用`GetHeadPosition`或`Find`建立初始位置，则可以在转发迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的最后一个元素，则 的新`rPosition`值将设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList：GetPrev

获取 标识`rPosition`的列表元素，然后设置`rPosition`到列表中上一个条目的"位置"值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定列表中元素的类型。

*r定位*<br/>
对前`GetPrev`一个成员或其他成员函数调用返回的定位值的引用。

### <a name="return-value"></a>返回值

如果列表是**const，**`GetPrev`则返回列表头的元素的副本。 这允许函数仅在赋值语句的右侧使用，并保护列表不进行修改。

如果列表不是**const**，`GetPrev`则返回对列表元素的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

如果使用`GetPrev`调用`GetTailPosition`或`Find`建立初始位置，则可以在反向迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的第一个元素，则*rValue*的新值将设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>C 列表：获取大小

返回列表元素的数量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

列表中的项数。

### <a name="remarks"></a>备注

调用此方法以检索列表中的元素数。  调用此方法将生成与[CList：：GetCount](#getcount)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>C列表：：获取尾数

获取`CObject`表示此列表尾部元素的指针。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

请参阅[GetHead](../../mfc/reference/coblist-class.md#gethead)的返回值说明。

### <a name="remarks"></a>备注

在调用`GetTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>C 列表：：获取尾部位置

获取此列表尾部元素的位置;如果列表为空，则为 NULL。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList：：插入后

在指定位置的元素之后向此列表添加元素。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*位置*<br/>
由前`GetNext`一个 、`GetPrev`或`Find`成员函数调用返回的定位值。

*ARG_TYPE*<br/>
指定列表元素类型的模板参数。

*新元素*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可以用于迭代或列表元素检索的位置值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList：：插入之前

将元素添加到此列表中指定位置处的元素之前。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*位置*<br/>
由前`GetNext`一个 、`GetPrev`或`Find`成员函数调用返回的定位值。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*新元素*<br/>
要添加到此列表的元素。

### <a name="return-value"></a>返回值

一个可以用于迭代或列表元素检索的位置值。

### <a name="remarks"></a>备注

如果*位置*为 NULL，则元素将插入到列表的头部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList：：空

指示此列表是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此列表为空，则为非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList：：全部删除

从此列表中删除所有元素并释放关联的内存。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

如果列表已为空，则不生成错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList：：删除AT

从该列表中删除指定的元素。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>参数

*位置*<br/>
要从列表中删除的元素的位置。

### <a name="remarks"></a>备注

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>C 列表：：删除头

从列表的头部删除元素并返回指向该元素的指针。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

以前位于列表头的元素。

### <a name="remarks"></a>备注

在调用`RemoveHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>C 列表：：删除尾数

从列表的尾部删除元素，并返回指向该元素的指针。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>参数

*类型*<br/>
指定列表中元素类型的模板参数。

### <a name="return-value"></a>返回值

位于列表尾部的元素。

### <a name="remarks"></a>备注

在调用`RemoveTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList：：Setat

位置类型的变量是列表的键。

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*Pos*<br/>
要设置的元素的位置。

*ARG_TYPE*<br/>
用于指定列表元素类型的模板参数（可以为一个引用）。

*新元素*<br/>
要添加到列表中的元素。

### <a name="remarks"></a>备注

它与索引不同，并且不能自己对位置值进行操作。 `SetAt`将元素写入列表中的指定位置。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMap 类](../../mfc/reference/cmap-class.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)
