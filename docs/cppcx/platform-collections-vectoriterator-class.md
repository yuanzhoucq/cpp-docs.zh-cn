---
title: Platform::Collections::VectorIterator 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: 8e776e0f5d479ee8633efa647ac41e6b1b5f9c0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595593"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 类

为从 Windows 运行时 IVector 接口派生的对象提供标准模板库迭代器。

VectorIterator 是存储类型 VectorProxy 元素的代理迭代器\<T >。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

## <a name="syntax"></a>语法

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>参数

*T*<br/>
VectorIterator 模板类的类型名称。

### <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`difference_type`|指针差异 (ptrdiff_t)。|
|`iterator_category`|随机访问迭代器 (::std::random_access_iterator_tag) 的类别。|
|`pointer`|指向内部的类型，Platform::Collections::Details::VectorProxy\<T >，即实现 VectorIterator 所需。|
|`reference`|引用的内部类型，Platform::Collections::Details::VectorProxy\<T >、、，它是实现 VectorIterator 所需。|
|`value_type`|`T` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|初始化 VectorIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[VectorIterator::operator- 运算符](#operator-minus)|从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。|
|[VectorIterator::operator-- 运算符](#operator-decrement)|递减当前 VectorIterator。|
|[VectorIterator::operator!= 运算符](#operator-inequality)|指示当前 VectorIterator 是否不等于指定的 VectorIterator。|
|[VectorIterator::operator* 运算符](#operator-dereference)|检索对当前 VectorIterator 指定的元素的引用。|
|[VectorIterator::operator\[\]](#operator-at)|检索对属于当前 VectorIterator 的指定偏移量的元素的引用。|
|[VectorIterator::operator+ 运算符](#operator-plus)|返回引用偏移指定 VectorIterator 指定偏移量处的元素的 VectorIterator。|
|[VectorIterator::operator++ 运算符](#operator-increment)|递增当前 VectorIterator。|
|[VectorIterator::operator+= 运算符](#operator-plus-assign)|按指定偏移量递增当前 VectorIterator。|
|[VectorIterator::operator< 运算符](#operator-less-than)|指示当前 VectorIterator 是否小于指定的 VectorIterator。|
|[Vectoriterator:: Operator\<= 运算符](#operator-less-than-or-equals)|指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。|
|[VectorIterator::operator-= 运算符](#operator-subtract-assign)|按指定偏移量递减当前 VectorIterator。|
|[VectorIterator::operator== 运算符](#operator-equality)|指示当前 VectorIterator 是否等于指定的 VectorIterator。|
|[VectorIterator::operator> 运算符](#operator-greater-than)|指示当前 VectorIterator 是否大于指定的 VectorIterator。|
|[VectorIterator::operator-> 运算符](#operator-arrow)|检索当前 VectorIterator 引用的元素的地址。|
|[VectorIterator::operator>= 运算符](#operator-greater-than-or-equal)|指示当前 VectorIterator 是否大于或等于指定的 VectorIterator。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorIterator`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="operator-arrow"></a>  Vectoriterator:: Operator-&gt;运算符

检索当前 VectorIterator 引用的元素的地址。

### <a name="syntax"></a>语法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>返回值

当前 VectorIterator 引用的元素的值。

返回值的类型是此运算符的实现所需的未指定内部类型。

## <a name="operator-decrement"></a>  Vectoriterator:: Operator-运算符

递减当前 VectorIterator。

### <a name="syntax"></a>语法

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>返回值

第一个语法先递减，然后返回当前 VectorIterator。 第二个语法返回当前 VectorIterator 的副本，然后递减当前 VectorIterator。

### <a name="remarks"></a>备注

第一个 VectorIterator 语法预先递减当前 VectorIterator。

第二个语法后递减当前 VectorIterator。 第二个语法中的 `int` 类型指示后递减操作，而不是实际整数操作数。

## <a name="operator-dereference"></a>  Vectoriterator:: Operator\*运算符

检索当前 VectorIterator 指定的元素的地址。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 VectorIterator 指定的元素。

## <a name="operator-equality"></a>  Vectoriterator:: Operator = = 运算符

指示当前 VectorIterator 是否等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**当前 VectorIterator 是否等于*其他*; 否则为**false**。

## <a name="operator-greater-than"></a>  Vectoriterator:: Operator&gt;运算符

指示当前 VectorIterator 是否大于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**当前 VectorIterator 是否大于*其他*; 否则为**false**。

## <a name="operator-greater-than-or-equals"></a>  Vectoriterator:: Operator&gt;= 运算符

指示当前 VectorIterator 是否大于或等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**当前 VectorIterator 是否大于或等于*其他*; 否则为**false**。

## <a name="operator-increment"></a>  Vectoriterator:: Operator + + 运算符

递增当前 VectorIterator。

### <a name="syntax"></a>语法

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>返回值

第一个语法先递增然后返回当前 VectorIterator。 第二个语法返回当前 VectorIterator 的副本然后递增当前 VectorIterator。

### <a name="remarks"></a>备注

第一个 VectorIterator 语法预先递增当前 VectorIterator。

第二个语法后递增当前 VectorIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。

## <a name="operator-inequality"></a>  Vectoriterator:: Operator ！ = 运算符

指示当前 VectorIterator 是否不等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**当前 VectorIterator 是否不相等*其他*; 否则为**false**。

## <a name="operator-less-than"></a>  Vectoriterator:: Operator&lt;运算符

指示当前 VectorIterator 是否小于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**如果当前 VectorIterator 是否小于*其他*; 否则为**false**。

## <a name="operator-less-than-or-equals"></a>  Vectoriterator:: Operator&lt;= 运算符

指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**true**当前 VectorIterator 是否小于或等于*其他*; 否则为**false**。

## <a name="operator-minus"></a>  Vectoriterator:: Operator-运算符

从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。

### <a name="syntax"></a>语法

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*n*<br/>
元素数目。

*other*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

第一个运算符语法返回一个 VectorIterator 对象，该对象比当前 VectorIterator 少 `n` 个元素。 第二个运算符语法返回介于当前 VectorIterator 和 `other` VectorIterator 之间的元素数目。

## <a name="operator-plus-assign"></a>  Vectoriterator:: Operator + = 运算符

按指定偏移量递增当前 VectorIterator。

### <a name="syntax"></a>语法

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

更新的 VectorIterator。

## <a name="operator-plus"></a>  Vectoriterator:: Operator + 运算符

返回引用偏移指定 VectorIterator 指定偏移量处的元素的 VectorIterator。

### <a name="syntax"></a>语法

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>参数

*T*<br/>
在第二个语法中，VectorIterator 的类型名称。

*n*<br/>
整数偏移。

*i*<br/>
在第二个语法，一个 VectorIterator。

### <a name="return-value"></a>返回值

在第一个语法中，引用偏移当前 VectorIterator 指定偏移量处的元素的 VectorIterator。

在第二个语法中，引用偏移参数 `i` 开头指定偏移量处的元素的 VectorIterator。

### <a name="remarks"></a>备注

第一个语法示例

## <a name="operator-minus-equals"></a>  Vectoriterator:: Operator-= 运算符

按指定偏移量递减当前 VectorIterator。

### <a name="syntax"></a>语法

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

更新的 VectorIterator。

## <a name="operator-at"></a>  VectorIterator::operator\[\]

检索对属于当前 VectorIterator 的指定偏移量的元素的引用。

### <a name="syntax"></a>语法

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

`n` 元素从当前 VectorIterator 移置开的元素。

## <a name="ctor"></a>  Vectoriterator:: Vectoriterator 构造函数

初始化 VectorIterator 类的新实例。

### <a name="syntax"></a>语法

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>参数

*v*<br/>
IVector\<T > 对象。

### <a name="remarks"></a>备注

第一个语法示例是默认构造函数。 第二个语法示例是用来构造从 IVector VectorIterator 的显式构造函数\<T > 对象。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)
