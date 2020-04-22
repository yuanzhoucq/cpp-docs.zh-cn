---
title: COblist 类
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749684"
---
# <a name="coblist-class"></a>COblist 类

f 支持按顺序或按`CObject`指针值可访问的非唯一指针的有序列表。

## <a name="syntax"></a>语法

```
class CObList : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COblist：COblist](#coblist)|为`CObject`指针构造空列表。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COblist：：添加头](#addhead)|将元素（或其他列表中的所有元素）添加到列表的头部（制作新头）。|
|[COblist：：添加尾数](#addtail)|将元素（或其他列表中的所有元素）添加到列表的尾部（制作新尾部）。|
|[CObList：查找](#find)|获取指针值指定的元素的位置。|
|[COblist：查找索引](#findindex)|获取由零基索引指定的元素的位置。|
|[COblist：：获取At](#getat)|获取给定位置的元素。|
|[COblist：获取计数](#getcount)|返回此列表中的元素数。|
|[COblist：获取头](#gethead)|返回列表的头元素（不能为空）。|
|[COblist：获取头位置](#getheadposition)|返回列表头元素的位置。|
|[COblist：获取下一个](#getnext)|获取下一个迭代元素。|
|[COblist：GetPrev](#getprev)|获取用于迭代的前一个元素。|
|[COblist：获取 Size](#getsize)|返回此列表中的元素数。|
|[COblist：获取尾翼](#gettail)|返回列表的尾部元素（不能为空）。|
|[COblist：：获取尾部位置](#gettailposition)|返回列表尾部元素的位置。|
|[COblist：：插入后](#insertafter)|在给定位置后插入新元素。|
|[COblist：：插入之前](#insertbefore)|在给定位置之前插入新元素。|
|[COblist：：是空的](#isempty)|测试空列表条件（无元素）。|
|[COblist：：删除所有](#removeall)|从此列表中删除所有元素。|
|[COblist：：删除At](#removeat)|从此列表中删除由位置指定的元素。|
|[COblist：：删除头](#removehead)|从列表的头部中删除元素。|
|[COblist：：删除尾带](#removetail)|从列表尾部中删除元素。|
|[COblist：：Setat](#setat)|将元素设置在给定位置。|

## <a name="remarks"></a>备注

`CObList`列表类似于双链接列表。

位置类型的变量是列表的键。 可以使用位置变量作为迭代器按顺序遍历列表，也可以用作保留位置的书签。 但是，位置与索引不同。

元素插入在列表头、尾部和已知位置非常快速。 需要按值或索引查找元素的顺序搜索。 如果列表很长，则此搜索速度可能会很慢。

`CObList`合并IMPLEMENT_SERIAL宏以支持其元素的序列化和转储。 如果将`CObject`指针列表存储到存档（使用重载插入运算符或`Serialize`成员函数）时，则依次序列化每个`CObject`元素。

如果需要列表中单个`CObject`元素的转储，则必须将转储上下文的深度设置为 1 或更大。

删除`CObList`对象或删除其元素时，将仅删除`CObject`指针，而不是删除它们引用的对象。

可以从 派生`CObList`您自己的类。 新的列表类，旨在保存指向派生自`CObject`的对象的指针，添加新的数据成员和新成员函数。 请注意，生成的列表不是严格键入安全，因为它允许插入任何`CObject`指针。

> [!NOTE]
> 如果要序列化列表，则必须在派生类的实现中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

有关使用`CObList`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>COblist：：添加头

将新元素或元素列表添加到此列表的主管。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>参数

*新元素*<br/>
要`CObject`添加到此列表的指针。

*pNewlist*<br/>
指向另一个`CObList`列表的指针。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

下表显示了与`CObList::AddHead`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置添加头（空**<strong>\*</strong>`newElement`**）;**<br /><br /> **空添加头（ CPtrlist）;** <strong>\*</strong> `pNewList` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置添加头（cString&** `newElement` **）;**<br /><br /> **位置加头（LPCTSTR）;** `newElement` **);**<br /><br /> **无效添加头（CStringlist）;** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>备注

在操作之前，列表可以为空。

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

此程序的结果如下：

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>COblist：：添加尾数

将新元素或元素列表添加到此列表的尾部。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>参数

*新元素*<br/>
要`CObject`添加到此列表的指针。

*pNewlist*<br/>
指向另一个`CObList`列表的指针。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>备注

在操作之前，列表可以为空。

下表显示了与`CObList::AddTail`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置添加尾数（空**<strong>\*</strong>`newElement`**）;**<br /><br /> **虚无添加目录（CPtrlist）;** <strong>\*</strong> `pNewList` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置添加尾数（const CString&** `newElement` **）;**<br /><br /> **位置加尾（LPCTSTR）;** `newElement` **);**<br /><br /> **虚无添加尾数（CStringlist）;** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

此程序的结果如下：

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>COblist：COblist

构造空`CObject`指针列表。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
用于扩展列表的内存分配粒度。

### <a name="remarks"></a>备注

随着列表的增长，内存以*nBlockSize*条目的单位分配。 如果内存分配失败，将引发`CMemoryException`。

下表显示了与`CObList::CObList`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList（INT_PTR** `nBlockSize` **= 10 ）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CStringlist（INT_PTR** `nBlockSize` **= 10 ）;**|

### <a name="example"></a>示例

  下面是所有集合示例中使用的`CObject`派生类`CAge`的列表：

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

下面是`CObList`构造函数使用的示例：

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CObList：查找

按顺序搜索列表以查找与指定`CObject``CObject`指针匹配的第一个指针。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>参数

*搜索价值*<br/>
要在此列表中找到的对象指针。

*启动后*<br/>
搜索的开始位置。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果未找到对象，则为 NULL。

### <a name="remarks"></a>备注

请注意，将比较指针值，而不是对象的内容。

下表显示了与`CObList::Find`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 查找（空**<strong>\*</strong>`searchValue`**隙、位置**`startAfter` **= 空） 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置查找（LPCTSTR，**`searchValue`**位置**`startAfter` **= NULL）const;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>COblist：查找索引

将*nIndex*的值用作列表中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要找到的列表元素的零基索引。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果*nIndex*太大，则为 NULL。 （如果*nIndex*为负，则框架将生成断言。

### <a name="remarks"></a>备注

它从列表的头部开始顺序扫描，在第*n*个元素上停止。

下表显示了与`CObList::FindIndex`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置查找索引（ INT_PTR** `nIndex` **） 康斯特;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置查找索引（ INT_PTR** `nIndex` **） 康斯特;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>COblist：：获取At

位置类型的变量是列表的键。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
由上一个`GetHeadPosition`或`Find`成员函数调用返回的定位值。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

它与索引不同，并且不能自己对位置值进行操作。 `GetAt`检索与`CObject`给定位置关联的指针。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

下表显示了与`CObList::GetAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&空隙\*（ 位置***position***位置） 同;**<br /><br /> **空\*&获取（位置***位置***）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**const CString&获取位置***position***位置）**<br /><br /> **CString&获取位置***position***）;**|

### <a name="example"></a>示例

  请参阅[FindIndex](#findindex)的示例。

## <a name="coblistgetcount"></a><a name="getcount"></a>COblist：获取计数

获取此列表中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

包含元素计数的整数值。

下表显示了与`CObList::GetCount`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR获取计数（ ） const;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**INT_PTR获取计数（ ） const;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>COblist：获取头

获取`CObject`表示此列表头元素的指针。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>返回值

如果列表通过指向 的`const CObList`指针访问，则`GetHead`返回一个`CObject`指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的`CObList`指针访问列表，则`GetHead`返回对指针的`CObject`引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

在调用`GetHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

下表显示了与`CObList::GetHead`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&获取头\*的空隙;空\*&拿头（ ）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**康斯特·克斯特林&获取头（ ） const;CString&获取头（ ）;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

下面的示例说明了赋值语句左侧`GetHead`的使用。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>COblist：获取头位置

获取此列表头元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

下表显示了与`CObList::GetHeadPosition`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置获取头位置（ ） 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置获取头位置（ ） 同;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>COblist：获取下一个

获取*r定位*标识的列表元素，然后将*r定位*设置到列表中`POSITION`下一个条目的值。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*r定位*<br/>
对前`GetNext``GetHeadPosition`一个成员函数调用返回的"位置"值的引用。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

如果使用`GetNext`调用`GetHeadPosition`或`Find`建立初始位置，则可以在转发迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的最后一个元素，则*rValue*的新值将设置为 NULL。

可以在迭代期间删除元素。 请参阅[RemoveAt](#removeat)的示例。

> [!NOTE]
> 从 MFC 8.0 开始，此方法的 const 版本`const CObject*`已更改为`const CObject*&`返回而不是 。  进行此更改是为了使编译器符合C++标准。

下表显示了与`CObList::GetNext`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

此程序的结果如下：

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>COblist：GetPrev

获取*rPosition*标识的列表元素，然后将*r定位*设置到列表中上一个条目的"位置"值。

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*r定位*<br/>
对前`GetPrev`一个成员或其他成员函数调用返回的定位值的引用。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

如果使用`GetPrev`调用`GetTailPosition`或`Find`建立初始位置，则可以在反向迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的第一个元素，则*rValue*的新值将设置为 NULL。

> [!NOTE]
> 从 MFC 8.0 开始，此方法的 const 版本`const CObject*`已更改为`const CObject*&`返回而不是 。  进行此更改是为了使编译器符合C++标准。

下表显示了与`CObList::GetPrev`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

此程序的结果如下：

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>COblist：获取 Size

返回列表元素的数量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

列表中的项数。

### <a name="remarks"></a>备注

调用此方法以检索列表中的元素数。

下表显示了与`CObList::GetSize`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR获取大小（ ） const;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**INT_PTR获取大小（ ） const;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>COblist：获取尾翼

获取`CObject`表示此列表尾部元素的指针。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

在调用`GetTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

下表显示了与`CObList::GetTail`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&获取的\*空隙;空\*&拿太子;（**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**康斯特CString&获取泰斯特;CString&GetTail（）;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>COblist：：获取尾部位置

获取此列表尾部元素的位置;如果列表为空，**则为 NULL。**

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

下表显示了与`CObList::GetTailPosition`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置获取位置（ ） 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置获取位置（ ） 同;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>COblist：：插入后

在指定位置的元素之后向此列表添加元素。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*位置*<br/>
由前`GetNext`一个 、`GetPrev`或`Find`成员函数调用返回的定位值。

*新元素*<br/>
要添加到此列表的对象指针。

下表显示了与`CObList::InsertAfter`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置插入后（位置***位置***，空隙**<strong>\*</strong>`newElement`**）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置插入后（位置***位置***，康斯特CString&）;** `newElement` **);**<br /><br /> **位置插入后（位置***位置***，LPCTSTR）;** `newElement` **);**|

### <a name="return-value"></a>返回值

与*位置*参数相同的位置值。

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

此程序的结果如下：

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>COblist：：插入之前

将元素添加到此列表中指定位置处的元素之前。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*位置*<br/>
由前`GetNext`一个 、`GetPrev`或`Find`成员函数调用返回的定位值。

*新元素*<br/>
要添加到此列表的对象指针。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

下表显示了与`CObList::InsertBefore`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置插入之前（位置***位置***，空隙**<strong>\*</strong>`newElement`**）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置插入之前（位置***位置***，const CString&）;** `newElement` **);**<br /><br /> **位置插入之前（位置***位置***，LPCTSTR）;** `newElement` **);**|

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

此程序的结果如下：

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>COblist：：是空的

指示此列表是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此列表为空，则为非零;否则 0。

下表显示了与`CObList::IsEmpty`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**BOOL 是空的（ ） 康斯特;**|

### <a name="example"></a>示例

  请参阅[删除所有](#removeall)的示例。

## <a name="coblistremoveall"></a><a name="removeall"></a>COblist：：删除所有

从此列表中删除所有元素并释放关联的`CObList`内存。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果列表已为空，则不生成错误。

从 中删除 元素时`CObList`，将从列表中删除对象指针。 您有责任删除对象本身。

下表显示了与`CObList::RemoveAll`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**无效删除所有（ ）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**无效删除所有（ ）;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>COblist：：删除At

从该列表中删除指定的元素。

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>参数

*位置*<br/>
要从列表中删除的元素的位置。

### <a name="remarks"></a>备注

从 中删除 元素时`CObList`，将从列表中删除对象指针。 您有责任删除对象本身。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

下表显示了与`CObList::RemoveAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**空删除At（位置***位置***）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**空删除At（位置***位置***）;**|

### <a name="example"></a>示例

  在列表迭代期间删除元素时要小心。 下面的示例显示了一种删除技术，该技术保证[GetNext](#getnext)的有效**位置**值。

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

此程序的结果如下：

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>COblist：：删除头

从列表的头部删除元素并返回指向该元素的指针。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>返回值

以前`CObject`位于列表头的指针。

### <a name="remarks"></a>备注

在调用`RemoveHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

下表显示了与`CObList::RemoveHead`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**无效\*删除头（）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CString 删除头（）;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>COblist：：删除尾带

从列表的尾部删除元素，并返回指向该元素的指针。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>返回值

指向列表尾部的对象的指针。

### <a name="remarks"></a>备注

在调用`RemoveTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表是否包含元素。

下表显示了与`CObList::RemoveTail`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**无效\*去除尾数（）;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CString 删除尾带（）;**|

### <a name="example"></a>示例

有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>COblist：：Setat

将元素设置在给定位置。

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*Pos*<br/>
要设置的元素的位置。

*新元素*<br/>
要`CObject`写入列表的指针。

### <a name="remarks"></a>备注

位置类型的变量是列表的键。 它与索引不同，并且不能自己对位置值进行操作。 `SetAt`将`CObject`指针写入列表中的指定位置。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

下表显示了与`CObList::SetAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**空设置（位置**`pos`**，const CString&）;** `newElement` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**空位（位置**`pos`**，LPCTSTR）;** `newElement` **);**|

### <a name="example"></a>示例

  有关`CAge`类的列表，请参阅[CObList：CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

此程序的结果如下：

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CStringList 类](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList 类](../../mfc/reference/cptrlist-class.md)
