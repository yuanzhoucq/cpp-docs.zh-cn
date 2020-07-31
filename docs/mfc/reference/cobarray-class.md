---
title: CObArray 类
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: b083bf0e82f9d9b928e613f07a71d36147240cd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212366"
---
# <a name="cobarray-class"></a>CObArray 类

支持 `CObject` 指针数组。

## <a name="syntax"></a>语法

```
class CObArray : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CObArray：： CObArray](#cobarray)|为指针构造一个空数组 `CObject` 。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CObArray：： Add](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CObArray：： Append](#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CObArray：： Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CObArray：： .Value.elementat](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CObArray：： FreeExtra](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CObArray：： GetAt](#getat)|返回给定索引位置处的值。|
|[CObArray：： GetCount](#getcount)|获取此数组中的元素数。|
|[CObArray：：](#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CObArray：： GetSize](#getsize)|获取此数组中的元素数。|
|[CObArray：： System.array.getupperbound](#getupperbound)|返回最大的有效索引。|
|[CObArray：： InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CObArray：： IsEmpty](#isempty)|确定数组是否为空。|
|[CObArray：： RemoveAll](#removeall)|从此数组中移除所有元素。|
|[CObArray：： RemoveAt](#removeat)|移除特定索引处的元素。|
|[CObArray：： SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CObArray：： SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CObArray：： SetSize](#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CObArray：： operator \[\]](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

这些对象数组类似于 C 数组，但可以根据需要动态收缩和增长。

数组索引的起始位置始终为0。 您可以决定是在添加超出当前界限的元素时修复上限还是允许数组展开。 即使某些元素为 null，内存也会连续分配到上限。

在 Win32 下，对象的大小 `CObArray` 仅限于可用内存。

与 C 数组一样，索引元素的访问时间 `CObArray` 是常量，与数组大小无关。

`CObArray`合并 IMPLEMENT_SERIAL 宏，以支持其元素的序列化和转储。 如果 `CObject` 使用重载的插入运算符或成员函数将指针的数组存储到存档中， `Serialize` 则每个 `CObject` 元素又会随数组索引一起序列化。

如果需要 `CObject` 在数组中使用单个元素的转储，则必须将对象的深度设置 `CDumpContext` 为1或更大。

`CObArray`删除对象时，或删除其元素时，只 `CObject` 会删除指针，而不会删除它们引用的对象。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

数组类派生类似于列表派生。 有关专用列表类的派生的详细信息，请参阅文章[集合](../../mfc/collections.md)。

> [!NOTE]
> 如果打算序列化数组，则必须在派生类的实现中使用 IMPLEMENT_SERIAL 宏。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray：： Add

将新元素添加到数组的末尾，将数组增大1。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>参数

*（Newelement*<br/>
`CObject`要添加到此数组的指针。

### <a name="return-value"></a>返回值

所添加的元素的索引。

### <a name="remarks"></a>备注

如果[SetSize](#setsize)已用于大于1的*nGrowBy*值，则可能会分配额外的内存。 但是，上限将仅增加1。

下表显示了与类似的其他成员函数 `CObArray::Add` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add （BYTE** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Add （DWORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Add （void** <strong>\*</strong> `newElement`**);**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add （LPCTSTR** `newElement` **）; throw （CMemoryException \* ）;**<br /><br /> **INT_PTR Add （Const CString&** `newElement` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add （UINT** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 添加（WORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>示例

  有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程序的结果如下所示：

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray：： Append

调用此成员函数可将另一个数组的内容添加到给定数组的末尾。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个追加的元素的索引。

### <a name="remarks"></a>备注

数组必须具有相同的类型。

如有必要， `Append` 可能会分配额外内存来容纳追加到数组的元素。

下表显示了与类似的其他成员函数 `CObArray::Append` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 追加（Const CByteArray&** *src* **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 追加（Const CDWordArray&** *src* **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 追加（Const CPtrArray&** *src* **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 追加（Const CStringArray&** *src* **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 追加（Const CUIntArray&** *src* **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 追加（Const CWordArray&** *src* **）;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray：： Copy

调用此成员函数以用同一类型的另一个数组的元素覆盖给定数组的元素。

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

`Copy`不释放内存;但是，如有必要， `Copy` 可能会分配额外内存来容纳复制到数组的元素。

下表显示了与类似的其他成员函数 `CObArray::Copy` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Void 副本（Const CByteArray&** *src* **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Void 副本（Const CDWordArray&** *src* **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Void 副本（Const CPtrArray&** *src* **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Void 副本（Const CStringArray&** *src* **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Void 副本（Const CUIntArray&** *src* **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Void 副本（Const CWordArray&** *src* **）;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray：： CObArray

构造空 `CObject` 的指针数组。

```
CObArray();
```

### <a name="remarks"></a>备注

数组每次增长一个元素。

下表显示了类似于的其他构造函数 `CObArray::CObArray` 。

|类|构造函数|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray：： .Value.elementat

在该数组中返回对元素指针的临时引用。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于返回的值的整数索引 `GetUpperBound` 。

### <a name="return-value"></a>返回值

对指针的引用 `CObject` 。

### <a name="remarks"></a>备注

它用于为数组实现左侧赋值运算符。 请注意，这是一个高级函数，只应用于实现特殊的数组运算符。

下表显示了与类似的其他成员函数 `CObArray::ElementAt` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& .value.elementat （INT_PTR** `nIndex` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& .value.elementat （INT_PTR** `nIndex` **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& .value.elementat （INT_PTR** `nIndex` **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& .value.elementat （INT_PTR** `nIndex` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& .value.elementat （INT_PTR** `nIndex` **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& .value.elementat （INT_PTR** `nIndex` **）;**|

### <a name="example"></a>示例

  请参阅[CObArray：： GetSize](#getsize)的示例。

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray：： FreeExtra

释放阵列增长时分配的任何额外内存。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>备注

此函数不影响数组的大小或上限。

下表显示了与类似的其他成员函数 `CObArray::FreeExtra` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra （）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra （）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra （）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra （）;**|

### <a name="example"></a>示例

  请参阅[CObArray：：](#getdata)的示例。

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray：： GetAt

返回指定索引处的数组元素。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于返回的值的整数索引 `GetUpperBound` 。

### <a name="return-value"></a>返回值

`CObject`当前位于此索引处的指针元素。

### <a name="remarks"></a>备注

> [!NOTE]
> 传递负值或大于返回值的值 `GetUpperBound` 将导致断言失败。

下表显示了与类似的其他成员函数 `CObArray::GetAt` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt （INT_PTR** `nIndex` **） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt （INT_PTR** `nIndex` **） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*GetAt （INT_PTR** `nIndex` **） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt （INT_PTR** `nIndex` **） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt （INT_PTR** `nIndex` **） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt （INT_PTR** `nIndex` **） const;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray：： GetCount

返回数组元素的数目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

数组中的项数。

### <a name="remarks"></a>备注

调用此方法可检索数组中的元素数。 由于索引从零开始，因此大小比最大索引大1。

下表显示了与类似的其他成员函数 `CObArray::GetCount` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray：：

使用此成员函数可获取对数组中的元素的直接访问。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>返回值

指向指针数组的指针 `CObject` 。

### <a name="remarks"></a>备注

如果没有可用的元素，则 `GetData` 返回 null 值。

直接访问数组中的元素有助于更快地工作，在调用时请小心 `GetData` ; 你直接执行的任何错误都将影响数组的元素。

下表显示了与类似的其他成员函数 `CObArray::GetData` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const BYTE 字节 \* （） const;字节的字节 \* （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD 字节 \* （） const; DWORD 字节 \* （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void \* \* （） const; void \* \***|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString \* （） const;CString \***|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT \* （） const;UINT \***|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const 字 \* （） const;字处理 \* （）;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray：： GetSize

返回数组的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>备注

由于索引从零开始，因此大小比最大索引大1。

下表显示了与类似的其他成员函数 `CObArray::GetSize` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray：： System.array.getupperbound

返回此数组的当前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>返回值

上限的索引（从零开始）。

### <a name="remarks"></a>备注

由于数组索引从零开始，因此此函数返回小于的值 1 `GetSize` 。

条件 `GetUpperBound( )` =-1 指示数组不包含任何元素。

下表显示了与类似的其他成员函数 `CObArray::GetUpperBound` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray：： InsertAt

在指定索引处插入一个元素（或另一个数组中的所有元素）。

```cpp
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
可能大于返回的值的整数索引 `GetUpperBound` 。

*（Newelement*<br/>
`CObject`要放置在此数组中的指针。 允许值为 NULL 的 *(newelement* 。

*nCount*<br/>
应插入此元素的次数（默认值为1）。

*nStartIndex*<br/>
可能大于返回的值的整数索引 `GetUpperBound` 。

*pNewArray*<br/>
包含要添加到此数组中的元素的另一个数组。

### <a name="remarks"></a>备注

的第一个版本在 `InsertAt` 数组中的指定索引处插入一个元素（或一个元素的多个副本）。 在此过程中，它将索引中的现有元素上移（增量索引），并将其上方的所有元素上移。

第二个版本从 `CObArray` *nStartIndex*位置开始插入来自其他集合的所有元素。

`SetAt`相反，函数会替换一个指定的数组元素，而不会移动任何元素。

下表显示了与类似的其他成员函数 `CObArray::InsertAt` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，BYTE** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CByteArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，DWORD** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CDWordArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CPtrArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CStringArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，UINT** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CUIntArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，WORD** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CWordArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>示例

  有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程序的结果如下所示：

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray：： IsEmpty

确定数组是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果数组为空，则为非零值;否则为0。

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray：： operator []

这些下标运算符是和函数的便利替代品 `SetAt` `GetAt` 。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>备注

为 not 的数组调用的第一个运算符 **`const`** 可用于赋值语句右侧（r 值）或左侧（左值）。 第二个（为 **`const`** 数组调用）仅可在右侧使用。

如果下标（在赋值语句的左侧或右侧）超出界限，则此库的调试版本将断言。

下表显示了与类似的其他运算符 `CObArray::operator []` 。

|类|操作员|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **BYTE 运算符 [] （int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **DWORD 运算符 [] （int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **void \* 运算符 [] （int_ptr** `nindex` ** \) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **CString 运算符 [] （int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **UINT 运算符 [] （int_ptr** `nindex` ** \) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& 运算符 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **WORD 运算符 [] （int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray：： RemoveAll

删除此数组中的所有指针，但并不实际删除 `CObject` 对象。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果数组已为空，则函数仍可正常工作。

`RemoveAll`函数释放用于指针存储的所有内存。

下表显示了与类似的其他成员函数 `CObArray::RemoveAll` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll （）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll （）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll （）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>示例

有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray：： RemoveAt

从数组中的指定索引处开始移除一个或多个元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于返回的值的整数索引 `GetUpperBound` 。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

在此过程中，它将所有元素向下移动到删除的元素之上。 它将减小数组的上限，但不释放内存。

如果尝试删除的元素多于删除点上方数组中包含的元素，则库断言的调试版本。

`RemoveAt`函数 `CObject` 从数组中删除指针，但不删除对象本身。

下表显示了与类似的其他成员函数 `CObArray::RemoveAt` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** *nCount* **= 1）;**|

### <a name="example"></a>示例

  有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程序的结果如下所示：

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray：： SetAt

设置指定索引处的数组元素。

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于返回的值的整数索引 `GetUpperBound` 。

*（Newelement*<br/>
要插入此数组中的对象指针。 允许空值。

### <a name="remarks"></a>备注

`SetAt`不会导致数组增长。 `SetAtGrow`如果希望数组自动增长，请使用。

必须确保索引值表示数组中的有效位置。 如果该函数超出界限，则为调试版本的库断言。

下表显示了与类似的其他成员函数 `CObArray::SetAt` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt （INT_PTR** `nIndex` **，BYTE** `newElement` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，DWORD** `newElement` **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，UINT** `newElement` **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，WORD** `newElement` **）;**|

### <a name="example"></a>示例

  有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程序的结果如下所示：

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray：： SetAtGrow

设置指定索引处的数组元素。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于0的整数索引。

*（Newelement*<br/>
要添加到此数组的对象指针。 允许空值。

### <a name="remarks"></a>备注

如有必要，数组将自动增长（也就是说，对上限进行调整以容纳新元素）。

下表显示了与类似的其他成员函数 `CObArray::SetAtGrow` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，BYTE** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，DWORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，UINT** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，WORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>示例

  有关所有集合示例中所用类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程序的结果如下所示：

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray：： SetSize

确定空数组或现有数组的大小;如有必要，分配内存。

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>参数

*nNewSize*<br/>
新数组大小（元素数）。 必须高于或等于 0。

*nGrowBy*<br/>
如果需要增加大小，要分配的元素槽的最小数目。

### <a name="remarks"></a>备注

如果新大小小于旧大小，则会截断数组，并释放所有未使用的内存。 为提高效率，请 `SetSize` 在使用数组之前调用来设置数组的大小。 这可以防止每次添加项时都需要重新分配和复制数组。

当数组正在增长时， *nGrowBy*参数会影响内部内存分配。 它的用途绝不会影响和报告的数组 `GetSize` 大小 `GetUpperBound` 。

如果数组的大小增长，则所有新分配的**CObject** <strong>\*</strong> 指针将设置为 NULL。

下表显示了与类似的其他成员函数 `CObArray::SetSize` 。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>示例

  请参阅[CObArray：：](#getdata)的示例。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStringArray 类](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray 类](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray 类](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray 类](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray 类](../../mfc/reference/cdwordarray-class.md)
