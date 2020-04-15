---
title: Platform::Collections::VectorViewIterator 类
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363693"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator 类

为从 Windows 运行时`IVectorView`接口派生的对象提供标准模板库迭代器。

`ViewVectorIterator` 是存储 `VectorProxy<T>`类型的元素的代理迭代器。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

## <a name="syntax"></a>语法

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>参数

*T*<br/>
VectorViewIterator 模板类的类型名称。

### <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`difference_type`|指针差异 (ptrdiff_t)。|
|`iterator_category`|随机访问迭代器 (::std::random_access_iterator_tag) 的类别。|
|`pointer`|指向实现 VectorViewIterator 所需的内部类型的指针。|
|`reference`|对实现 VectorViewIterator 所需的内部类型的引用。|
|`value_type`|`T` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[矢量视图迭代器：：矢量视图迭代器](#ctor)|初始化 VectorViewIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[矢量视图迭代器：：运算符 - 运算符](#operator-minus)|从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。|
|[矢量视图迭代器：：运算符 -- 运算符](#operator-decrement)|递减当前 VectorViewIterator。|
|[矢量视图迭代器：：运算符！= 运算符](#operator-inequality)|指示当前 VectorViewIterator 是否不等于指定的 VectorViewIterator。|
|[矢量视图迭代器：：运算符* 运算符](#operator-dereference)|检索对当前 VectorViewIterator 指定的元素的引用。|
|[矢量视图迭代器：：运算符\[\]](#operator-at)|检索对偏移当前 VectorViewIterator 指定量的元素的引用。|
|[矢量视图迭代器：：运算符+ 运算符](#operator-plus)|返回引用偏移指定 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。|
|[矢量视图迭代器：：运算符* 运算符](#operator-increment)|递增当前 VectorViewIterator。|
|[矢量视图迭代器：：运算符= 运算符](#operator-plus-equals)|按指定偏移量递增当前 VectorViewIterator。|
|[矢量视图迭代器：：运算符<运算符](#operator-less-than)|指示当前 VectorViewIterator 是否小于指定 VectorViewIterator。|
|[矢量视图迭代器：：运算符\<= 运算符](#operator-less-than-or-equals)|指示当前 VectorViewIterator 是否小于或等于指定的 VectorViewIterator。|
|[矢量视图迭代器：：运算符-= 运算符](#operator-minus-assign)|按指定偏移量递减当前 VectorViewIterator。|
|[矢量视图迭代器：：运算符 = 运算符](#operator-equality)|指示当前 VectorViewIterator 是否等于指定 VectorViewIterator。|
|[VectorViewIterator::operator> 运算符](#operator-greater-than)|指示当前 VectorViewIterator 是否大于指定的 VectorViewIterator。|
|[矢量视图迭代器：：运算符->运算符](#operator-arrow)|检索当前 VectorViewIterator 引用的元素的地址。|
|[矢量视图迭代器：：运算符>= 运算符](#operator-greater-than-or-equals)|指示当前 VectorViewIterator 是否大于或等于指定的 VectorViewIterator。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorViewIterator`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>矢量视图迭代器：：运算符 -&gt;运算符

检索当前 VectorViewIterator 引用的元素的地址。

### <a name="syntax"></a>语法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>返回值

当前 VectorViewIterator 引用的元素的值。

返回值的类型是此运算符的实现所需的未指定内部类型。

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>矢量视图迭代器：：运算符 -- 运算符

递减当前 VectorViewIterator。

### <a name="syntax"></a>语法

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>返回值

第一个语法先递减，然后返回当前 VectorViewIterator。 第二个语法返回当前 VectorViewIterator 的副本，然后递减当前 VectorViewIterator。

### <a name="remarks"></a>备注

第一个 VectorViewIterator 语法预先递减当前 VectorViewIterator。

第二个语法后递减当前 VectorViewIterator。 第二个语法中的 `int` 类型指示后递减操作，而不是实际整数操作数。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>矢量视图迭代器：：运算符\*运算符

检索对当前 VectorViewIterator 指定的元素的引用。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 VectorViewIterator 指定的元素。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>矢量视图迭代器：：运算符 = 运算符

指示当前 VectorViewIterator 是否等于指定 VectorViewIterator。

### <a name="syntax"></a>语法

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorViewIterator。

### <a name="return-value"></a>返回值

**如果**电流`VectorViewIterator`等于*其他*， 则为 true ;否则，**假**。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>矢量视图迭代器：：运算符&gt;运算符

指示当前 VectorViewIterator 是否大于指定的 VectorViewIterator。

### <a name="syntax"></a>语法

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorViewIterator。

### <a name="return-value"></a>返回值

如果当前矢量视图器大于*其他*，**则为 true** ;否则，**假**。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>矢量视图迭代器：：运算符&gt;= 运算符

指示电流`VectorViewIterator`是否大于或等于指定的`VectorViewIterator`。

### <a name="syntax"></a>语法

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorViewIterator。

### <a name="return-value"></a>返回值

**如果**电流`VectorViewIterator`大于或等于*其他*;否则，**假**。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>矢量视图迭代器：：运算符* 运算符

递增当前 VectorViewIterator。

### <a name="syntax"></a>语法

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>返回值

第一个语法先递增然后返回当前 VectorViewIterator。 第二个语法返回当前 VectorViewIterator 的副本然后递增当前 VectorViewIterator。

### <a name="remarks"></a>备注

第一个 VectorViewIterator 语法预先递增当前 VectorViewIterator。

第二个语法后递增当前 VectorViewIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>矢量视图迭代器：：运算符！= 运算符

指示当前 VectorViewIterator 是否不等于指定的 VectorViewIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorViewIterator。

### <a name="return-value"></a>返回值

如果电流`VectorViewIterator`不等于*其他*，**则为 true;** 否则，**假**。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>矢量视图迭代器：：运算符&lt;运算符

指示当前 VectorIterator 是否小于指定的 VectorIterator。

### <a name="syntax"></a>语法

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一个 `VectorIterator`。

### <a name="return-value"></a>返回值

**如果**电流`VectorIterator`小于*其他*， 则为 true ;否则，**假**。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>矢量视图迭代器：：运算符&lt;= 运算符

指示电流`VectorIterator`是否小于或等于指定的`VectorIterator`。

### <a name="syntax"></a>语法

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一个 `VectorIterator`。

### <a name="return-value"></a>返回值

**如果**电流`VectorIterator`小于或等于*其他*;否则，**假**。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>矢量视图迭代器：：运算符 - 运算符

从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。

### <a name="syntax"></a>语法

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>参数

*n*<br/>
元素数目。

*其他*<br/>
另一 VectorViewIterator。

### <a name="return-value"></a>返回值

第一个运算符语法返回一个 VectorViewIterator 对象，该对象比当前 VectorViewIterator 少 `n` 个元素。 第二个运算符语法返回介于当前 VectorViewIterator 和 `other` VectorViewIterator 之间的元素数目。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>矢量视图迭代器：：运算符= 运算符

按指定偏移量递增当前 VectorViewIterator。

### <a name="syntax"></a>语法

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

更新的 VectorViewIterator。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>矢量视图迭代器：：运算符+ 运算符

返回引用偏移指定 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。

### <a name="syntax"></a>语法

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>参数

*T*<br/>
在第二个语法中，VectorViewIterator 的类型名称。

*n*<br/>
整数偏移。

*Ⅰ*<br/>
在第二个语法，一个 VectorViewIterator。

### <a name="return-value"></a>返回值

在第一个语法中，引用偏移当前 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。

在第二个语法中，引用偏移参数 `i` 开头指定偏移量处的元素的 VectorViewIterator。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>矢量视图迭代器：：运算符-= 运算符

按指定偏移量递减当前 VectorIterator。

### <a name="syntax"></a>语法

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

更新的 VectorIterator。

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>矢量视图迭代器：：运算符\[\]

检索对偏移当前 VectorViewIterator 指定量的元素的引用。

### <a name="syntax"></a>语法

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>参数

*n*<br/>
整数偏移。

### <a name="return-value"></a>返回值

`n` 元素从当前 VectorViewIterator 移置开的元素。

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>矢量视图迭代器：：矢量视图迭代器构造函数

初始化 VectorViewIterator 类的新实例。

### <a name="syntax"></a>语法

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>参数

*v*<br/>
iVectorView\<T>对象。

### <a name="remarks"></a>备注

第一个语法示例是默认构造函数。 第二个语法示例是显式构造函数，用于从 IVectorView\<T>对象构造 VectorViewIteror。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
