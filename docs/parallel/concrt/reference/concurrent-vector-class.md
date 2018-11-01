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
ms.openlocfilehash: 367a5ed6bf9d42730a309570c93afd1b315bae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501746"
---
# <a name="concurrentvector-class"></a>concurrent_vector 类

`concurrent_vector` 类是允许对任意元素进行随机访问的序列容器类。 它支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作。

## <a name="syntax"></a>语法

```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在向量中的元素数据类型。

*_Ax*<br/>
表示存储的分配器对象封装有关分配和解除分配的并发向量内存的详细信息的类型。 此参数为可选参数，默认值为 `allocator<T>`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`allocator_type`|表示并发向量的分配器类的类型。|
|`const_iterator`|一个类型，提供的随机访问迭代器可读取`const`并发向量中的元素。|
|`const_pointer`|提供一个指针指向的类型`const`并发向量中的元素。|
|`const_reference`|提供对引用的类型`const`存储在用于读取和执行并发向量中元素`const`操作。|
|`const_reverse_iterator`|一个类型，提供的随机访问迭代器可读取任何`const`并发向量中的元素。|
|`difference_type`|提供并发向量中的两个元素之间的有符号的距离的类型。|
|`iterator`|提供可读取并发向量中的任何元素的随机访问迭代器的类型。 使用迭代器对元素的修改不是并发安全的。|
|`pointer`|提供指向并发向量中元素的类型。|
|`reference`|提供对存储在并发向量的元素的引用的类型。|
|`reverse_iterator`|提供可读取并发反向矢量中的任何元素的随机访问迭代器的类型。 使用迭代器对元素的修改不是并发安全的。|
|`size_type`|一种计算并发向量中的元素数目的类型。|
|`value_type`|表示并发向量中存储的数据类型的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[concurrent_vector](#ctor)|已重载。 构造并发向量。|
|[~ concurrent_vector 析构函数](#dtor)|清除所有元素，并销毁此并发向量。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[assign](#assign)|已重载。 清除并发向量的元素，并为其分配`_N`的副本`_Item`，或指定的迭代器范围的值 [ `_Begin`， `_End`)。 此方法不是并发安全的。|
|[at](#at)|已重载。 提供对并发向量中的给定索引处的元素的访问。 此方法是并发安全方法对于读取操作，并且还增加矢量，只要你确保值`_Index`小于并发向量的大小。|
|[back](#back)|已重载。 返回的引用或`const`到最后一个引用并发向量中的元素。 如果并发向量为空，则返回值未定义。 此方法是并发安全的。|
|[begin](#begin)|已重载。 返回一个迭代器的类型`iterator`或`const_iterator`并发向量的开头。 此方法是并发安全的。|
|[capacity](#capacity)|返回到的并发向量可增长而无需分配更多内存的最大大小。 此方法是并发安全的。|
|[cbegin](#cbegin)|返回一个迭代器类型的`const_iterator`并发向量的开头。 此方法是并发安全的。|
|[cend](#cend)|返回一个迭代器类型的`const_iterator`到并发向量末尾。 此方法是并发安全的。|
|[clear](#clear)|清除并发向量中的所有元素。 此方法不是并发安全的。|
|[crbegin](#crbegin)|返回一个迭代器类型的`const_reverse_iterator`并发向量的开头。 此方法是并发安全的。|
|[crend](#crend)|返回一个迭代器类型的`const_reverse_iterator`到并发向量末尾。 此方法是并发安全的。|
|[empty](#empty)|测试是否并发向量为空时调用此方法。 此方法是并发安全的。|
|[end](#end)|已重载。 返回一个迭代器的类型`iterator`或`const_iterator`到并发向量末尾。 此方法是并发安全的。|
|[front](#front)|已重载。 返回的引用或`const`并发向量中第一个元素的引用。 如果并发向量为空，则返回值未定义。 此方法是并发安全的。|
|[get_allocator](#get_allocator)|返回用于构造并发向量的分配器的副本。 此方法是并发安全的。|
|[grow_by](#grow_by)|已重载。 增大此并发向量通过`_Delta`元素。 此方法是并发安全的。|
|[grow_to_at_least](#grow_to_at_least)|增大此并发向量，直到它至少具有`_N`元素。 此方法是并发安全的。|
|[max_size](#max_size)|返回的最大并发向量可容纳的元素数。 此方法是并发安全的。|
|[push_back](#push_back)|已重载。 将给定的项追加到并发向量末尾。 此方法是并发安全的。|
|[rbegin](#rbegin)|已重载。 返回一个迭代器的类型`reverse_iterator`或`const_reverse_iterator`并发向量的开头。 此方法是并发安全的。|
|[rend](#rend)|已重载。 返回一个迭代器的类型`reverse_iterator`或`const_reverse_iterator`到并发向量末尾。 此方法是并发安全的。|
|[reserve](#reserve)|分配足够的空间来增长到大小的并发向量`_N`而无需分配更多的内存更高版本。 此方法不是并发安全的。|
|[resize](#resize)|已重载。 并发向量的大小更改为所请求的大小，删除或根据需要添加元素。 此方法不是并发安全的。|
|[shrink_to_fit](#shrink_to_fit)|将压缩要减少碎片并优化内存使用的并发向量的内部表示形式。 此方法不是并发安全的。|
|[size](#size)|返回在并发向量中的元素数。 此方法是并发安全的。|
|[swap](#swap)|交换两个并发向量的内容。 此方法不是并发安全的。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator[]](#operator_at)|已重载。 提供对并发向量中的给定索引处的元素的访问。 此方法是并发安全方法对于读取操作，并且还增加矢量，只要你确保值`_Index`小于并发向量的大小。|
|[operator=](#operator_eq)|已重载。 另一种内容分配`concurrent_vector`到此对象。 此方法不是并发安全的。|

## <a name="remarks"></a>备注

有关详细信息`concurrent_vector`类，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>要求

**标头：** concurrent_vector.h

**命名空间：** 并发

##  <a name="assign"></a> 分配

清除并发向量的元素，并为其分配`_N`的副本`_Item`，或指定的迭代器范围的值 [ `_Begin`， `_End`)。 此方法不是并发安全的。

```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>参数

*_InputIterator*<br/>
指定的迭代器的类型。

*_N*<br/>
要复制到此并发向量的项目数。

*项目 （_i)*<br/>
对用来填充并发向量值的引用。

*（_b)*<br/>
指向源范围的第一个元素的迭代器。

*（_e)*<br/>
指向一个源范围的最后一个元素之后的迭代器。

### <a name="remarks"></a>备注

`assign` 不是并发安全的。 您必须确保没有其他线程在调用此方法时所调用的并发向量中的方法。

##  <a name="at"></a> 在

提供对并发向量中的给定索引处的元素的访问。 此方法是并发安全方法对于读取操作，并且还增加矢量，只要你确保值`_Index`小于并发向量的大小。

```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>参数

*_Index*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

对给定索引处的项的引用。

### <a name="remarks"></a>备注

该函数的版本`at`，它返回一个非`const`引用不能用于并发地写入来自不同线程的元素。 应使用不同的同步对象来同步并发读取和写入到相同的数据元素的操作。

该方法将引发`out_of_range`如果`_Index`大于或等于并发向量的大小和`range_error`如果索引不中断向量的一部分。 有关如何一个向量，可能会中断的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

##  <a name="back"></a> 返回

返回的引用或`const`到最后一个引用并发向量中的元素。 如果并发向量为空，则返回值未定义。 此方法是并发安全的。

```
reference back();

const_reference back() const;
```

### <a name="return-value"></a>返回值

引用或`const`到最后一个引用并发向量中的元素。

##  <a name="begin"></a> 开始

返回一个迭代器的类型`iterator`或`const_iterator`并发向量的开头。 此方法是并发安全的。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`iterator`或`const_iterator`并发向量的开头。

##  <a name="capacity"></a> 容量

返回到的并发向量可增长而无需分配更多内存的最大大小。 此方法是并发安全的。

```
size_type capacity() const;
```

### <a name="return-value"></a>返回值

无需分配更多内存的情况下并发向量可增长到的最大大小。

### <a name="remarks"></a>备注

与 c + + 标准库不同`vector`、`concurrent_vector`对象不会移动现有元素，前提是它分配更多的内存。

##  <a name="cbegin"></a> cbegin

返回一个迭代器类型的`const_iterator`并发向量的开头。 此方法是并发安全的。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`const_iterator`并发向量的开头。

##  <a name="cend"></a> cend

返回一个迭代器类型的`const_iterator`到并发向量末尾。 此方法是并发安全的。

```
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`const_iterator`到并发向量末尾。

##  <a name="clear"></a> 清除

清除并发向量中的所有元素。 此方法不是并发安全的。

```
void clear();
```

### <a name="remarks"></a>备注

`clear` 不是并发安全的。 您必须确保没有其他线程在调用此方法时所调用的并发向量中的方法。 `clear` 不会释放内部数组。 若要释放内部数组，调用函数`shrink_to_fit`后`clear`。

##  <a name="ctor"></a> concurrent_vector

构造并发向量。

```
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

*项目 （_i)*<br/>
构造的对象中的元素的值。

*（_b)*<br/>
要复制的元素范围内的第一个元素的位置。

*（_e)*<br/>
要复制的元素范围外的第一个元素的位置。

### <a name="remarks"></a>备注

所有构造函数存储一个分配器对象`_Al`并初始化此矢量。

第一个构造函数指定一个空初始矢量，并显式指定的分配器类型。 若要使用。

第二个和第三个构造函数指定并发向量的副本`_Vector`。

第四个构造函数指定并发向量 `_Vector` 的移动。

第五个构造函数指定指定数目的重复项 ( `_N`) 的类的默认值的元素`T`。

第六个构造函数指定的重复项 ( `_N`) 值的元素`_Item`。

最后一个构造函数指定值提供的迭代器范围 [ `_Begin`， `_End`)。

##  <a name="dtor"></a> ~concurrent_vector

清除所有元素，并销毁此并发向量。

```
~concurrent_vector();
```

##  <a name="crbegin"></a> crbegin

返回一个迭代器类型的`const_reverse_iterator`并发向量的开头。 此方法是并发安全的。

```
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`const_reverse_iterator`并发向量的开头。

##  <a name="crend"></a> crend

返回一个迭代器类型的`const_reverse_iterator`到并发向量末尾。 此方法是并发安全的。

```
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`const_reverse_iterator`到并发向量末尾。

##  <a name="empty"></a> 为空

测试是否并发向量为空时调用此方法。 此方法是并发安全的。

```
bool empty() const;
```

### <a name="return-value"></a>返回值

**true**如果向量为空时调用的函数，此时**false**否则为。

##  <a name="end"></a> 结束

返回一个迭代器的类型`iterator`或`const_iterator`到并发向量末尾。 此方法是并发安全的。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`iterator`或`const_iterator`到并发向量末尾。

##  <a name="front"></a> 前端

返回的引用或`const`并发向量中第一个元素的引用。 如果并发向量为空，则返回值未定义。 此方法是并发安全的。

```
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

引用或`const`并发向量中第一个元素的引用。

##  <a name="get_allocator"></a> get_allocator

返回用于构造并发向量的分配器的副本。 此方法是并发安全的。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造的分配器的副本`concurrent_vector`对象。

##  <a name="grow_by"></a> grow_by

增大此并发向量通过`_Delta`元素。 此方法是并发安全的。

```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>参数

*_Delta*<br/>
要追加到对象的元素数。

*项目 （_i)*<br/>
要初始化新元素的值。

### <a name="return-value"></a>返回值

追加到第一项的迭代器。

### <a name="remarks"></a>备注

如果`_Item`未指定，则为默认构造的新元素。

##  <a name="grow_to_at_least"></a> grow_to_at_least

增大此并发向量，直到它至少具有`_N`元素。 此方法是并发安全的。

```
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
新的最小大小为`concurrent_vector`对象。

### <a name="return-value"></a>返回值

指向追加序列的开头或索引处的元素的迭代器`_N`如果未追加元素。

##  <a name="max_size"></a> max_size

返回的最大并发向量可容纳的元素数。 此方法是并发安全的。

```
size_type max_size() const;
```

### <a name="return-value"></a>返回值

最大元素数`concurrent_vector`对象可以保存。

##  <a name="operator_eq"></a> 运算符 =

另一种内容分配`concurrent_vector`到此对象。 此方法不是并发安全的。

```
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

对此引用`concurrent_vector`对象。

##  <a name="operator_at"></a> operator]

提供对并发向量中的给定索引处的元素的访问。 此方法是并发安全方法对于读取操作，并且还增加矢量，只要你确保值`_Index`小于并发向量的大小。

```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>参数

*_Index*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

对给定索引处的项的引用。

### <a name="remarks"></a>备注

版本`operator []`，它返回一个非`const`引用不能用于并发地写入来自不同线程的元素。 应使用不同的同步对象来同步并发读取和写入到相同的数据元素的操作。

无边界检查执行，确保`_Index`是到此并发向量的有效索引。

##  <a name="push_back"></a> push_back

将给定的项追加到并发向量末尾。 此方法是并发安全的。

```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>参数

*项目 （_i)*<br/>
要追加的值。

### <a name="return-value"></a>返回值

追加到项的迭代器。

##  <a name="rbegin"></a> rbegin

返回一个迭代器的类型`reverse_iterator`或`const_reverse_iterator`并发向量的开头。 此方法是并发安全的。

```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`reverse_iterator`或`const_reverse_iterator`并发向量的开头。

##  <a name="rend"></a> rend

返回一个迭代器的类型`reverse_iterator`或`const_reverse_iterator`到并发向量末尾。 此方法是并发安全的。

```
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>返回值

类型的迭代器`reverse_iterator`或`const_reverse_iterator`到并发向量末尾。

##  <a name="reserve"></a> 保留

分配足够的空间来增长到大小的并发向量`_N`而无需分配更多的内存更高版本。 此方法不是并发安全的。

```
void reserve(size_type _N);
```

### <a name="parameters"></a>参数

*_N*<br/>
要保留的空间的元素数。

### <a name="remarks"></a>备注

`reserve` 不是并发安全的。 您必须确保没有其他线程在调用此方法时所调用的并发向量中的方法。 在方法返回之后的并发向量的容量可能大于请求的保留。

##  <a name="resize"></a> 重设大小

并发向量的大小更改为所请求的大小，删除或根据需要添加元素。 此方法不是并发安全的。

```
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
新的大小大于原始大小时添加至向量的新元素的值。 如果省略值，则新对象分配的默认值为它们的类型。

### <a name="remarks"></a>备注

如果容器的大小小于请求的大小，元素将添加到向量，直到它达到请求的大小。 如果容器的大小大于请求的大小，最接近容器末尾元素将被删除之前该容器达到大小`_N`。 如果容器的当前大小与请求的大小相同，则不采取任何操作。

`resize` 不是并发安全的。 您必须确保没有其他线程在调用此方法时所调用的并发向量中的方法。

##  <a name="shrink_to_fit"></a> shrink_to_fit

将压缩要减少碎片并优化内存使用的并发向量的内部表示形式。 此方法不是并发安全的。

```
void shrink_to_fit();
```

### <a name="remarks"></a>备注

此方法将在内部重新分配内存四处移动元素，使所有迭代器失效。 `shrink_to_fit` 不是并发安全的。 您必须确保没有其他线程在调用此函数时所调用的并发向量中的方法。

##  <a name="size"></a> 大小

返回在并发向量中的元素数。 此方法是并发安全的。

```
size_type size() const;
```

### <a name="return-value"></a>返回值

在此元素的数目`concurrent_vector`对象。

### <a name="remarks"></a>备注

保证返回的大小将追加到该函数调用的所有元素都包含`push_back`，或增大调用此方法之前已完成的操作。 但是，它还可能包括分配的元素，但仍在通过对任何的增长方法的并发调用的构造。

##  <a name="swap"></a> 交换

交换两个并发向量的内容。 此方法不是并发安全的。

```
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>参数

*_Vector*<br/>
`concurrent_vector`对象要与其交换内容。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)

