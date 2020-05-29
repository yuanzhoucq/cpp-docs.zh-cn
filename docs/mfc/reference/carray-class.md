---
title: CArray 类
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 3355e72c58365e97f8f3f8ce09754285f671915a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753977"
---
# <a name="carray-class"></a>CArray 类

支持类似于 C 数组的数组，但可以根据需要动态减少和增长。

## <a name="syntax"></a>语法

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>参数

*类型*<br/>
指定数组中存储的对象类型的模板参数。 *TYPE*是 返回的`CArray`参数。

*ARG_TYPE*<br/>
指定用于访问数组中存储对象的参数类型的模板参数。 通常引用*TYPE*。 *ARG_TYPE*是传递给`CArray`的参数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CArray：CArray](#carray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CArray：：添加](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CArray：：追加](#append)|将另一个数组追加到数组中;如有必要，增大数组|
|[CArray：：复制](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[Carray：：元素At](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CArray：：免费额外](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[Carray：getat](#getat)|返回给定索引位置处的值。|
|[CArray：获取计数](#getcount)|获取此数组中的元素数。|
|[CArray：获取数据](#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CArray：获取 Size](#getsize)|获取此数组中的元素数。|
|[Carray：获取上部](#getupperbound)|返回最大的有效索引。|
|[Carray：：插入At](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[数组：：为空](#isempty)|确定数组是否为空。|
|[Carray：：删除所有](#removeall)|从此数组中移除所有元素。|
|[数组：：删除 AT](#removeat)|移除特定索引处的元素。|
|[Carray：：Setat](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[Carray：setat增长](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CArray：：设置大小](#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

数组索引始终从位置 0 开始。 您可以决定是否修复上限，还是使数组在添加超过当前绑定的元素时展开。 即使某些元素为空，内存也会连续分配给上限。

> [!NOTE]
> 大多数调整`CArray`对象大小或向其添加元素的方法都使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)来移动元素。 这是一个问题，因为`memcpy_s`与需要调用构造函数的任何对象不兼容。 如果 中的`CArray`项与`memcpy_s`不兼容，则必须创建适当大小的新`CArray`项。 然后，您必须使用[CArray：：copy](#copy)和[CArray：setAt](#setat)来填充新数组，因为这些方法使用赋值运算符`memcpy_s`而不是 。

与 C 数组一样，`CArray`索引元素的访问时间是恒定的，并且与数组大小无关。

> [!TIP]
> 在使用数组之前，请使用[SetSize](#setsize)来建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要数组中单个元素的转储，则必须将[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象的深度设置为 1 或更大。

此类的某些成员函数调用全局帮助器函数，这些函数必须针对`CArray`类的大多数用途进行自定义。 请参阅 MFC 宏和全局部分中的主题[集合类帮助器](../../mfc/reference/collection-class-helpers.md)。

数组类派生类似于列表派生。

有关如何使用的详细信息`CArray`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray：：添加

将新元素添加到数组的末尾，将数组增加 1。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
指定引用此数组中元素的参数类型的模板参数。

*新元素*<br/>
要添加到此数组的元素。

### <a name="return-value"></a>返回值

添加元素的索引。

### <a name="remarks"></a>备注

如果[SetSize](#setsize)已使用`nGrowBy`的值大于 1，则可能会分配额外的内存。 但是，上限仅增加 1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray：：追加

调用此成员函数将一个数组的内容添加到另一个数组的末尾。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个附加元素的索引。

### <a name="remarks"></a>备注

数组必须具有相同的类型。

如有必要，`Append`可以分配额外的内存以容纳追加到数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray：CArray

构造一个空数组。

```
CArray();
```

### <a name="remarks"></a>备注

数组一次增加一个元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray：：复制

使用此成员函数将一个数组的元素复制到另一个数组。

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

调用此成员函数以用另一个数组的元素覆盖一个数组的元素。

`Copy`不释放内存;但是，如有必要，`Copy`可能会分配额外的内存以适应复制到数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>Carray：：元素At

返回对数组中指定元素的临时引用。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于[GetUpperBound](#getupperbound)返回的值的整数索引。

### <a name="return-value"></a>返回值

对数组元素的引用。

### <a name="remarks"></a>备注

它用于实现数组的左侧赋值运算符。

### <a name="example"></a>示例

  请参阅[GetSize 的示例](#getsize)。

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray：：免费额外

释放在阵列增长时分配的任何额外内存。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>备注

此函数对数组的大小或上限没有影响。

### <a name="example"></a>示例

  请参阅[GetData](#getdata)的示例。

## <a name="carraygetat"></a><a name="getat"></a>Carray：getat

在指定的索引处返回数组元素。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定数组元素类型的模板参数。

*nIndex*<br/>
大于或等于 0 且小于或等于[GetUpperBound](#getupperbound)返回的值的整数索引。

### <a name="return-value"></a>返回值

当前位于此索引的数组元素。

### <a name="remarks"></a>备注

传递负值或大于返回`GetUpperBound`的值的值将导致断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray：获取计数

返回数组元素的数量。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

数组中的项数。

### <a name="remarks"></a>备注

调用此方法以检索数组中的元素数。 由于索引是零基的，因此大小大于最大索引的 1。 调用此方法将生成与[CArray：：getSize](#getsize)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray：获取数据

使用此成员函数可以直接访问数组中的元素。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>参数

*类型*<br/>
指定数组元素类型的模板参数。

### <a name="return-value"></a>返回值

指向数组元素的指针。

### <a name="remarks"></a>备注

如果没有可用的元素，`GetData`则返回 null 值。

虽然直接访问数组的元素可以帮助您更快地工作，但调用`GetData`时请谨慎操作 。您犯的任何错误都会直接影响数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray：获取 Size

返回数组的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>备注

由于索引是零基的，因此大小大于最大索引的 1。 调用此方法将生成与[CArray：：getCount](#getcount)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>Carray：获取上部

返回此数组的当前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>备注

由于数组索引是零基的，因此此函数返回的值 1 小于`GetSize`。

条件`GetUpperBound( )`= -1 表示数组不包含任何元素。

### <a name="example"></a>示例

  请参阅[CArray：：getAt](#getat)的示例。

## <a name="carrayinsertat"></a><a name="insertat"></a>Carray：：插入At

第一个版本在`InsertAt`数组中的指定索引中插入一个元素（或元素的多个副本）。

```cpp
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
可能大于 返回`GetUpperBound`的值的整数索引。

*ARG_TYPE*<br/>
指定此数组中元素类型的模板参数。

*新元素*<br/>
要放置在此数组中的元素。

*nCount*<br/>
应插入此元素的次数（默认值为 1）。

*nStartIndex*<br/>
可能大于[GetUpperBound](#getupperbound)返回的值的整数索引。

*pNewArray*<br/>
另一个包含要添加到此数组的元素的数组。

### <a name="remarks"></a>备注

在此过程中，它向上移动（通过增加索引）此索引中的现有元素，并向上移动其上方的所有元素。

第二个版本从*nStartIndex*位置`CArray`开始插入另一个集合中的所有元素。

相反`SetAt`，函数替换一个指定的数组元素，并且不移动任何元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>数组：：为空

确定数组是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果数组不包含任何元素，则非零;否则 0。

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray：：运算符\[\]

这些下标运算符是[SetAt](#setat)和[GetAt](#getat)函数的便捷替代。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此数组中元素类型的模板参数。

*nIndex*<br/>
要访问的元素的索引。

### <a name="remarks"></a>备注

第一个运算符（称为非**const**数组）可以在赋值语句的右侧（r 值）或左侧（l 值）上使用。 第二个，称为**const**数组，只能在右侧使用。

库的调试版本断言下标（在赋值语句的左侧或右侧）是否超出边界。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray：：重新定位元素

当数组应增长或收缩时，将数据重新定位到新缓冲区。

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>参数

*pNewData*<br/>
元素数组的新缓冲区。

*pData*<br/>
元素的旧数组。

*nCount*<br/>
旧数组中的元素数。

### <a name="remarks"></a>备注

*pNewData*始终足够大，可以容纳所有*pData*元素。

当数组应增长或收缩时（当调用[SetSize](#setsize)或[FreeExtra](#freeextra)时[），CArray](../../mfc/reference/carray-class.md)实现使用此方法将旧数据复制到新缓冲区。 默认实现仅复制数据。

对于元素包含指向其自己的成员之一的指针或其他结构包含指向其中一个数组元素的指针的数组，指针不会以纯副本更新。 在这种情况下，您可以通过使用相关类型的实现专业化`RelocateElements`来更正指针。 您还负责数据复制。

## <a name="carrayremoveall"></a><a name="removeall"></a>Carray：：删除所有

从此数组中移除所有元素。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果数组已为空，则函数仍然有效。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>数组：：删除 AT

删除从数组中指定索引开始的一个或多个元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于[GetUpperBound](#getupperbound)返回的值的整数索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

在此过程中，它会向下移动删除的元素上方的所有元素。 它会递减数组的上限，但不释放内存。

如果尝试删除的元素多于删除点上方的数组中包含的元素，则库的调试版本断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>Carray：：Setat

在指定的索引处设置数组元素。

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于[GetUpperBound](#getupperbound)返回的值的整数索引。

*ARG_TYPE*<br/>
模板参数，指定用于引用数组元素的参数类型。

*新元素*<br/>
要存储在指定位置的新元素值。

### <a name="remarks"></a>备注

`SetAt`不会导致数组增长。 如果您希望阵列自动增长，请使用[SetAtGrow。](#setatgrow)

必须确保索引值表示数组中的有效位置。 如果它超出边界，则库的调试版本断言。

### <a name="example"></a>示例

  请参阅[GetAt](#getat)的示例。

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>Carray：setat增长

在指定的索引处设置数组元素。

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 的整数索引。

*ARG_TYPE*<br/>
指定数组中元素类型的模板参数。

*新元素*<br/>
要添加到此数组的元素。 允许 NULL 值。

### <a name="remarks"></a>备注

如有必要，数组会自动增长（即，调整上限以适应新元素）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray：：设置大小

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

如果新大小小于旧大小，则数组将被截断，并释放所有未使用的内存。

在开始使用数组之前，使用此函数设置数组的大小。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

*nGrowBy*参数在阵列增长时影响内部内存分配。 其使用永远不会影响[GetSize](#getsize)和[GetUpperBound](#getupperbound)报告的数组大小。 如果使用默认值，MFC 会以计算的方式分配内存，以避免内存碎片，并优化大多数情况下的效率。

### <a name="example"></a>示例

  请参阅[GetData](#getdata)的示例。

## <a name="see-also"></a>请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)<br/>
[集合类帮助器](../../mfc/reference/collection-class-helpers.md)
