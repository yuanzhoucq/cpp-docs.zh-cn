---
title: Platform::Collections::VectorIterator 类
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354371"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 类

为从 Windows 运行时 IVector 接口派生的对象提供标准模板库迭代器。

矢量迭代器是存储矢量代理\<T>类型的元素的代理迭代器。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

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

|名称|说明|
|----------|-----------------|
|`difference_type`|指针差异 (ptrdiff_t)。|
|`iterator_category`|随机访问迭代器 (::std::random_access_iterator_tag) 的类别。|
|`pointer`|指向内部类型的指针，Platform：：集合：:D尾：：VectorProxy\<T>，这是实现 VectorItatateror 所必需的。|
|`reference`|对内部类型的引用，Platform：：集合：:D尾：：VectorProxy\<T>，这是实现 VectorItatererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererererer.|
|`value_type`|`T` 类型名称。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[矢量迭代器：矢量迭代器](#ctor)|初始化 VectorIterator 类的新实例。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[矢量迭代器：：运算符-运算符](#operator-minus)|从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。|
|[矢量迭代器：：运算符 -- 运算符](#operator-decrement)|递减当前 VectorIterator。|
|[矢量迭代器：：运算符！= 运算符](#operator-inequality)|指示当前 VectorIterator 是否不等于指定的 VectorIterator。|
|[矢量迭代器：：运算符* 运算符](#operator-dereference)|检索对当前 VectorIterator 指定的元素的引用。|
|[矢量迭代器：：运算符\[\]](#operator-at)|检索对属于当前 VectorIterator 的指定偏移量的元素的引用。|
|[矢量迭代器：：运算符+ 运算符](#operator-plus)|返回引用偏移指定 VectorIterator 指定偏移量处的元素的 VectorIterator。|
|[矢量迭代器：：运算符* 运算符](#operator-increment)|递增当前 VectorIterator。|
|[矢量迭代器：：运算符= 运算符](#operator-plus-assign)|按指定偏移量递增当前 VectorIterator。|
|[矢量迭代器：：运算符<运算符](#operator-less-than)|指示当前 VectorIterator 是否小于指定的 VectorIterator。|
|[矢量迭代器：：运算符\<= 运算符](#operator-less-than-or-equals)|指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。|
|[矢量迭代器：：运算符-= 运算符](#operator-minus-equals)|按指定偏移量递减当前 VectorIterator。|
|[矢量迭代器：：运算符 = 运算符](#operator-equality)|指示当前 VectorIterator 是否等于指定的 VectorIterator。|
|[VectorIterator::operator> 运算符](#operator-greater-than)|指示当前 VectorIterator 是否大于指定的 VectorIterator。|
|[矢量迭代器：：运算符->运算符](#operator-arrow)|检索当前 VectorIterator 引用的元素的地址。|
|[矢量迭代器：：运算符>= 运算符](#operator-greater-than-or-equals)|指示当前 VectorIterator 是否大于或等于指定的 VectorIterator。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`VectorIterator`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>矢量迭代器：：运算符-&gt;运算符

检索当前 VectorIterator 引用的元素的地址。

### <a name="syntax"></a>语法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>返回值

当前 VectorIterator 引用的元素的值。

返回值的类型是此运算符的实现所需的未指定内部类型。

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>矢量迭代器：：运算符 -- 运算符

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>矢量迭代器：：运算符\*

检索当前 VectorIterator 指定的元素的地址。

### <a name="syntax"></a>语法

```
reference operator*() const;
```

### <a name="return-value"></a>返回值

当前 VectorIterator 指定的元素。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>矢量迭代器：：运算符 = 运算符

指示当前 VectorIterator 是否等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

如果当前矢量迭代器等于*其他*，**则为 true** 。否则，**假**。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>矢量迭代器：：运算符&gt;

指示当前 VectorIterator 是否大于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

如果当前矢量迭代器大于*其他*，**则为 true** ;否则，**假**。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>矢量迭代器：：运算符&gt;= 运算符

指示当前 VectorIterator 是否大于或等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

如果当前矢量迭代器大于或等于*其他*，**则为 true;** 否则，**假**。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>矢量迭代器：：运算符* 运算符

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>矢量迭代器：：运算符！= 运算符

指示当前 VectorIterator 是否不等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

如果当前矢量迭代器不等于*其他*，**则为 true;** 否则，**假**。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>矢量迭代器：：运算符&lt;

指示当前 VectorIterator 是否小于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

**如果**当前矢量迭代器小于*其他*， 为 true ;否则，**假**。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>矢量迭代器：：运算符&lt;= 运算符

指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。

### <a name="syntax"></a>语法

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>参数

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

如果当前矢量迭代器小于或等于*其他*，**则为 true;** 否则，**假**。

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>矢量迭代器：：运算符-运算符

从当前迭代器中减去指定数目的元素以生成新迭代器，或者从当前迭代器中减去指定的迭代器以生成迭代器之间的元素数目。

### <a name="syntax"></a>语法

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>参数

*n*<br/>
元素数目。

*其他*<br/>
另一 VectorIterator。

### <a name="return-value"></a>返回值

第一个运算符语法返回一个 VectorIterator 对象，该对象比当前 VectorIterator 少 `n` 个元素。 第二个运算符语法返回介于当前 VectorIterator 和 `other` VectorIterator 之间的元素数目。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>矢量迭代器：：运算符= 运算符

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>矢量迭代器：：运算符+ 运算符

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

*Ⅰ*<br/>
在第二个语法，一个 VectorIterator。

### <a name="return-value"></a>返回值

在第一个语法中，引用偏移当前 VectorIterator 指定偏移量处的元素的 VectorIterator。

在第二个语法中，引用偏移参数 `i` 开头指定偏移量处的元素的 VectorIterator。

### <a name="remarks"></a>备注

第一个语法示例

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>矢量迭代器：：运算符-= 运算符

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

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>矢量迭代器：：运算符\[\]

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

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>矢量迭代器：矢量迭代器构造函数

初始化 VectorIterator 类的新实例。

### <a name="syntax"></a>语法

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>参数

*v*<br/>
IVector\<T>对象。

### <a name="remarks"></a>备注

第一个语法示例是默认构造函数。 第二个语法示例是显式构造函数，用于从 IVector\<T>对象构造 VectorIteror。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
