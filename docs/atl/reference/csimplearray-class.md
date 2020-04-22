---
title: CSimpleArray 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: d3386687757412d09e4df29e84f691f1615c472a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746471"
---
# <a name="csimplearray-class"></a>CSimpleArray 类

此类提供了用于管理简单数组的方法。

## <a name="syntax"></a>语法

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在数组中的数据类型。

*TEqual*<br/>
特征对象，定义*T*类型元素的相等性测试。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[简单数组：：C简单数组](#csimplearray)|简单数组的构造函数。|
|[简单数组：：*C简单数组](#dtor)|简单数组的析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[简单数组：：添加](#add)|向数组添加新元素。|
|[简单数组：查找](#find)|在数组中查找元素。|
|[CSimplearray：获取数据](#getdata)|返回指向数组中存储数据的指针。|
|[简单数组：获取 Size](#getsize)|返回存储在数组中的元素数。|
|[简单数组：：删除](#remove)|从数组中删除给定元素。|
|[简单数组：：删除所有](#removeall)|从数组中删除所有元素。|
|[简单数组：：删除At](#removeat)|从数组中删除指定的元素。|
|[简单数组：：设置Atindex](#setatindex)|设置数组中的指定元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|从数组中检索元素。|
|[CSimpleArray：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

`CSimpleArray`提供了用于创建和管理任何给定类型的`T`简单数组的方法。

该参数`TEqual`提供了一种为类型中的`T`两个元素定义相等函数的方法。 通过创建类似于[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)的类，可以更改任何给定数组的相等测试的行为。 例如，在处理指针数组时，将相等性定义为根据指针引用的值可能很有用。 默认实现使用运算符 **_（）**。

和`CSimpleArray` [CSimpleMap](../../atl/reference/csimplemap-class.md)都专为少量元素而设计。 当数组包含大量元素时，应使用[CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap。](../../atl/reference/catlmap-class.md)

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>简单数组：：添加

向数组添加新元素。

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>参数

*t*<br/>
要添加到数组的元素。

### <a name="return-value"></a>返回值

如果元素已成功添加到数组中，则返回 TRUE，否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>简单数组：：C简单数组

数组对象的构造函数。

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>参数

*src*<br/>
一个现有的 `CSimpleArray` 对象。

### <a name="remarks"></a>备注

初始化数据成员，创建新的空`CSimpleArray`对象或现有`CSimpleArray`对象的副本。

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>简单数组：：*C简单数组

析构函数。

```
~CSimpleArray();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="csimplearrayfind"></a><a name="find"></a>简单数组：查找

在数组中查找元素。

```
int Find(const T& t) const;
```

### <a name="parameters"></a>参数

*t*<br/>
要为其搜索的元素。

### <a name="return-value"></a>返回值

返回找到的元素的索引，如果找不到该元素，则返回 -1。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimplearray：获取数据

返回指向数组中存储数据的指针。

```
T* GetData() const;
```

### <a name="return-value"></a>返回值

返回指向数组中数据的指针。

## <a name="csimplearraygetsize"></a><a name="getsize"></a>简单数组：获取 Size

返回存储在数组中的元素数。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

返回存储在数组中的元素数。

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray：：运算符\[\]

从数组中检索元素。

```
T& operator[](int nindex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
元素索引。

### <a name="return-value"></a>返回值

返回*nIndex*引用的数组的元素。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray：：运算符 |

赋值运算符。

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>参数

*src*<br/>
要复制的数组。

### <a name="return-value"></a>返回值

返回指向更新`CSimpleArray`对象的指针。

### <a name="remarks"></a>备注

将*src* `CSimpleArray`引用的对象中的所有元素复制到当前数组对象中，替换所有现有数据。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>简单数组：：删除

从数组中删除给定元素。

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>参数

*t*<br/>
要从数组中删除的元素。

### <a name="return-value"></a>返回值

如果找到并删除了该元素，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

删除元素时，将重新编号数组中的剩余元素以填充空白空间。

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>简单数组：：删除所有

从数组中删除所有元素。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

删除当前存储在数组中的所有元素。

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>简单数组：：删除At

从数组中删除指定的元素。

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指向要删除的元素的索引。

### <a name="return-value"></a>返回值

如果删除元素，则返回 TRUE;如果索引无效，则返回 FALSE。

### <a name="remarks"></a>备注

删除元素时，将重新编号数组中的剩余元素以填充空白空间。

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>简单数组：：设置Atindex

在数组中设置指定元素。

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要更改的元素的索引。

*t*<br/>
要分配给指定元素的值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;如果索引无效，则返回 FALSE。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
