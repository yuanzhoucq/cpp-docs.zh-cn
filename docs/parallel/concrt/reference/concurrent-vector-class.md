---
title: concurrent_vector 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 9144fd0870bfb72e923a7271ffdd655e03a9bd57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215837"
---
# <a name="concurrent_vector-class"></a>concurrent_vector 类

`concurrent_vector` 类是允许对任意元素进行随机访问的序列容器类。 它支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

## <a name="syntax"></a>语法

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>参数

*T*<br/>
要存储在向量中的元素的数据类型。

*_Ax*<br/>
表示存储分配器对象的类型，该对象封装有关并发向量的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<T>`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`allocator_type`|一个类型，表示并发向量的分配器类。|
|`const_iterator`|一种类型，它提供可读取并发向量中的元素的随机访问迭代器 **`const`** 。|
|`const_pointer`|一种类型，它提供指向 **`const`** 并发向量中元素的指针。|
|`const_reference`|一种类型，它提供对 **`const`** 存储在并发向量中以读取和执行操作的元素的引用 **`const`** 。|
|`const_reverse_iterator`|一种类型，它提供可读取并发向量中的任何元素的随机访问迭代器 **`const`** 。|
|`difference_type`|一种类型，它提供并发向量中两个元素之间的有符号距离。|
|`iterator`|一种类型，它提供可读取并发向量中的任何元素的随机访问迭代器。 使用迭代器修改元素不是并发安全的。|
|`pointer`|一种类型，它提供指向并发向量中元素的指针。|
|`reference`|一种类型，该类型提供对并发向量中存储的元素的引用。|
|`reverse_iterator`|一种类型，它提供可读取反向并发向量中的任何元素的随机访问迭代器。 使用迭代器修改元素不是并发安全的。|
|`size_type`|一种类型，它对并发向量中的元素数进行计数。|
|`value_type`|一种类型，表示并发向量中存储的数据类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[concurrent_vector](#ctor)|已重载。 构造并发向量。|
|[~ concurrent_vector 析构函数](#dtor)|清除所有元素并销毁此并发向量。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[assign](#assign)|已重载。 清除并发向量的元素，并为其分配 `_N` 副本 `_Item` 或由迭代器范围 [，）指定的值 `_Begin` `_End` 。 此方法不是并发安全方法。|
|[at](#at)|已重载。 提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。|
|[返回](#back)|已重载。 返回对 **`const`** 并发向量中最后一个元素的引用或引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。|
|[准备](#begin)|已重载。 返回类型 `iterator` 或 `const_iterator` 并发向量开头的迭代器。 此方法是并发安全方法。|
|[功能](#capacity)|返回并发向量可以增长到的最大大小，无需分配更多内存。 此方法是并发安全方法。|
|[cbegin](#cbegin)|返回到并发向量开头的类型的迭代器 `const_iterator` 。 此方法是并发安全方法。|
|[cend](#cend)|返回对并发向量末尾的类型的迭代器 `const_iterator` 。 此方法是并发安全方法。|
|[清除](#clear)|清除并发向量中的所有元素。 此方法不是并发安全方法。|
|[crbegin](#crbegin)|返回到并发向量开头的类型的迭代器 `const_reverse_iterator` 。 此方法是并发安全方法。|
|[crend](#crend)|返回对并发向量末尾的类型的迭代器 `const_reverse_iterator` 。 此方法是并发安全方法。|
|[empty](#empty)|测试在调用此方法时并发向量是否为空。 此方法是并发安全方法。|
|[end](#end)|已重载。 返回类型 `iterator` 或 `const_iterator` 并发向量末尾的迭代器。 此方法是并发安全方法。|
|[主](#front)|已重载。 返回对 **`const`** 并发向量中第一个元素的引用或引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。|
|[get_allocator](#get_allocator)|返回用于构造并发向量的分配器副本。 此方法是并发安全方法。|
|[grow_by](#grow_by)|已重载。 按元素增长此并发向量 `_Delta` 。 此方法是并发安全方法。|
|[grow_to_at_least](#grow_to_at_least)|增大此并发向量，直到它至少具有 `_N` 元素。 此方法是并发安全方法。|
|[max_size](#max_size)|返回并发矢量可容纳的最大元素数。 此方法是并发安全方法。|
|[push_back](#push_back)|已重载。 将给定项追加到并发向量的末尾。 此方法是并发安全方法。|
|[rbegin](#rbegin)|已重载。 返回类型 `reverse_iterator` 或 `const_reverse_iterator` 并发向量开头的迭代器。 此方法是并发安全方法。|
|[rend](#rend)|已重载。 返回类型 `reverse_iterator` 或 `const_reverse_iterator` 并发向量末尾的迭代器。 此方法是并发安全方法。|
|[保留](#reserve)|分配足够的空间以将并发向量增长为大小， `_N` 而无需在以后分配更多内存。 此方法不是并发安全方法。|
|[调节](#resize)|已重载。 将并发向量的大小更改为所需大小，并根据需要删除或添加元素。 此方法不是并发安全方法。|
|[shrink_to_fit](#shrink_to_fit)|压缩并发向量的内部表示形式，以减少碎片并优化内存使用。 此方法不是并发安全方法。|
|[大小](#size)|返回并发向量中的元素数目。 此方法是并发安全方法。|
|[swap](#swap)|交换两个并发向量的内容。 此方法不是并发安全方法。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[操作员\[\]](#operator_at)|已重载。 提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。|
|[operator =](#operator_eq)|已重载。 将另一个对象的内容分配 `concurrent_vector` 给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关类的详细信息 `concurrent_vector` ，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>要求

**标头：** concurrent_vector。h

**命名空间：** 并发

## <a name="assign"></a><a name="assign"></a>将

清除并发向量的元素，并为其分配 `_N` 副本 `_Item` 或由迭代器范围 [，）指定的值 `_Begin` `_End` 。 此方法不是并发安全方法。

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>参数

*_InputIterator*<br/>
指定迭代器的类型。

*_N*<br/>
要复制到并发向量中的项数。

*_Item*<br/>
对用于填充并发向量的值的引用。

*_Begin*<br/>
源范围中第一个元素的迭代器。

*_End*<br/>
指向源范围最后一个元素之后的一个迭代器。

### <a name="remarks"></a>备注

`assign`不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。

## <a name="at"></a><a name="at"></a>最

提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>参数

*_Index*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

对给定索引处的项的引用。

### <a name="remarks"></a>备注

返回非引用的函数的版本 `at` **`const`** 不能用于同时从不同的线程写入元素。 应使用不同的同步对象将并发读写操作同步到相同的数据元素。

`out_of_range`如果 `_Index` 大于或等于并发向量的大小，并且 `range_error` 如果该索引为矢量的损坏部分，则会引发方法。 有关矢量如何中断的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="back"></a><a name="back"></a>返回

返回对 **`const`** 并发向量中最后一个元素的引用或引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>返回值

对 **`const`** 并发向量中最后一个元素的引用或引用。

## <a name="begin"></a><a name="begin"></a>准备

返回类型 `iterator` 或 `const_iterator` 并发向量开头的迭代器。 此方法是并发安全方法。

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

类型 `iterator` `const_iterator` 为或并发向量开头的迭代器。

## <a name="capacity"></a><a name="capacity"></a>功能

返回并发向量可以增长到的最大大小，无需分配更多内存。 此方法是并发安全方法。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>返回值

无需分配更多内存的情况下并发向量可增长到的最大大小。

### <a name="remarks"></a>备注

与 c + + 标准库不同 `vector` ， `concurrent_vector` 当对象分配更多内存时，它不会移动现有元素。

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

返回到并发向量开头的类型的迭代器 `const_iterator` 。 此方法是并发安全方法。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

并发向量开头的类型的迭代器 `const_iterator` 。

## <a name="cend"></a><a name="cend"></a>cend

返回对并发向量末尾的类型的迭代器 `const_iterator` 。 此方法是并发安全方法。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

并发向量末尾的类型的迭代器 `const_iterator` 。

## <a name="clear"></a><a name="clear"></a>清除

清除并发向量中的所有元素。 此方法不是并发安全方法。

```cpp
void clear();
```

### <a name="remarks"></a>备注

`clear`不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。 `clear`不释放内部数组。 若要释放内部数组，请 `shrink_to_fit` 在之后调用函数 `clear` 。

## <a name="concurrent_vector"></a><a name="ctor"></a>concurrent_vector

构造并发向量。

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>参数

*M*<br/>
源向量的分配器类型。

*_InputIterator*<br/>
输入迭代器的类型。

*_Al*<br/>
要用于此对象的分配器类。

*_Vector*<br/>
要从中复制或移动元素的源 `concurrent_vector` 对象。

*_N*<br/>
`concurrent_vector` 对象的初始容量。

*_Item*<br/>
构造的对象中的元素的值。

*_Begin*<br/>
要复制的元素范围内的第一个元素的位置。

*_End*<br/>
要复制的元素范围外的第一个元素的位置。

### <a name="remarks"></a>备注

所有构造函数都存储一个分配器对象 `_Al` 并初始化向量。

第一个构造函数指定一个空的初始向量，并显式指定分配器类型。 要使用的。

第二个和第三个构造函数指定并发向量的副本 `_Vector` 。

第四个构造函数指定并发向量 `_Vector` 的移动。

第五个构造函数指定类的默认值的指定数量（ `_N` ）元素的重复 `T` 。

第六个构造函数指定值的（ `_N` ）元素的重复 `_Item` 。

最后一个构造函数指定由迭代器范围 [，）提供的值 `_Begin` `_End` 。

## <a name="concurrent_vector"></a><a name="dtor"></a>~ concurrent_vector

清除所有元素并销毁此并发向量。

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a><a name="crbegin"></a>crbegin

返回到并发向量开头的类型的迭代器 `const_reverse_iterator` 。 此方法是并发安全方法。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

并发向量开头的类型的迭代器 `const_reverse_iterator` 。

## <a name="crend"></a><a name="crend"></a>crend

返回对并发向量末尾的类型的迭代器 `const_reverse_iterator` 。 此方法是并发安全方法。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

并发向量末尾的类型的迭代器 `const_reverse_iterator` 。

## <a name="empty"></a><a name="empty"></a>空白处

测试在调用此方法时并发向量是否为空。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果在调用函数时向量为空，则为 **`false`** ; 否则为。

## <a name="end"></a><a name="end"></a>端面

返回类型 `iterator` 或 `const_iterator` 并发向量末尾的迭代器。 此方法是并发安全方法。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

类型 `iterator` `const_iterator` 为或并发向量末尾的迭代器。

## <a name="front"></a><a name="front"></a>主

返回对 **`const`** 并发向量中第一个元素的引用或引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

对 **`const`** 并发向量中第一个元素的引用或引用。

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

返回用于构造并发向量的分配器副本。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造对象的分配器副本 `concurrent_vector` 。

## <a name="grow_by"></a><a name="grow_by"></a>grow_by

按元素增长此并发向量 `_Delta` 。 此方法是并发安全方法。

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>参数

*_Delta*<br/>
要追加到对象的元素的数目。

*_Item*<br/>
用于初始化新元素的值。

### <a name="return-value"></a>返回值

指向追加的第一项的迭代器。

### <a name="remarks"></a>备注

如果 `_Item` 未指定，则默认构造新元素。

## <a name="grow_to_at_least"></a><a name="grow_to_at_least"></a>grow_to_at_least

增大此并发向量，直到它至少具有 `_N` 元素。 此方法是并发安全方法。

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
对象的新的最小大小 `concurrent_vector` 。

### <a name="return-value"></a>返回值

指向追加序列的开头的迭代器， `_N` 如果未追加任何元素，则为索引处的元素。

## <a name="max_size"></a><a name="max_size"></a>max_size

返回并发矢量可容纳的最大元素数。 此方法是并发安全方法。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

对象可容纳的最大元素数 `concurrent_vector` 。

## <a name="operator"></a><a name="operator_eq"></a>operator =

将另一个对象的内容分配 `concurrent_vector` 给此对象。 此方法不是并发安全方法。

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>参数

*M*<br/>
源向量的分配器类型。

*_Vector*<br/>
源 `concurrent_vector` 对象。

### <a name="return-value"></a>返回值

对此对象的引用 `concurrent_vector` 。

## <a name="operator"></a><a name="operator_at"></a>运算符 []

提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>参数

*_Index*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

对给定索引处的项的引用。

### <a name="remarks"></a>备注

`operator []`返回非引用的的版本 **`const`** 不能用于同时从不同的线程写入元素。 应使用不同的同步对象将并发读写操作同步到相同的数据元素。

不执行边界检查来确保 `_Index` 是并发向量的有效索引。

## <a name="push_back"></a><a name="push_back"></a>push_back

将给定项追加到并发向量的末尾。 此方法是并发安全方法。

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>参数

*_Item*<br/>
要追加的值。

### <a name="return-value"></a>返回值

追加到项的迭代器。

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

返回类型 `reverse_iterator` 或 `const_reverse_iterator` 并发向量开头的迭代器。 此方法是并发安全方法。

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>返回值

类型 `reverse_iterator` `const_reverse_iterator` 为或并发向量开头的迭代器。

## <a name="rend"></a><a name="rend"></a>rend

返回类型 `reverse_iterator` 或 `const_reverse_iterator` 并发向量末尾的迭代器。 此方法是并发安全方法。

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>返回值

类型 `reverse_iterator` `const_reverse_iterator` 为或并发向量末尾的迭代器。

## <a name="reserve"></a><a name="reserve"></a>保留

分配足够的空间以将并发向量增长为大小， `_N` 而无需在以后分配更多内存。 此方法不是并发安全方法。

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
要为其保留空间的元素的数目。

### <a name="remarks"></a>备注

`reserve`不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。 在方法返回后，并发向量的容量可能大于请求的保留的容量。

## <a name="resize"></a><a name="resize"></a>调节

将并发向量的大小更改为所需大小，并根据需要删除或添加元素。 此方法不是并发安全方法。

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>参数

*_N*<br/>
并发向量的新大小。

*初始值*<br/>
新的大小大于原始大小时添加至向量的新元素的值。 如果省略此值，则会为新对象分配其类型的默认值。

### <a name="remarks"></a>备注

如果容器的大小小于请求的大小，则会将元素添加到向量，直到它达到请求的大小。 如果容器的大小大于请求的大小，则会删除最接近容器末尾的元素，直到该容器达到大小 `_N` 。 如果容器的当前大小与请求的大小相同，则不采取任何操作。

`resize`不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a>shrink_to_fit

压缩并发向量的内部表示形式，以减少碎片并优化内存使用。 此方法不是并发安全方法。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>备注

此方法将在内部重新分配内存移动元素，从而使所有迭代器失效。 `shrink_to_fit`不是并发安全的。 调用此函数时，必须确保没有其他线程在并发向量上调用方法。

## <a name="size"></a><a name="size"></a>规格

返回并发向量中的元素数目。 此方法是并发安全方法。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

此对象中的元素数 `concurrent_vector` 。

### <a name="remarks"></a>备注

返回的大小保证包含通过调用函数追加的所有元素 `push_back` ，或者在调用此方法之前已完成的增长操作。 但是，它还可能包括通过对任何增长方法的并发调用来分配但仍在构造中的元素。

## <a name="swap"></a><a name="swap"></a>购

交换两个并发向量的内容。 此方法不是并发安全方法。

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>参数

*_Vector*<br/>
要与其交换内容的 `concurrent_vector` 对象。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)
