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
ms.openlocfilehash: c19715f62704bfc97059421451929cbbec2506ce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754469"
---
# <a name="cobarray-class"></a>CObArray 类

支持 `CObject` 指针数组。

## <a name="syntax"></a>语法

```
class CObArray : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CObarray：CObarray](#cobarray)|为`CObject`指针构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CObarray：添加](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CObarray：：附加](#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CObarray：复制](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CObarray：：元素At](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CObarray：：免费额外](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CObarray：：获取At](#getat)|返回给定索引位置处的值。|
|[CObarray：获取计数](#getcount)|获取此数组中的元素数。|
|[CObarray：获取数据](#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CObarray：获取 Size](#getsize)|获取此数组中的元素数。|
|[CObarray：：获取上部](#getupperbound)|返回最大的有效索引。|
|[CObarray：：插入At](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CObarray：：是空的](#isempty)|确定数组是否为空。|
|[CObarray：：删除所有](#removeall)|从此数组中移除所有元素。|
|[CObarray：：删除At](#removeat)|移除特定索引处的元素。|
|[CObarray：：Setat](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CObarray：：Setat增长](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CObarray：：设置大小](#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CObArray：：运算符\[\]](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

这些对象数组类似于 C 数组，但它们可以根据需要动态收缩和增长。

数组索引始终从位置 0 开始。 您可以决定是否修复上限，或者允许在将元素添加到当前绑定后展开数组。 即使某些元素为空，内存也会连续分配给上限。

在 Win32 下，`CObArray`对象的大小仅限于可用内存。

与 C 数组一样，`CObArray`索引元素的访问时间是恒定的，并且与数组大小无关。

`CObArray`合并IMPLEMENT_SERIAL宏以支持其元素的序列化和转储。 如果将`CObject`指针数组存储在存档中（使用重载插入运算符或`Serialize`成员函数，则每个`CObject`元素依次与其数组索引一起序列化。

如果需要数组中单个`CObject`元素的转储，则必须将`CDumpContext`对象的深度设置为 1 或更大。

删除`CObArray`对象或删除其元素时，将仅删除`CObject`指针，而不是删除它们引用的对象。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

数组类派生类似于列表派生。 有关特殊用途列表类的派生的详细信息，请参阅文章[集合](../../mfc/collections.md)。

> [!NOTE]
> 如果要序列化数组，则必须在派生类的实现中使用IMPLEMENT_SERIAL宏。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObarray：添加

将新元素添加到数组的末尾，将数组增加 1。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>参数

*新元素*<br/>
要`CObject`添加到此数组的指针。

### <a name="return-value"></a>返回值

添加元素的索引。

### <a name="remarks"></a>备注

如果[SetSize](#setsize)已使用*nGrowBy*值大于 1，则可能会分配额外的内存。 但是，上限仅增加 1。

下表显示了与`CObArray::Add`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR添加（字节**`newElement`**）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR添加（DWORD）;** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR添加（无效**<strong>\*</strong>`newElement`**）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR加（LPCTSTR）;** `newElement` **投掷 （\* CMemoryexception ）**<br /><br /> **INT_PTR添加（cString&）;** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR加（UINT）;** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR添加（WORD）;** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|

### <a name="example"></a>示例

  有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程序的结果如下：

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObarray：：附加

调用此成员函数将另一个数组的内容添加到给定数组的末尾。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个附加元素的索引。

### <a name="remarks"></a>备注

数组必须具有相同的类型。

如有必要，`Append`可以分配额外的内存以容纳追加到数组的元素。

下表显示了与`CObArray::Append`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR附录（cByteArray** *&src）;* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR追加（cdWordArray&** *src* **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR附录（cPtrArray&** *src）;* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR附录（cStringarray&** *src* **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR附录（cuIntarray** *&src）;* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR附录（cWordArray&src）;** *src* **);**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObarray：复制

调用此成员函数，用相同类型的另一个数组的元素覆盖给定数组的元素。

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

`Copy`不释放内存;但是，如有必要，`Copy`可能会分配额外的内存以适应复制到数组的元素。

下表显示了与`CObArray::Copy`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**无效复制（cByteArray&** *src）;* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**无效复制（cst CDWordArray&** *src）;* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效复制（const CPtrarray&** *src* **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**无效复制（cStringarray&** *src）;* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**无效复制（const CUIntarray&** *src* **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**无效拷贝（cWordArray&** *src）;* **);**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObarray：CObarray

构造空`CObject`指针数组。

```
CObArray();
```

### <a name="remarks"></a>备注

数组一次增加一个元素。

下表显示了与`CObArray::CObArray`的其他构造函数类似的 。

|类|构造函数|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray（**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray（**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray（**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**弦乐（）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntarray（**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray（**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObarray：：元素At

在该数组中返回对元素指针的临时引用。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于 返回`GetUpperBound`的值的整数索引。

### <a name="return-value"></a>返回值

对指针的`CObject`引用。

### <a name="remarks"></a>备注

它用于实现数组的左侧赋值运算符。 请注意，这是一个高级函数，应仅用于实现特殊数组运算符。

下表显示了与`CObArray::ElementAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE&元素（INT_PTR** `nIndex` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD&元素（INT_PTR）;** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效\*&元素（INT_PTR）;** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**弦&元素（INT_PTR）;** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT&元素（INT_PTR）;** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD&元素（INT_PTR）;** `nIndex` **);**|

### <a name="example"></a>示例

  请参阅[CObarray 示例：：获取 Size](#getsize)。

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObarray：：免费额外

释放在阵列增长时分配的任何额外内存。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>备注

此函数对数组的大小或上限没有影响。

下表显示了与`CObArray::FreeExtra`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**无效免费额外（）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**无效免费额外（）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效免费额外（）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**无效免费额外（）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**无效免费额外（）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**无效免费额外（）;**|

### <a name="example"></a>示例

  请参阅[CObarray 示例：：获取数据](#getdata)。

## <a name="cobarraygetat"></a><a name="getat"></a>CObarray：：获取At

在指定的索引处返回数组元素。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于 返回`GetUpperBound`的值的整数索引。

### <a name="return-value"></a>返回值

当前`CObject`位于此索引的指针元素。

### <a name="remarks"></a>备注

> [!NOTE]
> 传递负值或大于返回`GetUpperBound`的值的值将导致断言失败。

下表显示了与`CObArray::GetAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE 获取（ INT_PTR** `nIndex` **） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD 获取（ INT_PTR** `nIndex` **） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效\*获取（ INT_PTR** `nIndex` **） 同一点;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString Getat（ INT_PTR** `nIndex` **） 同一点;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT Getat（ INT_PTR** `nIndex` **） 康斯特;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD 获取（ INT_PTR** `nIndex` **） 康斯特;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObarray：获取计数

返回数组元素的数量。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

数组中的项数。

### <a name="remarks"></a>备注

调用此方法以检索数组中的元素数。 由于索引是零基的，因此大小大于最大索引的 1。

下表显示了与`CObArray::GetCount`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR获取计数（ ） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR获取计数（ ） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR获取计数（ ） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR获取计数（ ） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR获取计数（ ） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR获取计数（ ） const;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObarray：获取数据

使用此成员函数可以直接访问数组中的元素。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>返回值

指向指针数组的`CObject`指针。

### <a name="remarks"></a>备注

如果没有可用的元素，`GetData`则返回 null 值。

虽然直接访问数组的元素可以帮助您更快地工作，但调用`GetData`时请谨慎操作 。您犯的任何错误都会直接影响数组的元素。

下表显示了与`CObArray::GetData`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**康斯特 BYTE\*获取数据 （ ） const;字节\*获取数据（）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**康斯特DWORD\*获取数据（ ） const;DWORD\*获取数据（**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空白\*\*获取数据（ ） const;\*\*空获取数据 （ ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\*获取数据 （ ） const;CString\*获取数据（）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**康斯特 UINT\*获取数据 （ ） const;UINT\*获取数据（）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**康斯特WORD\*获取数据（ ）WORD\*获取数据（**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObarray：获取 Size

返回数组的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>备注

由于索引是零基的，因此大小大于最大索引的 1。

下表显示了与`CObArray::GetSize`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR获取大小（ ） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR获取大小（ ） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR获取大小（ ） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR获取大小（ ） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR获取大小（ ） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR获取大小（ ） const;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObarray：：获取上部

返回此数组的当前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>返回值

上限的索引（从零开始）。

### <a name="remarks"></a>备注

由于数组索引是零基的，因此此函数返回的值 1 小于`GetSize`。

条件`GetUpperBound( )`= -1 表示数组不包含任何元素。

下表显示了与`CObArray::GetUpperBound`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObarray：：插入At

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
可能大于 返回`GetUpperBound`的值的整数索引。

*新元素*<br/>
要`CObject`放置在此数组中的指针。 允许*新的*值 NULL 元素。

*nCount*<br/>
应插入此元素的次数（默认值为 1）。

*nStartIndex*<br/>
可能大于 返回`GetUpperBound`的值的整数索引。

*pNewArray*<br/>
另一个包含要添加到此数组的元素的数组。

### <a name="remarks"></a>备注

第一个版本在`InsertAt`数组中的指定索引中插入一个元素（或元素的多个副本）。 在此过程中，它向上移动（通过增加索引）此索引中的现有元素，并向上移动其上方的所有元素。

第二个版本从*nStartIndex*位置`CObArray`开始插入另一个集合中的所有元素。

相反`SetAt`，函数替换一个指定的数组元素，并且不移动任何元素。

下表显示了与`CObArray::InsertAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空插入At（INT_PTR，**`nIndex`**字节**`newElement`**，int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**空插入**`nStartIndex`**（INT_PTR，CBytearray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空插入At（INT_PTR，DWORD，int** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**空插入**`nStartIndex`**（INT_PTR，CDWordarray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空插入At（INT_PTR，**`nIndex`**空**<strong>\*</strong>`newElement`**，int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**空插入**`nStartIndex`**（INT_PTR，CPtrarray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**零空插入At（INT_PTR，LPCTSTR，int** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**空插入**`nStartIndex`**（INT_PTR，CStringarray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空插入At（INT_PTR，UINT，int** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**空插入**`nStartIndex`**（INT_PTR，CUIntarray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空插入At（INT_PTR，WORD，int** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1）;**<br /><br /> **投掷（C记忆例外\*）;**<br /><br /> <strong>\*</strong>`pNewArray`**虚插入**`nStartIndex`**（INT_PTR，CWordarray）;** **);**<br /><br /> **投掷（C记忆例外\*）;**|

### <a name="example"></a>示例

  有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程序的结果如下：

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObarray：：是空的

确定数组是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果数组为空，则非零;否则 0。

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray：：运算符 |

这些下标运算符是 和`SetAt``GetAt`函数的方便替代。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>备注

第一个运算符（称为非**const**数组）可以在赋值语句的右侧（r 值）或左侧（l 值）上使用。 第二个，称为**const**数组，只能在右侧使用。

库的调试版本断言下标（在赋值语句的左侧或右侧）是否超出边界。

下表显示了与`CObArray::operator []`的其他运算符类似的 。

|类|操作员|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **BYTE 运算符 [（int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **DWORD 运算符 [（int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效\*&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **无效\*运算符 [（int_ptr**`nindex`**\)同;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **CString 运算符 [（int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **UINT 运算符 [（int_ptr**`nindex`**\)同;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD&运算符 [（int_ptr** `nindex` ** \);**<br /><br /> **WORD 运算符 [（int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObarray：：删除所有

从该数组中删除所有指针，但实际上不会删除对象`CObject`。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果数组已为空，则函数仍然有效。

该`RemoveAll`函数释放用于指针存储的所有内存。

下表显示了与`CObArray::RemoveAll`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**无效删除所有（ ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**无效删除所有（ ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**无效删除所有（ ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**无效删除所有（ ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**无效删除所有（ ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**无效删除所有（ ）;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObarray：：删除At

删除从数组中指定索引开始的一个或多个元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于 返回`GetUpperBound`的值的整数索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

在此过程中，它会向下移动删除的元素上方的所有元素。 它会递减数组的上限，但不释放内存。

如果尝试删除的元素多于删除点上方的数组中包含的元素，则库的调试版本断言。

函数`RemoveAt`从数组中删除`CObject`指针，但不会删除对象本身。

下表显示了与`CObArray::RemoveAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空移（INT_PTR，INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空移（INT_PTR，INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空移（INT_PTR，INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空移（INT_PTR，INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空移（INT_PTR，INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空删除At（INT_PTR，INT_PTRnCount** `nIndex` **, INT_PTR** *nCount* **= 1）;**|

### <a name="example"></a>示例

  有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程序的结果如下：

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObarray：：Setat

在指定的索引处设置数组元素。

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于 返回`GetUpperBound`的值的整数索引。

*新元素*<br/>
要在此数组中插入的对象指针。 允许 NULL 值。

### <a name="remarks"></a>备注

`SetAt`不会导致数组增长。 如果`SetAtGrow`希望数组自动增长，请使用。

必须确保索引值表示数组中的有效位置。 如果它超出边界，则库的调试版本断言。

下表显示了与`CObArray::SetAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空盘（INT_PTR，** `nIndex` **BYTE** `newElement` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空设置（INT_PTR，** `nIndex` **DWORD** `newElement` **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空设置（INT_PTR，** `nIndex`**无效**<strong>\*</strong>`newElement`**）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空设置（INT_PTR，** `nIndex` **LPCTSTR** `newElement` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空集（INT_PTR，** `nIndex` **UINT** `newElement` **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空集（INT_PTR，WORD）;** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>示例

  有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程序的结果如下：

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObarray：：Setat增长

在指定的索引处设置数组元素。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 的整数索引。

*新元素*<br/>
要添加到此数组的对象指针。 允许 NULL 值。

### <a name="remarks"></a>备注

如有必要，数组会自动增长（即，调整上限以适应新元素）。

下表显示了与`CObArray::SetAtGrow`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空塞特增长（INT_PTR，**`nIndex`**字节**`newElement`**）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空集（INT_PTR，** `nIndex` **DWORD** `newElement` **）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空（INT_PTR，** `nIndex`**空**<strong>\*</strong>`newElement`**）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空套（INT_PTR，LPCTSTR）;** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空塞特增长（INT_PTR，UINT）;** `nIndex` **, UINT** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空集（INT_PTR，WORD）;** `nIndex` **, WORD** `newElement` **);**<br /><br /> **投掷（C记忆例外\*）;**|

### <a name="example"></a>示例

  有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程序的结果如下：

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObarray：：设置大小

建立空数组或现有数组的大小;如有必要，分配内存。

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>参数

*n 新尺寸*<br/>
新的数组大小（元素数）。 必须大于或等于 0。

*nGrowBy*<br/>
如果需要增加大小，要分配的最小元素槽数。

### <a name="remarks"></a>备注

如果新大小小于旧大小，则数组将被截断，并释放所有未使用的内存。 为提高效率，请`SetSize`调用在使用数组之前设置数组的大小。 这样可以防止每次添加项时都需要重新分配和复制数组。

*nGrowBy*参数在阵列增长时影响内部内存分配。 其使用永远不会影响 和`GetSize``GetUpperBound`报告的数组大小。

如果数组的大小已增长，则所有新分配的**CObject**<strong>\*</strong>指针都设置为 NULL。

下表显示了与`CObArray::SetSize`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空设置大小（INT_PTR，int** `nNewSize` **, int** `nGrowBy` **= -1）;**<br /><br /> **投掷（C记忆例外\*）;**|

### <a name="example"></a>示例

  请参阅[CObarray 示例：：获取数据](#getdata)。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CStringarray 类](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray 类](../../mfc/reference/cptrarray-class.md)<br/>
[C字节类](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray 类](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray 类](../../mfc/reference/cdwordarray-class.md)
