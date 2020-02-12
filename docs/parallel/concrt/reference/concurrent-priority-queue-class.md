---
title: concurrent_priority_queue 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143221"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue 类

`concurrent_priority_queue` 类是允许多个线程并发推送和弹出项的容器。 项按优先级顺序弹出，其中优先级由作为模板参数提供的涵子确定。

## <a name="syntax"></a>语法

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>参数

*T*<br/>
要存储在优先级队列中的元素的数据类型。

*_Compare*<br/>
可将两个元素的值作为排序键进行比较以确定其在优先级队列中相对顺序的函数对象的类型。 此参数为可选自变量，默认值是二元谓词 `less<T>`。

*_Ax*<br/>
一种表示存储的分配器对象的类型，该分配器对象封装有关并发优先级队列的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<T>`。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`allocator_type`|一种表示适用于并发优先级队列的分配器类的类型。|
|`const_reference`|一种表示存储在并发优先级队列中类型的一个元素的常量引用的类型。|
|`reference`|一种表示存储在并发优先级队列中类型的一个元素的引用的类型。|
|`size_type`|一种计算并发优先级队列中元素数量的类型。|
|`value_type`|一种表示存储在并发优先级队列中的数据类型的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|已重载。 构造并发优先级队列。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[clear](#clear)|清除并发优先级中的所有元素。 此方法不是并发安全方法。|
|[empty](#empty)|测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全方法。|
|[get_allocator](#get_allocator)|返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全方法。|
|[push](#push)|已重载。 在并发优先级队列中添加一个元素。 此方法是并发安全方法。|
|[size](#size)|返回并发优先级队列中元素的数量。 此方法是并发安全方法。|
|[swap](#swap)|交换两个并发优先级队列中的内容。 此方法不是并发安全方法。|
|[try_pop](#try_pop)|如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全方法。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator=](#operator_eq)|已重载。 将另一个 `concurrent_priority_queue` 对象的内容分配给此对象。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关 `concurrent_priority_queue` 类的详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`concurrent_priority_queue`

## <a name="requirements"></a>要求

**标头：** concurrent_priority_queue。h

**命名空间：** 并发

## <a name="clear"></a>清除

清除并发优先级中的所有元素。 此方法不是并发安全方法。

```cpp
void clear();
```

### <a name="remarks"></a>备注

`clear` 不是并发安全的。 调用此方法时，必须确保没有其他线程在并发优先级队列中调用方法。 `clear` 不能释放内存。

## <a name="ctor"></a>concurrent_priority_queue

构造并发优先级队列。

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>参数

*_InputIterator*<br/>
输入迭代器的类型。

*_Al*<br/>
要用于此对象的分配器类。

*_Init_capacity*<br/>
`concurrent_priority_queue` 对象的初始容量。

*_Begin*<br/>
要复制的范围元素中的第一个元素的位置。

*_End*<br/>
要复制的元素范围以外的第一个元素的位置。

*_Src*<br/>
要从中复制或移动元素的源 `concurrent_priority_queue` 对象。

### <a name="remarks"></a>备注

所有构造函数都存储一个分配器对象 `_Al` 并初始化优先级队列。

第一个构造函数指定一个空的初始优先级队列，并根据需要指定分配器。

第二个构造函数指定具有初始容量 `_Init_capacity` 的优先级队列，并根据需要指定分配器。

第三个构造函数指定迭代器范围 [`_Begin`，`_End`）提供的值，并根据需要指定分配器。

第四个和第五个构造函数指定优先级队列 `_Src`的副本。

第六个和第七个构造函数指定 `_Src`的优先级队列移动。

## <a name="empty"></a>空白处

测试在调用此方法时并发优先级队列是否为空。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果在调用函数时优先级队列为空，**则为 true** ; 否则为**false** 。

## <a name="get_allocator"></a>get_allocator

返回用于构造并发优先级队列的分配器的副本。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造 `concurrent_priority_queue` 对象的分配器副本。

## <a name="operator_eq"></a>operator =

将另一个 `concurrent_priority_queue` 对象的内容分配给此对象。 此方法不是并发安全方法。

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
源 `concurrent_priority_queue` 对象。

### <a name="return-value"></a>返回值

对此 `concurrent_priority_queue` 对象的引用。

## <a name="push"></a>请求

在并发优先级队列中添加一个元素。 此方法是并发安全方法。

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>参数

*_Elem*<br/>
要添加到并发优先级队列中的元素。

## <a name="size"></a>规格

返回并发优先级队列中元素的数量。 此方法是并发安全方法。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

此 `concurrent_priority_queue` 对象中的元素数。

### <a name="remarks"></a>备注

返回的大小保证包含通过调用函数添加的所有元素 `push`。 但是，它可能不会反映挂起的并发操作的结果。

## <a name="swap"></a>购

交换两个并发优先级队列中的内容。 此方法不是并发安全方法。

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>参数

*_Queue*<br/>
要与其交换内容的 `concurrent_priority_queue` 对象。

## <a name="try_pop"></a>try_pop

如果队列非空，移除并返回队列中优先级最高的元素。 此方法是并发安全方法。

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>参数

*_Elem*<br/>
如果队列非空，则为将使用最高优先级元素填充的变量的引用。

### <a name="return-value"></a>返回值

如果弹出一个值，**则为 true** ; 否则为**false** 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)
