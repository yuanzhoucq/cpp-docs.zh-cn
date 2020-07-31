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
ms.openlocfilehash: f73666f3a20488d14a82b7c56d682f3f5b2386df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195169"
---
# <a name="carray-class"></a>CArray 类

支持类似于 C 数组的数组，但可以根据需要动态减小和增长。

## <a name="syntax"></a>语法

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>参数

*TYPE*<br/>
指定存储在数组中的对象类型的模板参数。 *类型*是返回的参数 `CArray` 。

*ARG_TYPE*<br/>
指定用于访问存储在数组中的对象的参数类型的模板参数。 通常是对*类型*的引用。 *ARG_TYPE*是传递给的参数 `CArray` 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CArray：： CArray](#carray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CArray：： Add](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CArray：： Append](#append)|将另一个数组追加到数组;必要时增大数组|
|[CArray：： Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CArray：： .Value.elementat](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CArray：： FreeExtra](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CArray：： GetAt](#getat)|返回给定索引位置处的值。|
|[CArray：： GetCount](#getcount)|获取此数组中的元素数。|
|[CArray：：](#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CArray：： GetSize](#getsize)|获取此数组中的元素数。|
|[CArray：： System.array.getupperbound](#getupperbound)|返回最大的有效索引。|
|[CArray：： InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CArray：： IsEmpty](#isempty)|确定数组是否为空。|
|[CArray：： RemoveAll](#removeall)|从此数组中移除所有元素。|
|[CArray：： RemoveAt](#removeat)|移除特定索引处的元素。|
|[CArray：： SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CArray：： SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CArray：： SetSize](#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

数组索引的起始位置始终为0。 你可以决定是要修复上限还是允许在添加超出当前绑定的元素时扩展数组。 即使某些元素为 null，内存也会连续分配到上限。

> [!NOTE]
> 大多数调整 `CArray` 对象大小或向其添加元素的方法使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)移动元素。 这是一个问题，因为与 `memcpy_s` 需要调用构造函数的任何对象都不兼容。 如果中的项 `CArray` 与不兼容 `memcpy_s` ，则必须创建适当大小的新 `CArray` 。 然后，必须使用[CArray：： Copy](#copy)和[CArray：： SetAt](#setat)填充新数组，因为这些方法使用赋值运算符而不是 `memcpy_s` 。

与 C 数组一样，索引元素的访问时间 `CArray` 是常量，与数组大小无关。

> [!TIP]
> 使用数组之前，请使用[SetSize](#setsize)建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要对数组中的单个元素进行转储，则必须将[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象的深度设置为1或更大。

此类的某些成员函数调用全局 helper 函数，这些函数必须针对该类的大多数用途进行自定义 `CArray` 。 请参阅 MFC Macros and Globals 部分的主题[集合类帮助](../../mfc/reference/collection-class-helpers.md)器。

数组类派生类似于列表派生。

有关如何使用的详细信息 `CArray` ，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray：： Add

将新元素添加到数组的末尾，将数组增大1。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*ARG_TYPE*<br/>
指定引用此数组中的元素的参数类型的模板参数。

*（Newelement*<br/>
要添加到此数组的元素。

### <a name="return-value"></a>返回值

所添加的元素的索引。

### <a name="remarks"></a>备注

如果[SetSize](#setsize)已用于 `nGrowBy` 大于1的值，则可能会分配额外的内存。 但是，上限将仅增加1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray：： Append

调用此成员函数可将一个数组的内容添加到另一个数组的末尾。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个追加的元素的索引。

### <a name="remarks"></a>备注

数组必须具有相同的类型。

如有必要， `Append` 可能会分配额外内存来容纳追加到数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray：： CArray

构造一个空数组。

```
CArray();
```

### <a name="remarks"></a>备注

数组每次增长一个元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray：： Copy

使用此成员函数将一个数组的元素复制到另一个数组。

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

调用此成员函数以覆盖一个数组中具有另一个数组元素的元素。

`Copy`不释放内存;但是，如有必要， `Copy` 可能会分配额外内存来容纳复制到数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray：： .Value.elementat

返回对数组中指定元素的临时引用。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于[system.array.getupperbound](#getupperbound)返回的值的整数索引。

### <a name="return-value"></a>返回值

对数组元素的引用。

### <a name="remarks"></a>备注

它用于为数组实现左侧赋值运算符。

### <a name="example"></a>示例

  请参阅[GetSize](#getsize)的示例。

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray：： FreeExtra

释放阵列增长时分配的任何额外内存。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>备注

此函数不影响数组的大小或上限。

### <a name="example"></a>示例

  请参阅["有"](#getdata)的示例。

## <a name="carraygetat"></a><a name="getat"></a>CArray：： GetAt

返回指定索引处的数组元素。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定数组元素类型的模板参数。

*nIndex*<br/>
一个大于或等于0且小于或等于[system.array.getupperbound](#getupperbound)返回的值的整数索引。

### <a name="return-value"></a>返回值

当前位于此索引处的数组元素。

### <a name="remarks"></a>备注

传递负值或大于返回值的值 `GetUpperBound` 将导致断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray：： GetCount

返回数组元素的数目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

数组中的项数。

### <a name="remarks"></a>备注

调用此方法可检索数组中的元素数。 由于索引从零开始，因此大小比最大索引大1。 调用此方法将生成与[CArray：： GetSize](#getsize)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray：：

使用此成员函数可获取对数组中的元素的直接访问。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定数组元素类型的模板参数。

### <a name="return-value"></a>返回值

指向数组元素的指针。

### <a name="remarks"></a>备注

如果没有可用的元素，则 `GetData` 返回 null 值。

直接访问数组中的元素有助于更快地工作，在调用时请小心 `GetData` ; 你直接执行的任何错误都将影响数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray：： GetSize

返回数组的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>备注

由于索引从零开始，因此大小比最大索引大1。 调用此方法将生成与[CArray：： GetCount](#getcount)方法相同的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray：： System.array.getupperbound

返回此数组的当前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>备注

由于数组索引从零开始，因此此函数返回小于的值 1 `GetSize` 。

条件 `GetUpperBound( )` =-1 指示数组不包含任何元素。

### <a name="example"></a>示例

  请参阅[CArray：： GetAt](#getat)的示例。

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray：： InsertAt

的第一个版本在 `InsertAt` 数组中的指定索引处插入一个元素（或一个元素的多个副本）。

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
可能大于返回的值的整数索引 `GetUpperBound` 。

*ARG_TYPE*<br/>
用于指定此数组中的元素类型的模板参数。

*（Newelement*<br/>
要放置在此数组中的元素。

*nCount*<br/>
应插入此元素的次数（默认值为1）。

*nStartIndex*<br/>
可能大于[system.array.getupperbound](#getupperbound)返回的值的整数索引。

*pNewArray*<br/>
包含要添加到此数组中的元素的另一个数组。

### <a name="remarks"></a>备注

在此过程中，它将索引中的现有元素上移（增量索引），并将其上方的所有元素上移。

第二个版本从 `CArray` *nStartIndex*位置开始插入来自其他集合的所有元素。

`SetAt`相反，函数会替换一个指定的数组元素，而不会移动任何元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray：： IsEmpty

确定数组是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果数组不包含任何元素，则为非零值;否则为0。

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray：： operator\[\]

这些下标运算符是[SetAt](#setat)和[GetAt](#getat)函数的便利替代品。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
用于指定此数组中的元素类型的模板参数。

*nIndex*<br/>
要访问的元素的索引。

### <a name="remarks"></a>备注

为 not 的数组调用的第一个运算符 **`const`** 可用于赋值语句右侧（r 值）或左侧（左值）。 第二个（为 **`const`** 数组调用）仅可在右侧使用。

如果下标（在赋值语句的左侧或右侧）超出界限，则此库的调试版本将断言。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray：： RelocateElements

当数组应增大或缩小时，将数据重定位到新的缓冲区。

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
旧的元素数组。

*nCount*<br/>
旧数组中的元素数。

### <a name="remarks"></a>备注

*pNewData*始终足够大以容纳所有*pData*元素。

当数组应增大或收缩时（调用[SetSize](#setsize)或[FreeExtra](#freeextra)时）， [CArray](../../mfc/reference/carray-class.md)实现使用此方法将旧数据复制到新缓冲区。 默认实现仅复制数据。

对于元素包含一个指向其自己的成员的指针的数组，或另一个结构包含指向其中一个数组元素的指针，则不会以纯文本格式更新指针。 在这种情况下，可以通过实现具有相关类型的专用化来更正指针 `RelocateElements` 。 你还负责数据复制。

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray：： RemoveAll

从此数组中移除所有元素。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

如果数组已为空，则函数仍可正常工作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray：： RemoveAt

从数组中的指定索引处开始移除一个或多个元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于[system.array.getupperbound](#getupperbound)返回的值的整数索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

在此过程中，它将所有元素向下移动到删除的元素之上。 它将减小数组的上限，但不释放内存。

如果尝试删除的元素多于删除点上方数组中包含的元素，则库断言的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray：： SetAt

设置指定索引处的数组元素。

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于[system.array.getupperbound](#getupperbound)返回的值的整数索引。

*ARG_TYPE*<br/>
指定用于引用数组元素的参数类型的模板参数。

*（Newelement*<br/>
要存储在指定位置的新元素值。

### <a name="remarks"></a>备注

`SetAt`不会导致数组增长。 如果希望数组自动增长，请使用[SetAtGrow](#setatgrow) 。

必须确保索引值表示数组中的有效位置。 如果该函数超出界限，则为调试版本的库断言。

### <a name="example"></a>示例

  请参阅[GetAt](#getat)的示例。

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray：： SetAtGrow

设置指定索引处的数组元素。

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于0的整数索引。

*ARG_TYPE*<br/>
指定数组中的元素类型的模板参数。

*（Newelement*<br/>
要添加到此数组的元素。 允许空值。

### <a name="remarks"></a>备注

如有必要，数组将自动增长（也就是说，对上限进行调整以容纳新元素）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray：： SetSize

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

如果新大小小于旧大小，则会截断数组，并释放所有未使用的内存。

使用此函数可以在开始使用数组之前设置数组的大小。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

当数组正在增长时， *nGrowBy*参数会影响内部内存分配。 它的用途绝不会影响[GetSize](#getsize)和[system.array.getupperbound](#getupperbound)报告的数组大小。 如果使用默认值，则 MFC 将按计算的方式分配内存，以避免在大多数情况下出现内存碎片并优化效率。

### <a name="example"></a>示例

  请参阅["有"](#getdata)的示例。

## <a name="see-also"></a>另请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)<br/>
[集合类帮助器](../../mfc/reference/collection-class-helpers.md)
