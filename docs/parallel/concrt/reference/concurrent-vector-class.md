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
ms.openlocfilehash: 002f1e3f691de3315810efed8f7d8f6c547cf653
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143138"
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

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`allocator_type`|一个类型，表示并发向量的分配器类。|
|`const_iterator`|一种类型，它提供可读取并发向量中的 `const` 元素的随机访问迭代器。|
|`const_pointer`|一种类型，它提供指向并发向量中的 `const` 元素的指针。|
|`const_reference`|一种类型，该类型提供对存储在并发向量中的 `const` 元素的引用，以便读取和执行 `const` 操作。|
|`const_reverse_iterator`|一种类型，它提供可读取并发向量中任何 `const` 元素的随机访问迭代器。|
|`difference_type`|一种类型，它提供并发向量中两个元素之间的有符号距离。|
|`iterator`|一种类型，它提供可读取并发向量中的任何元素的随机访问迭代器。 使用迭代器修改元素不是并发安全的。|
|`pointer`|一种类型，它提供指向并发向量中元素的指针。|
|`reference`|一种类型，该类型提供对并发向量中存储的元素的引用。|
|`reverse_iterator`|一种类型，它提供可读取反向并发向量中的任何元素的随机访问迭代器。 使用迭代器修改元素不是并发安全的。|
|`size_type`|一种类型，它对并发向量中的元素数进行计数。|
|`value_type`|一种类型，表示并发向量中存储的数据类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[concurrent_vector](#ctor)|已重载。 构造并发向量。|
|[~ concurrent_vector 析构函数](#dtor)|清除所有元素并销毁此并发向量。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[assign](#assign)|已重载。 清除并发向量的元素，并为其分配 `_N` `_Item`副本或迭代器范围 [`_Begin`，`_End`）指定的值。 此方法不是并发安全方法。|
|[at](#at)|已重载。 提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。|
|[back](#back)|已重载。 返回对并发向量中最后一个元素的引用或 `const` 引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。|
|[begin](#begin)|已重载。 返回 `iterator` 或 `const_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。|
|[capacity](#capacity)|返回并发向量可以增长到的最大大小，无需分配更多内存。 此方法是并发安全方法。|
|[cbegin](#cbegin)|返回 `const_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。|
|[cend](#cend)|返回 `const_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。|
|[clear](#clear)|清除并发向量中的所有元素。 此方法不是并发安全方法。|
|[crbegin](#crbegin)|返回 `const_reverse_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。|
|[crend](#crend)|返回 `const_reverse_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。|
|[empty](#empty)|测试在调用此方法时并发向量是否为空。 此方法是并发安全方法。|
|[end](#end)|已重载。 返回 `iterator` 或 `const_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。|
|[front](#front)|已重载。 返回对并发向量中第一个元素的引用或 `const` 引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。|
|[get_allocator](#get_allocator)|返回用于构造并发向量的分配器副本。 此方法是并发安全方法。|
|[grow_by](#grow_by)|已重载。 通过 `_Delta` 元素增长此并发向量。 此方法是并发安全方法。|
|[grow_to_at_least](#grow_to_at_least)|增大此并发向量，直到它至少具有 `_N` 元素。 此方法是并发安全方法。|
|[max_size](#max_size)|返回并发矢量可容纳的最大元素数。 此方法是并发安全方法。|
|[push_back](#push_back)|已重载。 将给定项追加到并发向量的末尾。 此方法是并发安全方法。|
|[rbegin](#rbegin)|已重载。 返回 `reverse_iterator` 或 `const_reverse_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。|
|[rend](#rend)|已重载。 返回 `reverse_iterator` 或 `const_reverse_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。|
|[reserve](#reserve)|分配足够的空间以将并发向量增长到 `_N` 大小，而无需在以后分配更多内存。 此方法不是并发安全方法。|
|[resize](#resize)|已重载。 将并发向量的大小更改为所需大小，并根据需要删除或添加元素。 此方法不是并发安全方法。|
|[shrink_to_fit](#shrink_to_fit)|压缩并发向量的内部表示形式，以减少碎片并优化内存使用。 此方法不是并发安全方法。|
|[size](#size)|返回并发向量中的元素数目。 此方法是并发安全方法。|
|[swap](#swap)|交换两个并发向量的内容。 此方法不是并发安全方法。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator\[\]](#operator_at)|已重载。 提供对并发向量中给定索引处的元素的访问。 对于读取操作，此方法是并发安全的，而且在增大向量时也是如此，前提是已确保该值 `_Index` 小于并发向量的大小。|
|[operator=](#operator_eq)|已重载。 将另一个 `concurrent_vector` 对象的内容分配给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关 `concurrent_vector` 类的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>要求

**标头：** concurrent_vector。h

**命名空间：** 并发

## <a name="assign"></a>将

清除并发向量的元素，并为其分配 `_N` `_Item`副本或迭代器范围 [`_Begin`，`_End`）指定的值。 此方法不是并发安全方法。

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

`assign` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。

## <a name="at"></a>最

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

返回非 `const` 引用的函数 `at` 的版本不能用于从不同线程同时写入元素。 应使用不同的同步对象将并发读写操作同步到相同的数据元素。

如果 `_Index` 大于或等于并发向量的大小，则方法会引发 `out_of_range`; 如果索引用于矢量的损坏部分，则会引发 `range_error`。 有关矢量如何中断的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="back"></a>返回

返回对并发向量中最后一个元素的引用或 `const` 引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>返回值

对并发向量中最后一个元素的引用或 `const` 引用。

## <a name="begin"></a>准备

返回 `iterator` 或 `const_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

`iterator` 或 `const_iterator` 到并发向量开头的类型的迭代器。

## <a name="capacity"></a>功能

返回并发向量可以增长到的最大大小，无需分配更多内存。 此方法是并发安全方法。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>返回值

无需分配更多内存的情况下并发向量可增长到的最大大小。

### <a name="remarks"></a>备注

与C++标准库 `vector`不同的是，如果 `concurrent_vector` 对象分配更多内存，则不会移动现有元素。

## <a name="cbegin"></a>cbegin

返回 `const_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

`const_iterator` 到并发向量开头的类型的迭代器。

## <a name="cend"></a>cend

返回 `const_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

`const_iterator` 到并发向量末尾的类型的迭代器。

## <a name="clear"></a>清除

清除并发向量中的所有元素。 此方法不是并发安全方法。

```cpp
void clear();
```

### <a name="remarks"></a>备注

`clear` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。 `clear` 不会释放内部数组。 若要释放内部数组，请在 `clear`之后调用函数 `shrink_to_fit`。

## <a name="ctor"></a>concurrent_vector

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

所有构造函数都存储一个分配器对象 `_Al` 并初始化该向量。

第一个构造函数指定一个空的初始向量，并显式指定分配器类型。 要使用的。

第二个和第三个构造函数指定并发向量 `_Vector`的副本。

第四个构造函数指定并发向量 `_Vector` 的移动。

第五个构造函数指定类 `T`的默认值的元素的指定数目（`_N`）重复。

第六个构造函数指定值 `_Item`的（`_N`）元素的重复。

最后一个构造函数指定迭代器范围 [`_Begin`，`_End`）提供的值。

## <a name="dtor"></a>~ concurrent_vector

清除所有元素并销毁此并发向量。

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a>crbegin

返回 `const_reverse_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

`const_reverse_iterator` 到并发向量开头的类型的迭代器。

## <a name="crend"></a>crend

返回 `const_reverse_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

`const_reverse_iterator` 到并发向量末尾的类型的迭代器。

## <a name="empty"></a>空白处

测试在调用此方法时并发向量是否为空。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果在调用函数时向量为空，**则为 true** ; 否则为**false** 。

## <a name="end"></a>端面

返回 `iterator` 或 `const_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

`iterator` 或 `const_iterator` 到并发向量末尾的类型的迭代器。

## <a name="front"></a>主

返回对并发向量中第一个元素的引用或 `const` 引用。 如果并发向量为空，则返回值为 undefined。 此方法是并发安全方法。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

对并发向量中第一个元素的引用或 `const` 引用。

## <a name="get_allocator"></a>get_allocator

返回用于构造并发向量的分配器副本。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造 `concurrent_vector` 对象的分配器副本。

## <a name="grow_by"></a>grow_by

通过 `_Delta` 元素增长此并发向量。 此方法是并发安全方法。

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

如果未指定 `_Item`，则默认构造新元素。

## <a name="grow_to_at_least"></a>grow_to_at_least

增大此并发向量，直到它至少具有 `_N` 元素。 此方法是并发安全方法。

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
`concurrent_vector` 对象的新的最小大小。

### <a name="return-value"></a>返回值

一个迭代器，它指向追加序列的开头，如果未追加任何元素，则为索引 `_N` 的元素。

## <a name="max_size"></a>max_size

返回并发矢量可容纳的最大元素数。 此方法是并发安全方法。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

`concurrent_vector` 对象可以容纳的最大元素数。

## <a name="operator_eq"></a>operator =

将另一个 `concurrent_vector` 对象的内容分配给此对象。 此方法不是并发安全方法。

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

对此 `concurrent_vector` 对象的引用。

## <a name="operator_at"></a>运算符 []

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

返回非 `const` 引用的 `operator []` 的版本不能用于从不同线程并发写入元素。 应使用不同的同步对象将并发读写操作同步到相同的数据元素。

不执行边界检查来确保 `_Index` 是并发向量的有效索引。

## <a name="push_back"></a>push_back

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

## <a name="rbegin"></a>rbegin

返回 `reverse_iterator` 或 `const_reverse_iterator` 到并发向量开头的类型的迭代器。 此方法是并发安全方法。

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>返回值

`reverse_iterator` 或 `const_reverse_iterator` 到并发向量开头的类型的迭代器。

## <a name="rend"></a>rend

返回 `reverse_iterator` 或 `const_reverse_iterator` 到并发向量末尾的类型的迭代器。 此方法是并发安全方法。

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>返回值

`reverse_iterator` 或 `const_reverse_iterator` 到并发向量末尾的类型的迭代器。

## <a name="reserve"></a>保留

分配足够的空间以将并发向量增长到 `_N` 大小，而无需在以后分配更多内存。 此方法不是并发安全方法。

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
要为其保留空间的元素的数目。

### <a name="remarks"></a>备注

`reserve` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。 在方法返回后，并发向量的容量可能大于请求的保留的容量。

## <a name="resize"></a>调节

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

*val*<br/>
新的大小大于原始大小时添加至向量的新元素的值。 如果省略此值，则会为新对象分配其类型的默认值。

### <a name="remarks"></a>备注

如果容器的大小小于请求的大小，则会将元素添加到向量，直到它达到请求的大小。 如果容器的大小大于请求的大小，则会删除最靠近容器末尾的元素，直到容器达到 `_N`大小。 如果容器的当前大小与请求的大小相同，则不采取任何操作。

`resize` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发向量上调用方法。

## <a name="shrink_to_fit"></a>shrink_to_fit

压缩并发向量的内部表示形式，以减少碎片并优化内存使用。 此方法不是并发安全方法。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>备注

此方法将在内部重新分配内存移动元素，从而使所有迭代器失效。 `shrink_to_fit` 不是并发安全的。 调用此函数时，必须确保没有其他线程在并发向量上调用方法。

## <a name="size"></a>规格

返回并发向量中的元素数目。 此方法是并发安全方法。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

此 `concurrent_vector` 对象中的元素数。

### <a name="remarks"></a>备注

返回的大小保证包含通过调用函数追加的所有元素 `push_back`或在调用此方法之前已完成的增长操作。 但是，它还可能包括通过对任何增长方法的并发调用来分配但仍在构造中的元素。

## <a name="swap"></a>购

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
