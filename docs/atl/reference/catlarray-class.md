---
title: CAtlArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c16337949340b03bbaa517ca98ac9b65a5bb2bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053925"
---
# <a name="catlarray-class"></a>CAtlArray 类

此类实现一个数组对象。

## <a name="syntax"></a>语法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>参数

*E*<br/>
要存储在数组中的数据类型。

*ETraits*<br/>
用于复制或移动元素的代码。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[添加](#add)|调用此方法以将元素添加到数组对象。|
|[追加](#append)|调用此方法以将一个数组的内容添加到另一个末尾。|
|[AssertValid](#assertvalid)|调用此方法用于确认数组对象有效。|
|[CAtlArray](#catlarray)|构造函数。|
|[~ CAtlArray](#dtor)|析构函数。|
|[复制](#copy)|调用此方法将一个数组的元素复制到另一个。|
|[FreeExtra](#freeextra)|调用此方法以从数组中移除任何空元素。|
|[GetAt](#getat)|调用此方法从数组对象中检索单个元素。|
|[GetCount](#getcount)|调用此方法以返回数组中存储的元素数量。|
|[GetData](#getdata)|调用此方法以返回指向数组中的第一个元素的指针。|
|[InsertArrayAt](#insertarrayat)|调用此方法要插入到另一个数组。|
|[InsertAt](#insertat)|数组对象调用此方法以插入新元素 （或一个元素的多个副本）。|
|[IsEmpty](#isempty)|调用此方法来测试如果数组为空。|
|[RemoveAll](#removeall)|调用此方法以从数组对象中移除所有元素。|
|[RemoveAt](#removeat)|调用此方法以从数组中移除一个或多个元素。|
|[SetAt](#setat)|调用此方法以设置元素值的数组对象中。|
|[SetAtGrow](#setatgrow)|调用此方法以扩展所需的数组的数组对象中设置元素的值。|
|[SetCount](#setcount)|调用此方法以设置数组对象的大小。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符&#91;&#93;](#operator_at)|调用此运算符可返回数组中的元素的引用。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[INARGTYPE](#inargtype)|要用于将元素添加到数组的数据类型。|
|[OUTARGTYPE](#outargtype)|要用于检索数组中元素的数据类型。|

## <a name="remarks"></a>备注

`CAtlArray` 提供用于创建和管理的用户定义类型的元素数组的方法。 尽管类似于标准 C 数组、`CAtlArray`对象可以动态缩小和增大。 数组索引总是开始于位置 0，并且可以固定的或允许为新元素添加上限。

对于较少的元素，ATL 类数组[CSimpleArray](../../atl/reference/csimplearray-class.md)可用。

`CAtlArray` 与 MFC 的密切相关`CArray`类，并会在 MFC 项目中，尽管没有序列化支持。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

调用此方法以将元素添加到数组对象。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>参数

*元素*<br/>
要添加到数组的元素。

### <a name="return-value"></a>返回值

返回添加的元素的索引。

### <a name="remarks"></a>备注

新元素添加到数组末尾。 如果元素不提供添加空元素;即，数组是其大小增大的像真正的元素被添加。 如果操作失败， [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)用参数 E_OUTOFMEMORY 调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

调用此方法以将一个数组的内容添加到另一个末尾。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>参数

*aSrc*<br/>
要追加的数组。

### <a name="return-value"></a>返回值

返回第一个追加的元素的索引。

### <a name="remarks"></a>备注

中提供的数组的元素添加到现有数组的末尾。 如有必要，将分配内存来容纳新元素。

数组必须是同一类型的并且不能将一个数组追加到其自身。

在调试版本中 ATLASSERT 情况下会引发`CAtlArray`参数不是有效的数组或如果*aSrc*引用同一对象。 在发布版本中可能导致不可预知的行为的参数无效。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

调用此方法用于确认数组对象有效。

```
void AssertValid() const;
```

### <a name="remarks"></a>备注

如果数组对象不是有效的 ATLASSERT 将引发断言。 此方法是定义 _DEBUG 时才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

构造函数。

```
CAtlArray() throw();
```

### <a name="remarks"></a>备注

初始化数组对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  CAtlArray:: ~ CAtlArray

析构函数。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>备注

使用数组对象的任何资源将释放。

##  <a name="copy"></a>  CAtlArray::Copy

调用此方法将一个数组的元素复制到另一个。

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>参数

*aSrc*<br/>
要复制到一个数组的元素的源。

### <a name="remarks"></a>备注

调用此方法来覆盖一个数组的元素与另一个数组的元素。 如有必要，将分配内存来容纳新元素。 不能将数组的元素复制到本身。

如果要保留现有数组的内容，请使用[CAtlArray::Append](#append)相反。

在调试版本中 ATLASSERT 情况下会引发的现有`CAtlArray`对象不是有效的或者如果*aSrc*引用同一对象。 在发布版本中可能导致不可预知的行为的参数无效。

> [!NOTE]
> `CAtlArray::Copy` 不支持使用创建的元素组成的数组[CAutoPtr](../../atl/reference/cautoptr-class.md)类。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

调用此方法以从数组中移除任何空元素。

```
void FreeExtra() throw();
```

### <a name="remarks"></a>备注

任何空元素将被删除，但大小和数组的上限绑定保持不变。

在调试版本中将引发 ATLASSERT CAtlArray 对象不是有效的则数组将超出其最大大小。

##  <a name="getat"></a>  CAtlArray::GetAt

调用此方法从数组对象中检索单个元素。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>参数

*iElement*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需的数组元素的引用。

### <a name="remarks"></a>备注

在调试版本中 ATLASSERT 情况下会引发*iElement*超过数组中的元素数。 在发布版本中无效的参数可能会导致不可预知的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

调用此方法以返回数组中存储的元素数量。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回数组中存储的元素数量。

### <a name="remarks"></a>备注

返回的值数组中的第一个元素位于位置 0，因为`GetCount`始终为 1 大于最大的索引。

### <a name="example"></a>示例

有关示例，请参阅[CAtlArray::GetAt](#getat)。

##  <a name="getdata"></a>  CAtlArray::GetData

调用此方法以返回指向数组中的第一个元素的指针。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>返回值

返回指向数组中存储的第一个元素的内存位置的指针。 如果没有元素可用，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

要用于将元素添加到数组的数据类型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

调用此方法要插入到另一个数组。

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>参数

*iStart*<br/>
数组是要插入的索引。

*paNew*<br/>
要插入的数组。

### <a name="remarks"></a>备注

数组中的元素*paNew*复制到数组对象，开始元素*iStart*。 现有数组元素都将移以避免被覆盖。

在调试版本中 ATLASSERT 情况下会引发`CAtlArray`对象不是有效的或者如果*paNew*指针为 NULL 或无效。

> [!NOTE]
> `CAtlArray::InsertArrayAt` 不支持使用创建的元素组成的数组[CAutoPtr](../../atl/reference/cautoptr-class.md)类。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

数组对象调用此方法以插入新元素 （或一个元素的多个副本）。

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>参数

*iElement*<br/>
元素的位置插入索引。

*元素*<br/>
要插入的元素的值。

*nCount*<br/>
要添加的元素数。

### <a name="remarks"></a>备注

将一个或多个元素插入到索引处开始的数组*iElement*。 现有元素移动以避免被覆盖。

在调试版本中 ATLASSERT 情况下会引发`CAtlArray`对象无效，要添加的元素数为零，或组合的元素数是太大，要包含的数组。 在零售版本中传递了无效参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

调用此方法来测试如果数组为空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果数组为空，则返回 false 否则，则返回 true。

### <a name="remarks"></a>备注

数组被认为如果它不包含任何元素为空。 因此，即使该数组包含空元素，它不为空。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  CAtlArray::operator]

调用此运算符可返回数组中的元素的引用。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>参数

*iElement*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需的数组元素的引用。

### <a name="remarks"></a>备注

执行到相似的功能[CAtlArray::GetAt](#getat)。 与 MFC 类不同[CArray](../../mfc/reference/carray-class.md)，此运算符不能用作替代[CAtlArray::SetAt](#setat)。

在调试版本中 ATLASSERT 情况下会引发*iElement*超出了数组中元素的总数。 在零售版本中无效的参数可能会导致不可预知的结果。

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

要用于检索数组中元素的数据类型。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

调用此方法以从数组对象中移除所有元素。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

从数组对象中移除所有元素。

此方法调用[CAtlArray::SetCount](#setcount)来调整数组的大小，并随后释放任何已分配的内存。

### <a name="example"></a>示例

有关示例，请参阅[CAtlArray::IsEmpty](#isempty)。

##  <a name="removeat"></a>  CAtlArray::RemoveAt

调用此方法以从数组中移除一个或多个元素。

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>参数

*iElement*<br/>
要移除的第一个元素的索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

从数组中移除一个或多个元素。 剩余所有元素都向下都移动。 上限将减少，但之前调用，不释放内存[CAtlArray::FreeExtra](#freeextra)进行。

在调试版本中 ATLASSERT 情况下会引发`CAtlArray`对象不是有效的或者，如果总*iElement*并*nCount*超出了数组中元素的总数。 在零售版本中无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

调用此方法以设置元素值的数组对象中。

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>参数

*iElement*<br/>
指向要设置的数组元素的索引。

*元素*<br/>
指定元素的新值。

### <a name="remarks"></a>备注

在调试版本中 ATLASSERT 情况下会引发*iElement*超过数组中的元素数。 在零售版本中无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

有关示例，请参阅[CAtlArray::GetAt](#getat)。

##  <a name="setcount"></a>  CAtlArray::SetCount

调用此方法以设置数组对象的大小。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>参数

*nNewSize*<br/>
数组所需的大小。

*nGrowBy*<br/>
一个值，该值用于确定缓冲区的大小。 值为-1 会导致将用于在内部计算的值。

### <a name="return-value"></a>返回值

如果数组都在其他方面的成功已调整大小，则为 false，则返回 true。

### <a name="remarks"></a>备注

数组可增加或减少的大小。 如果增加，额外的空元素添加到数组。 如果减小时，将删除具有最大索引的元素，并释放内存。

使用此方法使用它之前设置数组的大小。 如果`SetCount`未使用，将添加元素的过程-执行后续的内存分配和 — 将降低性能和内存碎片。

### <a name="example"></a>示例

有关示例，请参阅[CAtlArray::GetData](#getdata)。

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

调用此方法以扩展所需的数组的数组对象中设置元素的值。

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>参数

*iElement*<br/>
指向要设置的数组元素的索引。

*元素*<br/>
指定元素的新值。

### <a name="remarks"></a>备注

替换由索引指向的元素的值。 如果*iElement*大于当前大小的数组，数组自动使用提高调用[CAtlArray::SetCount](#setcount)。 在调试版本中 ATLASSERT 情况下会引发`CAtlArray`对象无效。 在零售版本中无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>请参阅

[MMXSwarm 示例](../../visual-cpp-samples.md)<br/>
[DynamicConsumer 示例](../../visual-cpp-samples.md)<br/>
[UpdatePV 示例](../../visual-cpp-samples.md)<br/>
[字幕示例](../../visual-cpp-samples.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
