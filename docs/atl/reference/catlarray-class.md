---
title: CAtlarray 类
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
ms.openlocfilehash: 607af2adaa3ef28a768812f3c811eb2ed3169ad9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748788"
---
# <a name="catlarray-class"></a>CAtlarray 类

此类实现数组对象。

## <a name="syntax"></a>语法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>参数

*E*<br/>
要存储在数组中的数据类型。

*埃特格*<br/>
用于复制或移动元素的代码。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[添加](#add)|调用此方法以向数组对象添加元素。|
|[附加](#append)|调用此方法将一个数组的内容添加到另一个数组的末尾。|
|[断言有效](#assertvalid)|调用此方法以确认数组对象是否有效。|
|[克拉拉](#catlarray)|构造函数。|
|[*CAtlarray](#dtor)|析构函数。|
|[复制](#copy)|调用此方法将一个数组的元素复制到另一个数组。|
|[免费额外](#freeextra)|调用此方法从数组中删除任何空元素。|
|[GetAt](#getat)|调用此方法从数组对象检索单个元素。|
|[GetCount](#getcount)|调用此方法以返回存储在数组中的元素数。|
|[GetData](#getdata)|调用此方法以返回指向数组中第一个元素的指针。|
|[插入Arrayat](#insertarrayat)|调用此方法将一个数组插入到另一个数组中。|
|[插入At](#insertat)|调用此方法以将新元素（或元素的多个副本）插入数组对象。|
|[是空的](#isempty)|调用此方法以测试数组是否为空。|
|[全部删除](#removeall)|调用此方法从数组对象中删除所有元素。|
|[RemoveAt](#removeat)|调用此方法从数组中删除一个或多个元素。|
|[Setat](#setat)|调用此方法以设置数组对象中元素的值。|
|[SetAt增长](#setatgrow)|调用此方法以设置数组对象中元素的值，根据需要展开数组。|
|[设置计数](#setcount)|调用此方法以设置数组对象的大小。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 &#91;&#93;](#operator_at)|调用此运算符以返回对数组中元素的引用。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[INARG型](#inargtype)|用于向数组添加元素的数据类型。|
|[出型](#outargtype)|用于从数组检索元素的数据类型。|

## <a name="remarks"></a>备注

`CAtlArray`提供了创建和管理用户定义类型元素数组的方法。 尽管与标准 C 数组类似，`CAtlArray`但对象可以根据需要动态收缩和增长。 数组索引始终从位置 0 开始，并且上边界可以固定，或者允许在添加新元素时展开。

对于具有少量元素的数组，可以使用 ATL 类[CSimplearray。](../../atl/reference/csimplearray-class.md)

`CAtlArray`与 MFC 的`CArray`类别密切相关，将在 MFC 项目中工作，尽管没有序列化支持。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>克拉拉：添加

调用此方法以向数组对象添加元素。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>参数

*元素*<br/>
要添加到数组的元素。

### <a name="return-value"></a>返回值

返回添加元素的索引。

### <a name="remarks"></a>备注

新元素将添加到数组的末尾。 如果未提供任何元素，则添加空元素;如果未提供任何元素，则添加空元素。也就是说，数组的大小增加，就像添加了实际元素一样。 如果操作失败，则使用参数E_OUTOFMEMORY调用[AtlThrow。](debugging-and-error-reporting-global-functions.md#atlthrow)

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray：：附加

调用此方法将一个数组的内容添加到另一个数组的末尾。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>参数

*阿斯尔克*<br/>
要追加的数组。

### <a name="return-value"></a>返回值

返回第一个附加元素的索引。

### <a name="remarks"></a>备注

提供数组中的元素将添加到现有数组的末尾。 如有必要，将分配内存以适应新元素。

数组必须具有相同的类型，并且无法将数组追加到自身。

在调试生成中，如果参数不是有效的数组或`CAtlArray`*aSrc*引用同一对象，则将引发 ATLASSERT。 在发布版本中，无效参数可能导致不可预知的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlarray：：断言有效

调用此方法以确认数组对象是否有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>备注

如果数组对象无效，ATLASSERT 将引发断言。 仅当定义了_DEBUG时，此方法才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>克拉拉：克拉拉

构造函数。

```
CAtlArray() throw();
```

### <a name="remarks"></a>备注

初始化数组对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlarray：_CAtlarray

析构函数。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>备注

释放数组对象使用的任何资源。

## <a name="catlarraycopy"></a><a name="copy"></a>克拉拉：复制

调用此方法将一个数组的元素复制到另一个数组。

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>参数

*阿斯尔克*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

调用此方法用另一个数组的元素覆盖一个数组的元素。 如有必要，将分配内存以适应新元素。 无法将数组的元素复制到自身。

如果要保留数组的现有内容，请使用[CAtlArray：：：附加](#append)。

在调试生成中，如果现有`CAtlArray`对象无效，或者*aSrc*引用同一对象，则将引发 ATLASSERT。 在发布版本中，无效参数可能导致不可预知的行为。

> [!NOTE]
> `CAtlArray::Copy`不支持由[CAutoPtr](../../atl/reference/cautoptr-class.md)类创建的元素组成的数组。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlarray：免费额外

调用此方法从数组中删除任何空元素。

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>备注

删除任何空元素，但数组的大小和上限保持不变。

在调试生成中，如果 CAtlArray 对象无效，或者数组将超过其最大大小，将引发 ATLASSERT。

## <a name="catlarraygetat"></a><a name="getat"></a>克拉拉：：获取At

调用此方法从数组对象检索单个元素。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>参数

*i元素*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需数组元素的引用。

### <a name="remarks"></a>备注

在调试生成中，如果*iElement*超过数组中的元素数，将引发 ATLASSERT。 在发布版本中，无效的参数可能会导致不可预知的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlarray：获取计数

调用此方法以返回存储在数组中的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回存储在数组中的元素数。

### <a name="remarks"></a>备注

由于数组中的第一个元素位于位置 0，因此返回`GetCount`的值始终大于最大索引 1。

### <a name="example"></a>示例

请参阅[CAtlArray 的示例：：GetAt](#getat)。

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlarray：获取数据

调用此方法以返回指向数组中第一个元素的指针。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>返回值

返回指向存储数组中第一个元素的内存位置的指针。 如果没有可用的元素，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>克拉拉：：INARGTYPE

用于向数组添加元素的数据类型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>克拉拉：：插入Arrayat

调用此方法将一个数组插入到另一个数组中。

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>参数

*i 开始*<br/>
要插入数组的索引。

*paNew*<br/>
要插入的数组。

### <a name="remarks"></a>备注

数组*paNew*中的元素从元素*iStart*开始复制到数组对象中。 移动现有数组元素以避免被覆盖。

在调试生成中，如果`CAtlArray`对象无效，或者如果*paNew*指针为 NULL 或无效，将引发 ATLASSERT。

> [!NOTE]
> `CAtlArray::InsertArrayAt`不支持由[CAutoPtr](../../atl/reference/cautoptr-class.md)类创建的元素组成的数组。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>克拉拉：：插入At

调用此方法以将新元素（或元素的多个副本）插入数组对象。

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>参数

*i元素*<br/>
要插入元素或元素的索引。

*元素*<br/>
要插入的元素或元素的值。

*nCount*<br/>
要添加的元素数。

### <a name="remarks"></a>备注

从索引*iElement*开始，将一个或多个元素插入数组。 移动现有元素以避免被覆盖。

在调试生成中，如果`CAtlArray`对象无效、要添加的元素数为零或组合的元素数太大，数组无法包含，则将引发 ATLASSERT。 在零售版本中，传递无效参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>克拉拉：：空

调用此方法以测试数组是否为空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果数组为空，则返回 true，否则为 false。

### <a name="remarks"></a>备注

如果数组不包含任何元素，则该数组表示为空。 因此，即使数组包含空元素，它也不为空。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray：：运算符 |

调用此运算符以返回对数组中元素的引用。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>参数

*i元素*<br/>
要返回的数组元素的索引值。

### <a name="return-value"></a>返回值

返回对所需数组元素的引用。

### <a name="remarks"></a>备注

执行与[CAtlArray 类似的功能：：getAt](#getat)。 与 MFC 类[CArray](../../mfc/reference/carray-class.md)不同，此运算符不能用作[CAtlArray：setAt](#setat)的替代品。

在调试生成中，如果*iElement*超过数组中的元素总数，将引发 ATLASSERT。 在零售生成中，无效参数可能会导致不可预知的结果。

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>克拉拉：：OUTARGTYPE

用于从数组检索元素的数据类型。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlarray：删除所有

调用此方法从数组对象中删除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

从数组对象中删除所有元素。

此方法调用[CAtlArray：：SetCount](#setcount)以调整数组的大小，然后释放任何分配的内存。

### <a name="example"></a>示例

请参阅[CAtlArray 的示例：：是空的](#isempty)。

## <a name="catlarrayremoveat"></a><a name="removeat"></a>克拉拉：：删除At

调用此方法从数组中删除一个或多个元素。

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>参数

*i元素*<br/>
要删除的第一个元素的索引。

*nCount*<br/>
要移除的元素数。

### <a name="remarks"></a>备注

从数组中删除一个或多个元素。 任何剩余元素都向下移动。 上限将递减，但在调用[CAtlArray：：：FreeExtra](#freeextra)之前不会释放内存。

在调试生成中，如果`CAtlArray`对象无效，或者如果*iElement*和*nCount*的总和超过数组中的元素总数，则将引发 ATLASSERT。 在零售版本中，无效参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>克拉拉：：Setat

调用此方法以设置数组对象中元素的值。

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>参数

*i元素*<br/>
指向要设置的数组元素的索引。

*元素*<br/>
已指定元素的新值。

### <a name="remarks"></a>备注

在调试生成中，如果*iElement*超过数组中的元素数，将引发 ATLASSERT。 在零售生成中，无效参数可能会导致不可预知的结果。

### <a name="example"></a>示例

请参阅[CAtlArray 的示例：：GetAt](#getat)。

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlarray：：设置计数

调用此方法以设置数组对象的大小。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>参数

*n 新尺寸*<br/>
数组所需的大小。

*nGrowBy*<br/>
用于确定使缓冲区有多大的值。 值 -1 会导致使用内部计算的值。

### <a name="return-value"></a>返回值

如果数组成功调整大小，则返回 true，否则为 false。

### <a name="remarks"></a>备注

数组的大小可以增加或减小。 如果增加，则向数组中添加额外的空元素。 如果减少，将删除索引最大的元素并释放内存。

使用此方法在使用数组之前设置数组的大小。 如果不`SetCount`使用，添加元素的过程（以及执行的后续内存分配）将降低性能和片段内存。

### <a name="example"></a>示例

请参阅[CAtlArray 的示例：：获取数据](#getdata)。

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlarray：setat增长

调用此方法以设置数组对象中元素的值，根据需要展开数组。

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>参数

*i元素*<br/>
指向要设置的数组元素的索引。

*元素*<br/>
已指定元素的新值。

### <a name="remarks"></a>备注

替换索引指向的元素的值。 如果*iElement*大于数组的当前大小，则使用对[CAtlArray：：setCount](#setcount)的调用会自动增加数组。 在调试生成中，如果对象无效，`CAtlArray`将引发 ATLASSERT。 在零售版本中，无效参数可能会导致不可预知的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>另请参阅

[MMXSwarm 样品](../../overview/visual-cpp-samples.md)<br/>
[动态消费者示例](../../overview/visual-cpp-samples.md)<br/>
[更新PV示例](../../overview/visual-cpp-samples.md)<br/>
[选框示例](../../overview/visual-cpp-samples.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
