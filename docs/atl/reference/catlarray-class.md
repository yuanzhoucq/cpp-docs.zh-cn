---
title: CAtlArray 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423458"
---
# <a name="catlarray-class"></a>CAtlArray 类

此类实现数组对象。

## <a name="syntax"></a>语法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>parameters

*E*<br/>
要存储在数组中的数据类型。

*ETraits*<br/>
用于复制或移动元素的代码。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[添加](#add)|调用此方法可将元素添加到数组对象。|
|[Append](#append)|调用此方法可将一个数组的内容添加到另一个数组的末尾。|
|[AssertValid](#assertvalid)|调用此方法可确认数组对象是否有效。|
|[CAtlArray](#catlarray)|构造函数。|
|[~ CAtlArray](#dtor)|析构函数。|
|[Copy](#copy)|调用此方法可将一个数组的元素复制到另一个数组。|
|[FreeExtra](#freeextra)|调用此方法可从数组中移除任何空元素。|
|[GetAt](#getat)|调用此方法可从数组对象中检索单个元素。|
|[GetCount](#getcount)|调用此方法可返回数组中存储的元素数。|
|[GetData](#getdata)|调用此方法以返回指向数组中第一个元素的指针。|
|[InsertArrayAt](#insertarrayat)|调用此方法以将一个数组插入到另一个数组中。|
|[InsertAt](#insertat)|调用此方法可将新元素（或元素的多个副本）插入数组对象。|
|[IsEmpty](#isempty)|调用此方法可测试数组是否为空。|
|[RemoveAll](#removeall)|调用此方法可从数组对象中移除所有元素。|
|[RemoveAt](#removeat)|调用此方法可从数组中移除一个或多个元素。|
|[SetAt](#setat)|调用此方法可设置数组对象中的元素的值。|
|[SetAtGrow](#setatgrow)|调用此方法可设置数组对象中的元素的值，并根据需要扩展该数组。|
|[SetCount](#setcount)|调用此方法可设置数组对象的大小。|

### <a name="operators"></a>运算符

|||
|-|-|
|[操作员&#91;&#93;](#operator_at)|调用此运算符可返回对数组中的元素的引用。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[INARGTYPE](#inargtype)|用于向数组添加元素的数据类型。|
|[OUTARGTYPE](#outargtype)|用于检索数组中的元素的数据类型。|

## <a name="remarks"></a>备注

`CAtlArray` 提供用于创建和管理用户定义类型的元素数组的方法。 尽管类似于标准 C 数组，但 `CAtlArray` 对象可以根据需要动态收缩和增长。 数组索引始终从位置0开始，上限可以固定，或允许在添加新元素时进行扩展。

对于包含少量元素的数组，可以使用 ATL 类[CSimpleArray](../../atl/reference/csimplearray-class.md) 。

`CAtlArray` 与 MFC 的 `CArray` 类密切相关，并且将在 MFC 项目中运行，但不支持序列化。

有关详细信息，请参阅[ATL Collection 类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll

##  <a name="add"></a>CAtlArray：： Add

调用此方法可将元素添加到数组对象。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>parameters

*element*<br/>
要添加到数组中的元素。

### <a name="return-value"></a>返回值

返回所添加的元素的索引。

### <a name="remarks"></a>备注

新元素添加到数组的末尾。 如果未提供任何元素，则添加一个空元素;也就是说，数组的大小增加，就好像添加了实元素一样。 如果操作失败，则会调用[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)参数 E_OUTOFMEMORY。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>CAtlArray：： Append

调用此方法可将一个数组的内容添加到另一个数组的末尾。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>parameters

*aSrc*<br/>
要追加的数组。

### <a name="return-value"></a>返回值

返回第一个追加的元素的索引。

### <a name="remarks"></a>备注

提供的数组中的元素将添加到现有数组的末尾。 如有必要，将分配内存以容纳新元素。

数组必须具有相同的类型，并且不能将数组追加到其自身。

在调试版本中，如果 `CAtlArray` 参数不是有效数组或*aSrc*引用同一对象，则会引发 ATLASSERT。 在发布版本中，无效参数可能导致不可预知的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>CAtlArray::AssertValid

调用此方法可确认数组对象是否有效。

```
void AssertValid() const;
```

### <a name="remarks"></a>备注

如果 array 对象无效，ATLASSERT 将引发断言。 仅当定义 _DEBUG 时，此方法才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>CAtlArray::CAtlArray

构造函数。

```
CAtlArray() throw();
```

### <a name="remarks"></a>备注

初始化数组对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>CAtlArray：： ~ CAtlArray

析构函数。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>备注

释放数组对象使用的所有资源。

##  <a name="copy"></a>CAtlArray：： Copy

调用此方法可将一个数组的元素复制到另一个数组。

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>parameters

*aSrc*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

调用此方法可覆盖一个数组中具有另一个数组元素的元素。 如有必要，将分配内存以容纳新元素。 不能将数组的元素复制到其自身。

如果要保留数组的现有内容，请改为使用[CAtlArray：： Append](#append) 。

在调试版本中，如果现有 `CAtlArray` 对象无效或*aSrc*引用同一对象，则会引发 ATLASSERT。 在发布版本中，无效参数可能导致不可预知的行为。

> [!NOTE]
> `CAtlArray::Copy` 不支持包含通过[CAutoPtr](../../atl/reference/cautoptr-class.md)类创建的元素的数组。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>CAtlArray::FreeExtra

调用此方法可从数组中移除任何空元素。

```
void FreeExtra() throw();
```

### <a name="remarks"></a>备注

任何空元素都将被删除，但数组的大小和上限仍保持不变。

在调试版本中，如果 CAtlArray 对象无效，或者数组将超出其最大大小，则会引发 ATLASSERT。

##  <a name="getat"></a>CAtlArray：： GetAt

调用此方法可从数组对象中检索单个元素。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>parameters

*iElement*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需数组元素的引用。

### <a name="remarks"></a>备注

在调试版本中，如果*iElement*超过数组中的元素数，则会引发 ATLASSERT。 在发布版本中，无效参数可能导致不可预知的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>CAtlArray：： GetCount

调用此方法可返回数组中存储的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回数组中存储的元素数。

### <a name="remarks"></a>备注

数组中第一个元素的位置为0时，`GetCount` 返回的值始终大于最大的索引。

### <a name="example"></a>示例

请参阅[CAtlArray：： GetAt](#getat)的示例。

##  <a name="getdata"></a>CAtlArray：：

调用此方法以返回指向数组中第一个元素的指针。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>返回值

返回一个指向存储数组中第一个元素的内存位置的指针。 如果没有可用的元素，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>CAtlArray::INARGTYPE

用于向数组添加元素的数据类型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>CAtlArray::InsertArrayAt

调用此方法以将一个数组插入到另一个数组中。

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>parameters

*iStart*<br/>
要插入数组的位置的索引。

*paNew*<br/>
要插入的数组。

### <a name="remarks"></a>备注

数组*paNew*中的元素将复制到数组对象中，从元素*iStart*开始。 将移动现有数组元素，以避免被覆盖。

在调试版本中，如果 `CAtlArray` 对象无效，或者*paNew*指针为 NULL 或无效，则会引发 ATLASSERT。

> [!NOTE]
> `CAtlArray::InsertArrayAt` 不支持包含通过[CAutoPtr](../../atl/reference/cautoptr-class.md)类创建的元素的数组。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>CAtlArray：： InsertAt

调用此方法可将新元素（或元素的多个副本）插入数组对象。

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>parameters

*iElement*<br/>
要在其中插入元素的索引。

*element*<br/>
要插入的元素的值。

*nCount*<br/>
要添加的元素的数目。

### <a name="remarks"></a>备注

将一个或多个元素插入到数组中，从索引*iElement*开始。 将移动现有元素，以避免被覆盖。

在调试版本中，如果 `CAtlArray` 对象无效、要添加的元素的数量为零或元素的组合数量太大而无法包含，则将引发 ATLASSERT。 在零售版本中，传递无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>CAtlArray：： IsEmpty

调用此方法可测试数组是否为空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果数组为空，则返回 true，否则返回 false。

### <a name="remarks"></a>备注

如果数组不包含任何元素，则称其为空。 因此，即使数组包含空元素，也不是空的。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>CAtlArray：： operator []

调用此运算符可返回对数组中的元素的引用。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>parameters

*iElement*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需数组元素的引用。

### <a name="remarks"></a>备注

对[CAtlArray：： GetAt](#getat)执行类似的函数。 与 MFC 类[CArray](../../mfc/reference/carray-class.md)不同，此运算符不能用作[CAtlArray：： SetAt](#setat)的替换。

在调试版本中，如果*iElement*超过数组中的元素总数，则会引发 ATLASSERT。 在零售版本中，无效的参数可能会导致不可预知的结果。

##  <a name="outargtype"></a>CAtlArray::OUTARGTYPE

用于检索数组中的元素的数据类型。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>CAtlArray：： RemoveAll

调用此方法可从数组对象中移除所有元素。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

从数组对象中移除所有元素。

此方法调用[CAtlArray：： SetCount](#setcount)以调整数组的大小，然后释放任何分配的内存。

### <a name="example"></a>示例

请参阅[CAtlArray：： IsEmpty](#isempty)的示例。

##  <a name="removeat"></a>CAtlArray：： RemoveAt

调用此方法可从数组中移除一个或多个元素。

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>parameters

*iElement*<br/>
要移除的第一个元素的索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

从数组中移除一个或多个元素。 剩余的任何元素将向下移动。 上限减少，但在调用[CAtlArray：： FreeExtra](#freeextra)之前不会释放内存。

在调试版本中，如果 `CAtlArray` 对象无效，或者*iElement*和*nCount*的组合总计超过数组中的元素总数，则会引发 ATLASSERT。 在零售版本中，无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>CAtlArray：： SetAt

调用此方法可设置数组对象中的元素的值。

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>parameters

*iElement*<br/>
指向要设置的数组元素的索引。

*element*<br/>
已指定元素的新值。

### <a name="remarks"></a>备注

在调试版本中，如果*iElement*超过数组中的元素数，则会引发 ATLASSERT。 在零售版本中，无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

请参阅[CAtlArray：： GetAt](#getat)的示例。

##  <a name="setcount"></a>CAtlArray::SetCount

调用此方法可设置数组对象的大小。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>parameters

*nNewSize*<br/>
数组的所需大小。

*nGrowBy*<br/>
一个值，该值用于确定生成缓冲区的大小。 如果值为-1，则将使用内部计算的值。

### <a name="return-value"></a>返回值

如果成功调整数组的大小，则返回 true; 否则返回 false。

### <a name="remarks"></a>备注

可以增加或减少数组大小。 如果增加，则将额外的空元素添加到数组中。 如果减少，将删除具有最大索引的元素，并释放内存。

使用此方法可以在使用之前设置数组的大小。 如果未使用 `SetCount`，则添加元素（以及执行的后续内存分配）的过程将降低性能和碎片内存。

### <a name="example"></a>示例

请参阅[CAtlArray：：](#getdata)的示例。

##  <a name="setatgrow"></a>CAtlArray::SetAtGrow

调用此方法可设置数组对象中的元素的值，并根据需要扩展该数组。

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>parameters

*iElement*<br/>
指向要设置的数组元素的索引。

*element*<br/>
已指定元素的新值。

### <a name="remarks"></a>备注

替换索引所指向的元素的值。 如果*iElement*大于数组的当前大小，则使用对[CAtlArray：： SetCount](#setcount)的调用来自动增加数组。 在调试版本中，如果 `CAtlArray` 对象无效，则会引发 ATLASSERT。 在零售版本中，无效的参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>另请参阅

[MMXSwarm 示例](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer 示例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 示例](../../overview/visual-cpp-samples.md)<br/>
[天棚示例](../../overview/visual-cpp-samples.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
