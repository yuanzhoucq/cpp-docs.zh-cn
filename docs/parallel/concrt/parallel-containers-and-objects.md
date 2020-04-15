---
title: 并行容器和对象
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363049"
---
# <a name="parallel-containers-and-objects"></a>并行容器和对象

并行模式库 （PPL） 包括几个容器和对象，它们提供对其元素的线程安全访问。

*并发容器*提供对最重要的操作的并发安全访问。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。 这些容器的功能与标准库C++提供的功能类似。 例如，[并发：：concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类类似于[std：：vector](../../standard-library/vector-class.md)类，只不过`concurrent_vector`类允许您并行追加元素。 当您具有并行代码，需要读取和写入对同一容器的访问时，请使用并发容器。

*并发对象*在组件之间并发共享。 并行计算并发对象状态的进程会产生与另一个串行计算相同状态的进程相同的结果。 [并发：：可组合](../../parallel/concrt/reference/combinable-class.md)类是并发对象类型的一个示例。 该`combinable`类允许您并行执行计算，然后将这些计算合并到最终结果中。 否则，使用同步机制（例如互斥体）来同步对共享变量或资源的访问，请使用并发对象。

## <a name="sections"></a><a name="top"></a>部分

本主题详细介绍了以下并行容器和对象。

并发容器：

- [concurrent_vector 类](#vector)

  - [concurrent_vector和矢量之间的差异](#vector-differences)

  - [并发安全操作](#vector-safety)

  - [异常安全](#vector-exceptions)

- [concurrent_queue 类](#queue)

  - [concurrent_queue和队列之间的差异](#queue-differences)

  - [并发安全操作](#queue-safety)

  - [迭代器支持](#queue-iterators)

- [concurrent_unordered_map 类](#unordered_map)

  - [concurrent_unordered_map和unordered_map之间的差异](#map-differences)

  - [并发安全操作](#map-safety)

- [concurrent_unordered_multimap 类](#unordered_multimap)

- [concurrent_unordered_set 类](#unordered_set)

- [concurrent_unordered_multiset类](#unordered_multiset)

并发对象：

- [combinable 类](#combinable)

  - [方法和功能](#combinable-features)

  - [示例](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector类

[并发：：concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类是一个序列容器类，它就像[std：：：vector](../../standard-library/vector-class.md)类一样，允许您随机访问其元素。 该`concurrent_vector`类支持并发安全追加和元素访问操作。 追加操作不会使现有指针或迭代器无效。 迭代器访问和遍历操作也是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>concurrent_vector和矢量之间的差异

该`concurrent_vector`类与`vector`类非常相似。 `concurrent_vector`对象上的追加、元素访问和迭代器访问操作的复杂性与`vector`对象相同。 以下各点说明了与`concurrent_vector`的不同`vector`位置：

- 对`concurrent_vector`对象的追加、元素访问、迭代器访问和迭代器遍历操作是并发安全的。

- 只能向`concurrent_vector`对象的末尾添加元素。 类`concurrent_vector`不提供 方法`insert`。

- 对象`concurrent_vector`在追加时不使用[移动语义](../../cpp/rvalue-reference-declarator-amp-amp.md)。

- 类`concurrent_vector`不提供 或`erase``pop_back`方法。 与`vector`，使用[clear](reference/concurrent-vector-class.md#clear)方法从对象中删除`concurrent_vector`所有元素。

- 类`concurrent_vector`不连续地存储在内存中。 因此，不能以可以使用数组`concurrent_vector`的所有方式使用类。 例如，对于名为`v`type`concurrent_vector`的变量，表达式`&v[0]+2`生成未定义的行为。

- 类`concurrent_vector`定义[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 这些方法类似于[调整大小](reference/concurrent-vector-class.md#resize)方法，只不过它们是并发安全的。

- 对象`concurrent_vector`在追加或调整其大小时不会重新定位其元素。 这使得现有指针和迭代器能够在并发操作期间保持有效。

- 运行时不为 类型`concurrent_vector``bool`定义 的专用版本。

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>并发安全操作

追加或增加`concurrent_vector`对象大小或访问`concurrent_vector`对象中的元素的所有方法都是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。 此规则的例外情况是 方法`resize`。

下表显示了并发安全的常见`concurrent_vector`方法和运算符。

||||
|-|-|-|
|[在](reference/concurrent-vector-class.md#at)|[结束](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[开始](reference/concurrent-vector-class.md#begin)|[前面](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[返回](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[能力](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[空](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[大小](reference/concurrent-vector-class.md#size)|

例如`reserve`，运行时提供的与标准库C++兼容的操作并不并发安全。 下表显示了非并发安全的常见方法和运算符。

|||
|-|-|
|[分配](reference/concurrent-vector-class.md#assign)|[储备](reference/concurrent-vector-class.md#reserve)|
|[清楚](reference/concurrent-vector-class.md#clear)|[调整](reference/concurrent-vector-class.md#resize)|
|[运算符*](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

修改现有元素值的操作不并发安全。 使用同步对象（如[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象）将并发读取和写入操作同步到同一数据元素。 有关同步对象的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)。

转换使用`vector``concurrent_vector`使用 的现有代码时，并发操作可能会导致应用程序的行为发生更改。 例如，请考虑以下程序，该程序同时在对象上执行两个`concurrent_vector`任务。 第一个任务将其他元素追加到`concurrent_vector`对象。 第二个任务计算同一对象中所有元素的总和。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

尽管该方法`end`是并发安全的，但对[push_back](reference/concurrent-vector-class.md#push_back)方法的并发调用会导致返回`end`的值发生更改。 迭代器遍历的元素数不确定。 因此，每次运行该程序时，此程序都会产生不同的结果。 当元素类型不小时，在 和`push_back``end`调用之间可能存在争用条件。 该方法`end`可能会返回已分配但未完全初始化的元素。

### <a name="exception-safety"></a><a name="vector-exceptions"></a>异常安全

如果增长或分配操作引发异常，`concurrent_vector`则对象的状态将无效。 除非另有说明，`concurrent_vector`否则处于无效状态的对象的行为未定义。 但是，析构函数始终释放对象分配的内存，即使对象处于无效状态也是如此。

矢量元素`T`的数据类型必须满足以下要求。 否则，`concurrent_vector`类的行为未定义。

- 析构函数不得投掷。

- 如果默认或复制构造函数引发，则不能使用`virtual`关键字声明析构函数，并且必须使用零初始化内存正常工作。

[[顶部](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue类

[并发：：concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)类，就像[std：：queue](../../standard-library/queue-class.md)类一样，允许您访问其正面和后元素。 该`concurrent_queue`类启用并发安全排队和取消排队操作。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。 该`concurrent_queue`类还提供非并发安全的迭代器支持。

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>concurrent_queue和队列之间的差异

该`concurrent_queue`类与`queue`类非常相似。 以下各点说明了与`concurrent_queue`的不同`queue`位置：

- `concurrent_queue`对象上的排队和取消排队操作是并发安全的。

- 类`concurrent_queue`提供非并发安全的迭代器支持。

- 类`concurrent_queue`不提供 或`front``pop`方法。 类`concurrent_queue`通过定义[try_pop](reference/concurrent-queue-class.md#try_pop)方法替换这些方法。

- 类`concurrent_queue`不提供 方法`back`。 因此，您不能引用队列的末尾。

- 类`concurrent_queue`提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法而不是方法`size`。 该方法`unsafe_size`不并发安全。

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>并发安全操作

从`concurrent_queue`对象排队或取消排队的所有方法都是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。

下表显示了并发安全的常见`concurrent_queue`方法和运算符。

|||
|-|-|
|[空](reference/concurrent-queue-class.md#empty)|[推](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

尽管该方法`empty`是并发安全的，但并发操作可能会导致队列在`empty`方法返回之前增长或收缩。

下表显示了非并发安全的常见方法和运算符。

|||
|-|-|
|[清楚](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>迭代器支持

提供`concurrent_queue`不并发安全的迭代器。 我们建议您仅使用这些迭代器进行调试。

`concurrent_queue`迭代器仅向前方向遍历元素。 下表显示了每个迭代器支持的运算符。

|操作员|说明|
|--------------|-----------------|
|`operator++`|前进到队列中的下一个项目。 此运算符重载，以提供预增量和增量后语义。|
|`operator*`|检索对当前项的引用。|
|`operator->`|检索指向当前项的指针。|

[[顶部](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map类

[并发：：：concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)类是一个关联容器类，它就像[std：：unordered_map](../../standard-library/unordered-map-class.md)类一样，控制类型[std：:p空气\<const Key、Ty>](../../standard-library/pair-structure.md)的元素的不同长度序列。 将无序地图视为字典，您可以将键和值对添加到或按键查找值。 当您有多个线程或任务必须同时访问共享容器、插入或更新它时，此类非常有用。

下面的示例显示了 使用`concurrent_unordered_map`的基本结构。 本示例在范围 ['a'，" "i"中插入字符键。 由于操作顺序尚未确定，因此每个键的最终值也不确定。 但是，可以安全地并行执行插入。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

有关用于`concurrent_unordered_map`并行执行映射和减少操作的示例，请参阅[如何：在 并行中执行映射和减少操作](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>concurrent_unordered_map和unordered_map之间的差异

该`concurrent_unordered_map`类与`unordered_map`类非常相似。 以下各点说明了与`concurrent_unordered_map`的不同`unordered_map`位置：

- `erase` `bucket`、 `bucket_count``bucket_size`和 方法分别`unsafe_erase`命名为 、`unsafe_bucket``unsafe_bucket_count`和`unsafe_bucket_size`。 `unsafe_`命名约定指示这些方法不并发安全。 有关并发安全的详细信息，请参阅[并发安全操作](#map-safety)。

- 插入操作不会使现有指针或迭代器无效，也不会更改地图中已存在的项的顺序。 可以同时执行插入和遍历操作。

- `concurrent_unordered_map`仅支持正向迭代。

- 插入不会使 或更新由`equal_range`返回的迭代器无效或更新。 插入可以将不相等项追加到范围的末尾。 开始迭代器指向相等的项目。

为了帮助避免死锁，在调用内存`concurrent_unordered_map`分配器、哈希函数或其他用户定义的代码时，没有保留锁的方法。 此外，必须确保哈希函数始终计算同一值的等键。 最佳哈希函数在哈希代码空间之间统一分配密钥。

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>并发安全操作

该`concurrent_unordered_map`类支持并发安全插入和元素访问操作。 插入操作不会使现有指针或迭代器失效。 迭代器访问和遍历操作也是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不是元素初始化或特定遍历顺序的保证。 下表显示了常用`concurrent_unordered_map`的方法和运算符，这些方法和运算符是并发安全的。

|||||
|-|-|-|-|
|[在](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

尽管可以从`count`并发运行的线程中安全地调用该方法，但如果同时将新值插入容器中，则不同的线程可以接收不同的结果。

下表显示了非并发安全的常用方法和运算符。

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[运算符*](reference/concurrent-unordered-map-class.md#operator_eq)

除了这些方法之外，任何以方法`unsafe_`开头的方法也并不并发安全。

[[顶部](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap 类

[并发：：concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)类与`concurrent_unordered_map`类非常相似，只不过它允许多个值映射到同一个键。 它还在`concurrent_unordered_map`以下方面有所不同：

- [concurrent_unordered_multimap：：插入](reference/concurrent-unordered-multimap-class.md#insert)方法返回迭代器而不是`std::pair<iterator, bool>`。

- 类`concurrent_unordered_multimap`不提供，也不`operator[]`提供方法`at`。

下面的示例显示了 使用`concurrent_unordered_multimap`的基本结构。 本示例在范围 ['a'，" "i"中插入字符键。 `concurrent_unordered_multimap`使密钥具有多个值。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[顶部](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set类

[并发：：concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)类与`concurrent_unordered_map`类非常相似，只不过它管理值而不是键和值对。 类`concurrent_unordered_set`不提供，也不`operator[]`提供方法`at`。

下面的示例显示了 使用`concurrent_unordered_set`的基本结构。 本示例在范围 ['a'，" "i"中插入字符值。 并行执行插入是安全的。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[顶部](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset类

[并发：：：concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)类与类非常相似，`concurrent_unordered_set`只不过它允许重复值。 它还在`concurrent_unordered_set`以下方面有所不同：

- [concurrent_unordered_multiset：：插入](reference/concurrent-unordered-multiset-class.md#insert)方法返回迭代器而不是`std::pair<iterator, bool>`。

- 类`concurrent_unordered_multiset`不提供，也不`operator[]`提供方法`at`。

下面的示例显示了 使用`concurrent_unordered_multiset`的基本结构。 本示例在范围 ['a'，" "i"中插入字符值。 `concurrent_unordered_multiset`使值多次发生。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[顶部](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>可组合类

[并发：：可组合](../../parallel/concrt/reference/combinable-class.md)类提供可重用的线程本地存储，允许您执行细粒度计算，然后将这些计算合并到最终结果中。 你可以将 `combinable` 对象当作 reduction 变量。

当您`combinable`具有在多个线程或任务之间共享的资源时，该类非常有用。 该`combinable`类通过以无锁方式提供对共享资源的访问，帮助您消除共享状态。 因此，此类提供了使用同步机制（例如互斥体）来同步对来自多个线程的共享数据的访问的替代方法。

### <a name="methods-and-features"></a><a name="combinable-features"></a>方法和功能

下表显示了`combinable`类的一些重要方法。 有关所有类方法的详细信息，`combinable`请参阅[可组合类](../../parallel/concrt/reference/combinable-class.md)。

|方法|说明|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|检索对与当前线程上下文关联的局部变量的引用。|
|[清楚](reference/combinable-class.md#clear)|从`combinable`对象中删除所有线程局部变量。|
|[结合](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用提供的组合函数从所有线程局部计算集生成最终值。|

类`combinable`是一个模板类，在最终合并的结果上参数化。 如果调用默认构造函数，`T`模板参数类型必须具有默认构造函数和复制构造函数。 如果`T`模板参数类型没有默认构造函数，请调用以初始化函数作为其参数的构造函数的重载版本。

调用[组合](reference/combinable-class.md#combine)或[combine_each](reference/combinable-class.md#combine_each)方法后，`combinable`可以将其他数据存储在对象中。 您还可以多次调用 和`combine``combine_each`方法。 如果`combinable`对象中的局部值没有变化，则`combine`和`combine_each`方法每次调用它们时都会生成相同的结果。

### <a name="examples"></a><a name="combinable-examples"></a>例子

有关如何使用类的示例，`combinable`请参阅以下主题：

- [如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [如何：使用 combinable 来组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[顶部](#top)]

## <a name="related-topics"></a>相关主题

[如何：使用并行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
演示如何使用并行容器并行高效地存储和访问数据。

[如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
演示如何使用 类`combinable`消除共享状态，从而提高性能。

[如何：使用 combinable 来组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
演示如何使用函数`combine`合并线程本地数据集。

[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
描述 PPL，它提供了一个命令式编程模型，可促进可伸缩性和易用性，用于开发并发应用程序。

## <a name="reference"></a>参考

[concurrent_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 类](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 类](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 类](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset类](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable 类](../../parallel/concrt/reference/combinable-class.md)
