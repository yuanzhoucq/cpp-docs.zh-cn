---
title: CObList 类
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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424031"
---
# <a name="coblist-class"></a>CObList 类

可按顺序或指针值访问的不唯一 `CObject` 指针的 fSupports 排序列表。

## <a name="syntax"></a>语法

```
class CObList : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CObList：： CObList](#coblist)|为 `CObject` 指针构造一个空列表。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CObList：： AddHead](#addhead)|将一个元素（或另一个列表中的所有元素）添加到列表的开头（构成一个新头）。|
|[CObList：： AddTail](#addtail)|将一个元素（或另一个列表中的所有元素）添加到列表的尾部（生成新的尾部）。|
|[CObList：： Find](#find)|获取由指针值指定的元素的位置。|
|[CObList：： FindIndex](#findindex)|获取以零为基的索引指定的元素的位置。|
|[CObList：： GetAt](#getat)|获取给定位置处的元素。|
|[CObList：： GetCount](#getcount)|返回此列表中的元素数。|
|[CObList：： GetHead](#gethead)|返回列表的 head 元素（不能为空）。|
|[CObList：： GetHeadPosition](#getheadposition)|返回列表头元素的位置。|
|[CObList：： GetNext](#getnext)|获取用于循环访问的下一个元素。|
|[CObList：： GetPrev](#getprev)|获取用于循环访问的上一个元素。|
|[CObList：： GetSize](#getsize)|返回此列表中的元素数。|
|[CObList：： GetTail](#gettail)|返回列表的尾元素（不能为空）。|
|[CObList：： GetTailPosition](#gettailposition)|返回列表的尾元素的位置。|
|[CObList：： InsertAfter](#insertafter)|将新元素插入到给定位置之后。|
|[CObList：： InsertBefore](#insertbefore)|将新元素插入到给定位置之前。|
|[CObList：： IsEmpty](#isempty)|测试空列表条件（无元素）。|
|[CObList：： RemoveAll](#removeall)|从此列表中移除所有元素。|
|[CObList：： RemoveAt](#removeat)|从此列表中移除按位置指定的元素。|
|[CObList：： RemoveHead](#removehead)|从列表头中删除元素。|
|[CObList：： RemoveTail](#removetail)|从列表的末尾移除元素。|
|[CObList：： SetAt](#setat)|设置位于给定位置的元素。|

## <a name="remarks"></a>备注

`CObList` 列表的行为类似于双向链接列表。

POSITION 类型的变量是列表的键。 您可以使用 POSITION 变量作为迭代器来按顺序遍历列表，并将其作为书签来保存位置。 但位置不同于索引。

元素插入速度非常快，在列表头、尾部和已知位置。 需要顺序搜索按值或索引查找元素。 如果列表很长，则此搜索可能会很慢。

`CObList` 包含 IMPLEMENT_SERIAL 宏，以支持其元素的序列化和转储。 如果使用重载的插入运算符或使用 `Serialize` 成员函数将 `CObject` 指针的列表存储到存档中，则每个 `CObject` 元素将依次序列化。

如果需要转储列表中单个 `CObject` 元素，则必须将转储上下文的深度设置为1或更大。

删除 `CObList` 对象或删除其元素时，只会删除 `CObject` 的指针，而不会删除它们引用的对象。

你可以从 `CObList`派生你自己的类。 新的列表类，旨在保存指向派生自 `CObject`的对象的指针，并添加新的数据成员和新的成员函数。 请注意，结果列表并不是严格类型安全的，因为它允许插入任何 `CObject` 指针。

> [!NOTE]
>  如果打算序列化列表，则必须在派生类的实现中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

有关使用 `CObList`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

##  <a name="addhead"></a>CObList：： AddHead

将一个或一组新元素添加到此列表的开头。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>parameters

*（Newelement*<br/>
要添加到此列表中的 `CObject` 指针。

*pNewList*<br/>
指向另一个 `CObList` 列表的指针。 *PNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入元素的位置值。

下表显示了类似于 `CObList::AddHead`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead （void** <strong>\*</strong> `newElement` **）;**<br /><br /> **Void AddHead （CPtrList** <strong>\*</strong> `pNewList` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead （Const CString &** `newElement` **）;**<br /><br /> **POSITION AddHead （LPCTSTR** `newElement` **）;**<br /><br /> **Void AddHead （CStringList** <strong>\*</strong> `pNewList` **）;**|

### <a name="remarks"></a>备注

此列表在操作之前可以为空。

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

此程序的结果如下所示：

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList：： AddTail

将一个或一组新元素添加到此列表的尾部。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>parameters

*（Newelement*<br/>
要添加到此列表中的 `CObject` 指针。

*pNewList*<br/>
指向另一个 `CObList` 列表的指针。 *PNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入元素的位置值。

### <a name="remarks"></a>备注

此列表在操作之前可以为空。

下表显示了类似于 `CObList::AddTail`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail （void** <strong>\*</strong> `newElement` **）;**<br /><br /> **Void AddTail （CPtrList** <strong>\*</strong> `pNewList` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail （Const CString &** `newElement` **）;**<br /><br /> **POSITION AddTail （LPCTSTR** `newElement` **）;**<br /><br /> **Void AddTail （CStringList** <strong>\*</strong> `pNewList` **）;**|

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

此程序的结果如下所示：

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList：： CObList

构造空的 `CObject` 指针列表。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>parameters

*nBlockSize*<br/>
用于扩展列表的内存分配粒度。

### <a name="remarks"></a>备注

随着列表的增长，内存是以*nBlockSize*项的单位分配的。 如果内存分配失败，则会引发 `CMemoryException`。

下表显示了类似于 `CObList::CObList`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList （INT_PTR** `nBlockSize` **= 10）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList （INT_PTR** `nBlockSize` **= 10）;**|

### <a name="example"></a>示例

  下面是 `CObject`派生类的列表，`CAge` 用于所有集合示例：

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

下面是 `CObList` 构造函数用法的示例：

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList：： Find

按顺序搜索列表，查找与指定 `CObject` 指针匹配的第一个 `CObject` 指针。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>parameters

*searchValue*<br/>
要在此列表中找到的对象指针。

*startAfter*<br/>
搜索的起始位置。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果找不到该对象，则为 NULL。

### <a name="remarks"></a>备注

请注意，将对指针值进行比较，而不是对象的内容。

下表显示了类似于 `CObList::Find`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position Find （void** <strong>\*</strong> `searchValue` **，position** `startAfter` **= NULL） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position Find （LPCTSTR** `searchValue` **，Position** `startAfter` **= NULL） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList：： FindIndex

使用*nIndex*的值作为列表中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要查找的列表元素的从零开始的索引。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果*nIndex*太大，则为 NULL。 （如果*nIndex*为负，则框架将生成一个断言。）

### <a name="remarks"></a>备注

它从列表的开头开始顺序扫描，在第*n*个元素处停止。

下表显示了类似于 `CObList::FindIndex`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex （INT_PTR** `nIndex` **） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex （INT_PTR** `nIndex` **） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList：： GetAt

POSITION 类型的变量是列表的键。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>parameters

*position*<br/>
先前 `GetHeadPosition` 或 `Find` 成员函数调用返回的位置值。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

它与索引不同，不能自行操作位置值。 `GetAt` 检索与给定位置关联的 `CObject` 指针。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

下表显示了类似于 `CObList::GetAt`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt （位置***位置* **） const;**<br /><br /> **void\*& GetAt （位置***位置* **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**常量 CString & GetAt （位置***位置* **） const;**<br /><br /> **CString & GetAt （位置***位置* **）;**|

### <a name="example"></a>示例

  请参阅[FindIndex](#findindex)的示例。

##  <a name="getcount"></a>CObList：： GetCount

获取此列表中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

一个包含元素计数的整数值。

下表显示了类似于 `CObList::GetCount`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList：： GetHead

获取表示此列表头元素的 `CObject` 指针。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>返回值

如果通过指向 `const CObList`的指针访问列表，则 `GetHead` 返回 `CObject` 指针。 这只允许在赋值语句右侧使用该函数，从而保护列表不被修改。

如果直接访问该列表或通过指向 `CObList`的指针访问该列表，则 `GetHead` 返回对 `CObject` 指针的引用。 这允许将函数用于赋值语句的任意一侧，从而允许修改列表项。

### <a name="remarks"></a>备注

在调用 `GetHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

下表显示了类似于 `CObList::GetHead`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead （） const;void\*& GetHead （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead （） const;CString & GetHead （）;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

下面的示例阐释了如何在赋值语句左侧使用 `GetHead`。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList：： GetHeadPosition

获取此列表的头元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

下表显示了类似于 `CObList::GetHeadPosition`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition （） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList：： GetNext

获取由*rPosition*标识的列表元素，然后将*rPosition*设置为列表中下一项的 `POSITION` 值。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>parameters

*rPosition*<br/>
对由上一个 `GetNext`、`GetHeadPosition`或其他成员函数调用返回的位置值的引用。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

如果通过调用 `GetHeadPosition` 或 `Find`建立初始位置，则可以在向前迭代循环中使用 `GetNext`。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

如果检索到的元素是列表中的最后一个，则*rPosition*的新值将设置为 NULL。

可以在迭代期间删除某个元素。 请参阅[RemoveAt](#removeat)的示例。

> [!NOTE]
>  从 MFC 8.0 起，此方法的 const 版本已更改为返回 `const CObject*` 而不是 `const CObject*&`。  进行此更改是为了使编译器符合C++标准。

下表显示了类似于 `CObList::GetNext`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

此程序的结果如下所示：

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList：： GetPrev

获取由*rPosition*标识的列表元素，然后将*rPosition*设置为列表中上一项的位置值。

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>parameters

*rPosition*<br/>
对上一个 `GetPrev` 或其他成员函数调用返回的位置值的引用。

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

如果使用对 `GetTailPosition` 或 `Find`的调用建立初始位置，则可以使用反向迭代循环中的 `GetPrev`。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

如果检索到的元素是列表中的第一个元素，则*rPosition*的新值将设置为 NULL。

> [!NOTE]
>  从 MFC 8.0 起，此方法的 const 版本已更改为返回 `const CObject*` 而不是 `const CObject*&`。  进行此更改是为了使编译器符合C++标准。

下表显示了类似于 `CObList::GetPrev`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

此程序的结果如下所示：

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList：： GetSize

返回列表元素的数目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

列表中的项数。

### <a name="remarks"></a>备注

调用此方法可检索列表中的元素数。

下表显示了类似于 `CObList::GetSize`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList：： GetTail

获取表示此列表尾元素的 `CObject` 指针。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>返回值

请参阅[GetHead](#gethead)的返回值说明。

### <a name="remarks"></a>备注

在调用 `GetTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

下表显示了类似于 `CObList::GetTail`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail （） const;void\*& GetTail （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail （） const;CString & GetTail （）;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList：： GetTailPosition

获取此列表的尾元素的位置;如果列表为空，则**为 NULL** 。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

下表显示了类似于 `CObList::GetTailPosition`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition （） const;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList：： InsertAfter

将元素添加到此列表中位于指定位置的元素之后。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>parameters

*position*<br/>
由上一个 `GetNext`、`GetPrev`或 `Find` 成员函数调用返回的位置值。

*（Newelement*<br/>
要添加到此列表中的对象指针。

下表显示了类似于 `CObList::InsertAfter`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertAfter （位置***位置* **，void** <strong>\*</strong> `newElement` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertAfter （位置***位置* **、const CString &** `newElement` **）;**<br /><br /> **Position InsertAfter （位置***位置* **，LPCTSTR** `newElement` **）;**|

### <a name="return-value"></a>返回值

与*position*参数相同的位置值。

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

此程序的结果如下所示：

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList：： InsertBefore

将元素添加到此列表中指定位置处的元素之前。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>parameters

*position*<br/>
由上一个 `GetNext`、`GetPrev`或 `Find` 成员函数调用返回的位置值。

*（Newelement*<br/>
要添加到此列表中的对象指针。

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

下表显示了类似于 `CObList::InsertBefore`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertBefore （位置***位置* **，void** <strong>\*</strong> `newElement` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertBefore （位置***位置* **、const CString &** `newElement` **）;**<br /><br /> **Position InsertBefore （位置***位置* **，LPCTSTR** `newElement` **）;**|

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

此程序的结果如下所示：

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList：： IsEmpty

指示此列表是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此列表为空，则为非零值;否则为0。

下表显示了类似于 `CObList::IsEmpty`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty （） const;**|

### <a name="example"></a>示例

  请参阅[RemoveAll](#removeall)的示例。

##  <a name="removeall"></a>CObList：： RemoveAll

删除此列表中的所有元素并释放关联的 `CObList` 内存。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

如果该列表已为空，则不会生成任何错误。

从 `CObList`中删除元素时，将从列表中删除对象指针。 你负责删除对象本身。

下表显示了类似于 `CObList::RemoveAll`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList：： RemoveAt

从此列表中移除指定的元素。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>parameters

*position*<br/>
要从列表中移除的元素的位置。

### <a name="remarks"></a>备注

从 `CObList`中删除元素时，将从列表中删除对象指针。 你负责删除对象本身。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

下表显示了类似于 `CObList::RemoveAt`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Void RemoveAt （位置***位置* **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Void RemoveAt （位置***位置* **）;**|

### <a name="example"></a>示例

  在列表迭代期间删除元素时请小心。 下面的示例演示了一种可保证[GetNext](#getnext)的有效**位置**值的删除技术。

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

此程序的结果如下所示：

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList：： RemoveHead

从列表的开头移除元素，并返回指向它的指针。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>返回值

之前位于列表开头的 `CObject` 指针。

### <a name="remarks"></a>备注

在调用 `RemoveHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

下表显示了类似于 `CObList::RemoveHead`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead （）;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList：： RemoveTail

删除列表末尾的元素，并返回指向它的指针。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>返回值

指向位于列表末尾的对象的指针。

### <a name="remarks"></a>备注

在调用 `RemoveTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库断言的调试版本。 使用[IsEmpty](#isempty)验证列表中是否包含元素。

下表显示了类似于 `CObList::RemoveTail`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail （）;**|

### <a name="example"></a>示例

有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList：： SetAt

设置位于给定位置的元素。

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>parameters

pos<br/>
要设置的元素的位置。

*（Newelement*<br/>
要写入到列表中的 `CObject` 指针。

### <a name="remarks"></a>备注

POSITION 类型的变量是列表的键。 它与索引不同，不能自行操作位置值。 `SetAt` 将 `CObject` 指针写入列表中指定的位置。

您必须确保您的位置值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库断言的调试版本。

下表显示了类似于 `CObList::SetAt`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Void SetAt （位置**`pos` **、const CString &** `newElement` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Void SetAt （POSITION** `pos` **，LPCTSTR** `newElement` **）;**|

### <a name="example"></a>示例

  有关 `CAge` 类的列表，请参阅[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

此程序的结果如下所示：

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStringList 类](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList 类](../../mfc/reference/cptrlist-class.md)
