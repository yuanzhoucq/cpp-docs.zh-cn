---
title: concurrent_queue 类
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: a117a040adbf7f3aa316c346489bd2731d6c2402
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230345"
---
# <a name="concurrent_queue-class"></a>concurrent_queue 类

`concurrent_queue` 类是允许对其元素进行先进先出访问的序列容器类。 它支持一组有限的并发安全操作，例如 `push` 和 `try_pop`。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

## <a name="syntax"></a>语法

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>参数

*T*<br/>
要存储在队列中的元素的数据类型。

*_Ax*<br/>
表示存储分配器对象的类型，该对象封装有关此并发队列的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<T>`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`allocator_type`|一个类型，表示并发队列的分配器类。|
|`const_iterator`|一种类型，它表示 **`const`** 对并发队列中的元素的非线程安全迭代器。|
|`const_reference`|一种类型，该类型提供对 **`const`** 存储在并发队列中用于读取和执行操作的元素的引用 **`const`** 。|
|`difference_type`|一种类型，它提供并发队列中两个元素之间的有符号距离。|
|`iterator`|一种类型，它表示对并发队列中的元素的非线程安全迭代器。|
|`reference`|一种类型，该类型提供对存储在并发队列中的元素的引用。|
|`size_type`|一种类型，它对并发队列中的元素数进行计数。|
|`value_type`|表示存储在并发队列中的数据类型的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[concurrent_queue](#ctor)|已重载。 构造并发队列。|
|[~ concurrent_queue 析构函数](#dtor)|销毁并发队列。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[清除](#clear)|清除并发队列，销毁当前排队的任何元素。 此方法不是并发安全方法。|
|[empty](#empty)|测试在调用此方法时并发队列是否为空。 此方法是并发安全方法。|
|[get_allocator](#get_allocator)|返回用于构造并发队列的分配器副本。 此方法是并发安全方法。|
|[push](#push)|已重载。 将项排队在并发队列的结尾处。 此方法是并发安全方法。|
|[try_pop](#try_pop)|从队列中取消排队一个项（如果有）。 此方法是并发安全方法。|
|[unsafe_begin](#unsafe_begin)|已重载。 返回类型 `iterator` 或 `const_iterator` 并发队列开头的迭代器。 此方法不是并发安全方法。|
|[unsafe_end](#unsafe_end)|已重载。 返回类型 `iterator` 或 `const_iterator` 并发队列末尾的迭代器。 此方法不是并发安全方法。|
|[unsafe_size](#unsafe_size)|返回队列中的项数。 此方法不是并发安全方法。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`concurrent_queue`

## <a name="requirements"></a>要求

**标头：** concurrent_queue。h

**命名空间：** 并发

## <a name="clear"></a><a name="clear"></a>清除

清除并发队列，销毁当前排队的任何元素。 此方法不是并发安全方法。

```cpp
void clear();
```

## <a name="concurrent_queue"></a><a name="ctor"></a>concurrent_queue

构造并发队列。

```cpp
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>参数

*_InputIterator*<br/>
输入迭代器的类型，它指定值的范围。

*_Al*<br/>
要用于此对象的分配器类。

*_OtherQ*<br/>
要从中复制或移动元素的源 `concurrent_queue` 对象。

*_Begin*<br/>
要复制的元素范围内的第一个元素的位置。

*_End*<br/>
要复制的元素范围外的第一个元素的位置。

### <a name="remarks"></a>备注

所有构造函数都存储分配器对象 `_Al` 并初始化队列。

第一个构造函数指定一个空的初始队列，并显式指定要使用的分配器类型。

第二个构造函数指定并发队列的副本 `_OtherQ` 。

第三个构造函数指定并发队列 `_OtherQ` 的移动。

第四个构造函数指定由迭代器范围 [ `_Begin` ，）提供的值 `_End` 。

## <a name="concurrent_queue"></a><a name="dtor"></a>~ concurrent_queue

销毁并发队列。

```cpp
~concurrent_queue();
```

## <a name="empty"></a><a name="empty"></a>空白处

测试在调用此方法时并发队列是否为空。 此方法是并发安全方法。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果并发队列目前为空，则为 **`false`** ; 否则为。

### <a name="remarks"></a>备注

尽管此方法在调用方法、和时是并发安全的， `push` 而 `try_pop` `empty` 返回的值在被调用线程检查时可能不正确。

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

返回用于构造并发队列的分配器副本。 此方法是并发安全方法。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

用于构造并发队列的分配器副本。

## <a name="push"></a><a name="push"></a>请求

将项排队在并发队列的结尾处。 此方法是并发安全方法。

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
要添加到队列中的项。

### <a name="remarks"></a>备注

`push`与对方法、和的调用有关的并发安全 `push` `try_pop` `empty` 。

## <a name="try_pop"></a><a name="try_pop"></a>try_pop

从队列中取消排队一个项（如果有）。 此方法是并发安全方法。

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
对要存储取消排队项的位置的引用。

### <a name="return-value"></a>返回值

**`true`** 如果成功取消排队项，则 **`false`** 为; 否则为。

### <a name="remarks"></a>备注

如果某个项已成功取消排队，则该参数将 `_Dest` 接收取消排队值，该队列中保留的原始值将被销毁，此函数将返回 **`true`** 。 如果没有要取消排队的项，则此函数 **`false`** 将返回而不进行阻止，并且不 `_Dest` 定义参数的内容。

`try_pop`与对方法、和的调用有关的并发安全 `push` `try_pop` `empty` 。

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a>unsafe_begin

返回类型 `iterator` 或 `const_iterator` 并发队列开头的迭代器。 此方法不是并发安全方法。

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>返回值

类型 `iterator` 或 `const_iterator` 并发队列对象的开头的迭代器。

### <a name="remarks"></a>备注

类的迭代器 `concurrent_queue` 主要用于调试，因为它们速度较慢，并且迭代不与其他队列操作有关并发安全。

## <a name="unsafe_end"></a><a name="unsafe_end"></a>unsafe_end

返回类型 `iterator` 或 `const_iterator` 并发队列末尾的迭代器。 此方法不是并发安全方法。

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>返回值

类型 `iterator` `const_iterator` 为或并发队列末尾的迭代器。

### <a name="remarks"></a>备注

类的迭代器 `concurrent_queue` 主要用于调试，因为它们速度较慢，并且迭代不与其他队列操作有关并发安全。

## <a name="unsafe_size"></a><a name="unsafe_size"></a>unsafe_size

返回队列中的项数。 此方法不是并发安全方法。

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>返回值

并发队列的大小。

### <a name="remarks"></a>备注

`unsafe_size`不是并发安全的，如果同时调用方法 `push` 、和，则可能产生不正确的结果 `try_pop` `empty` 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
