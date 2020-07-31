---
title: 并行容器和对象
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: dffe9b3490f52645414643ebc23ab78553abafff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213900"
---
# <a name="parallel-containers-and-objects"></a>并行容器和对象

并行模式库（PPL）包含多个容器和对象，可提供对其元素的线程安全访问。

*并发容器*提供对最重要的操作的并发安全访问。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。 这些容器的功能类似于 c + + 标准库提供的功能。 例如， [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类类似于[std：： vector](../../standard-library/vector-class.md)类，不同之处在于 `concurrent_vector` 类使你能够并行追加元素。 如果有并行代码需要对同一容器的读取和写入访问权限，请使用并发容器。

*并发对象*同时在多个组件之间共享。 计算并行对象的状态的进程并行产生的结果与按顺序计算相同状态的另一个进程产生的结果相同。 [Concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类是并发对象类型的一个示例。 `combinable`利用类，可以并行执行计算，然后将这些计算合并为最终结果。 如果要在其他情况下使用同步机制（例如 mutex）来同步对共享变量或资源的访问，请使用并发对象。

## <a name="sections"></a><a name="top"></a>个

本主题详细介绍了以下并行容器和对象。

并发容器：

- [concurrent_vector 类](#vector)

  - [Concurrent_vector 和矢量之间的差异](#vector-differences)

  - [并发安全操作](#vector-safety)

  - [异常安全](#vector-exceptions)

- [concurrent_queue 类](#queue)

  - [Concurrent_queue 和队列之间的差异](#queue-differences)

  - [并发安全操作](#queue-safety)

  - [迭代器支持](#queue-iterators)

- [concurrent_unordered_map 类](#unordered_map)

  - [Concurrent_unordered_map 和 unordered_map 之间的差异](#map-differences)

  - [并发安全操作](#map-safety)

- [concurrent_unordered_multimap 类](#unordered_multimap)

- [concurrent_unordered_set 类](#unordered_set)

- [concurrent_unordered_multiset 类](#unordered_multiset)

并发对象：

- [组合类](#combinable)

  - [方法和功能](#combinable-features)

  - [示例](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector 类

[Concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类是一种序列容器类，与[std：： vector](../../standard-library/vector-class.md)类一样，可让你随机访问其元素。 `concurrent_vector`类可实现并发安全追加和元素访问操作。 追加操作不会使现有指针或迭代器失效。 迭代器访问和遍历操作也是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Concurrent_vector 和矢量之间的差异

`concurrent_vector`类与类非常相似 `vector` 。 对象上的追加、元素访问和迭代器访问操作的复杂性与对象的复杂程度 `concurrent_vector` 相同 `vector` 。 以下各点说明 `concurrent_vector` 与的不同之处 `vector` ：

- 对象上的追加、元素访问、迭代器访问和迭代器遍历操作 `concurrent_vector` 是并发安全的。

- 只能将元素添加到对象的末尾 `concurrent_vector` 。 `concurrent_vector`类不提供 `insert` 方法。

- `concurrent_vector`追加到对象时，该对象不使用[移动语义](../../cpp/rvalue-reference-declarator-amp-amp.md)。

- `concurrent_vector`类不提供 `erase` 或 `pop_back` 方法。 对于 `vector` ，请使用[clear](reference/concurrent-vector-class.md#clear)方法从对象中移除所有元素 `concurrent_vector` 。

- `concurrent_vector`类不会将其元素连续存储在内存中。 因此，您不能 `concurrent_vector` 以使用数组的所有方式使用该类。 例如，对于类型为的变量 `v` `concurrent_vector` ，表达式将 `&v[0]+2` 产生未定义的行为。

- `concurrent_vector`类定义[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 这些方法类似于[resize](reference/concurrent-vector-class.md#resize)方法，不同之处在于它们是并发安全方法。

- `concurrent_vector`追加到对象或调整其大小时，对象不会重新定位其元素。 这使得现有指针和迭代器在并发操作期间仍然有效。

- 运行时未为类型定义专用版本 `concurrent_vector` **`bool`** 。

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>并发安全操作

追加到或增加 `concurrent_vector` 对象大小或访问对象中元素的所有方法 `concurrent_vector` 均为并发安全方法。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。 此规则的例外情况是 `resize` 方法。

下表显示 `concurrent_vector` 了并发安全的常见方法和运算符。

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[准备](reference/concurrent-vector-class.md#begin)|[主](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[返回](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[功能](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[大小](reference/concurrent-vector-class.md#size)|

运行时提供的与 c + + 标准库兼容的操作，例如， `reserve` 不是并发安全的操作。 下表显示了不是并发安全的常见方法和运算符。

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[保留](reference/concurrent-vector-class.md#reserve)|
|[清除](reference/concurrent-vector-class.md#clear)|[调节](reference/concurrent-vector-class.md#resize)|
|[operator =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

修改现有元素值的操作不是并发安全操作。 使用同步对象（如[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象）将并发读写操作同步到相同的数据元素。 有关同步对象的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)。

转换使用的现有代码时 `vector` `concurrent_vector` ，并发操作可能导致应用程序的行为发生更改。 例如，请考虑以下在对象上并发执行两个任务的程序 `concurrent_vector` 。 第一个任务将其他元素追加到 `concurrent_vector` 对象。 第二个任务计算同一个对象中的所有元素之和。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

尽管 `end` 方法是并发安全方法，但对[push_back](reference/concurrent-vector-class.md#push_back)方法的并发调用会导致返回的值 `end` 更改。 迭代器遍历的元素数是不确定的。 因此，每次运行此程序时，可能会产生不同的结果。 如果元素类型为 "非普通"，则在和调用之间存在争用条件 `push_back` `end` 。 `end`方法可能返回已分配但未完全初始化的元素。

### <a name="exception-safety"></a><a name="vector-exceptions"></a>异常安全

如果增长或分配操作引发异常，则对象的状态 `concurrent_vector` 将变为无效。 除非另有说明， `concurrent_vector` 否则处于无效状态的对象的行为不确定。 但是，析构函数始终释放对象分配的内存，即使对象处于无效状态也是如此。

矢量元素的数据类型 `T` 必须满足以下要求。 否则，类的行为 `concurrent_vector` 是不确定的。

- 析构函数不能引发。

- 如果默认构造函数或复制构造函数引发，则不能使用关键字声明析构函数， **`virtual`** 并且它必须能够正确地使用初始化为零的内存。

[[顶部](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue 类

[Concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)类与[std：： queue](../../standard-library/queue-class.md)类一样，可让你访问其前端和后端元素。 `concurrent_queue`类可实现并发安全的排队和取消排队操作。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。 `concurrent_queue`类还提供了不并发安全的迭代器支持。

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Concurrent_queue 和队列之间的差异

`concurrent_queue`类与类非常相似 `queue` 。 以下各点说明 `concurrent_queue` 与的不同之处 `queue` ：

- 对象上的排队和取消排队操作 `concurrent_queue` 是并发安全的。

- `concurrent_queue`类提供不是并发安全的迭代器支持。

- `concurrent_queue`类不提供 `front` 或 `pop` 方法。 `concurrent_queue`类通过定义[try_pop](reference/concurrent-queue-class.md#try_pop)方法来替换这些方法。

- `concurrent_queue`类不提供 `back` 方法。 因此，不能引用队列的结尾。

- `concurrent_queue`类提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法，而不是 `size` 方法。 `unsafe_size`方法不是并发安全方法。

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>并发安全操作

所有从对象进行排队或取消排队的方法 `concurrent_queue` 都是并发安全方法。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。

下表显示 `concurrent_queue` 了并发安全的常见方法和运算符。

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

尽管 `empty` 方法是并发安全方法，但并发操作可能导致队列在方法返回之前增长或收缩 `empty` 。

下表显示了不是并发安全的常见方法和运算符。

|||
|-|-|
|[清除](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>迭代器支持

`concurrent_queue`提供不并发安全的迭代器。 建议仅将这些迭代器用于调试。

`concurrent_queue`迭代器仅按向前方向遍历元素。 下表显示每个迭代器支持的运算符。

|操作员|描述|
|--------------|-----------------|
|`operator++`|前进到队列中的下一项。 重载此运算符以提供前递增和递增后的语义。|
|`operator*`|检索对当前项的引用。|
|`operator->`|检索指向当前项的指针。|

[[顶部](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map 类

[Concurrency：： concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)类是一种关联容器类，就像[std：： unordered_map](../../standard-library/unordered-map-class.md)类一样，它控制[std：:p 飞机 \<const Key, Ty> ](../../standard-library/pair-structure.md)的不同长度的元素序列。 将无序映射视为字典，可将键和值对添加到中，或按键查找值。 如果有多个线程或任务需要同时访问共享容器、将其插入或更新，则此类很有用。

下面的示例演示了使用的基本结构 `concurrent_unordered_map` 。 此示例将在 [' a '，' i ' 范围内插入字符键。 由于操作的顺序是不确定的，因此每个键的最终值也不确定。 但是，并行执行插入是安全的。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

有关使用 `concurrent_unordered_map` 来并行执行映射和减少操作的示例，请参阅[如何：并行执行映射和减少操作](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Concurrent_unordered_map 和 unordered_map 之间的差异

`concurrent_unordered_map`类与类非常相似 `unordered_map` 。 以下各点说明 `concurrent_unordered_map` 与的不同之处 `unordered_map` ：

- `erase`、、 `bucket` `bucket_count` 和 `bucket_size` 方法分别命名为 `unsafe_erase` 、 `unsafe_bucket` `unsafe_bucket_count` `unsafe_bucket_size` 、和。 `unsafe_`命名约定指示这些方法不是并发安全方法。 有关并发安全的详细信息，请参阅[并发安全操作](#map-safety)。

- 插入操作不会使现有指针或迭代器失效，也不会更改映射中已存在的项的顺序。 Insert 和遍历操作可以同时发生。

- `concurrent_unordered_map`仅支持向前迭代。

- 插入不会使或更新返回的迭代器失效 `equal_range` 。 插入可以将不相等的项追加到范围的末尾。 Begin 迭代器指向相等的项。

若要帮助避免死锁， `concurrent_unordered_map` 则在调用内存分配器、哈希函数或其他用户定义的代码时，没有方法持有锁。 此外，必须确保哈希函数始终将相等键计算为相同的值。 最佳哈希函数会在哈希代码空间中统一分布密钥。

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>并发安全操作

`concurrent_unordered_map`类可实现并发安全插入和元素访问操作。 插入操作不会使现有指针或迭代器失效。 迭代器访问和遍历操作也是并发安全的。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。 下表显示了 `concurrent_unordered_map` 并发安全的常用方法和运算符。

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

尽管 `count` 可以通过并发运行的线程安全调用方法，但如果在容器中同时插入新值，则不同的线程可能会收到不同的结果。

下表显示了不并发安全的常用方法和运算符。

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator =](reference/concurrent-unordered-map-class.md#operator_eq)

除了这些方法，以开头的任何方法 `unsafe_` 也不是并发安全方法。

[[顶部](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap 类

[Concurrency：： concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)类与类密切相似， `concurrent_unordered_map` 只是它允许多个值映射到相同的键。 它还不同于 `concurrent_unordered_map` 以下方式：

- [Concurrent_unordered_multimap：： insert](reference/concurrent-unordered-multimap-class.md#insert)方法返回一个迭代器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multimap`该类不提供 `operator[]` 和 `at` 方法。

下面的示例演示了使用的基本结构 `concurrent_unordered_multimap` 。 此示例将在 [' a '，' i ' 范围内插入字符键。 `concurrent_unordered_multimap`允许键具有多个值。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[顶部](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set 类

[Concurrency：： concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)类与类密切相似， `concurrent_unordered_map` 只是它管理值而不是键和值对。 `concurrent_unordered_set`该类不提供 `operator[]` 和 `at` 方法。

下面的示例演示了使用的基本结构 `concurrent_unordered_set` 。 此示例在 [' a '，' i '] 范围内插入字符值。 并行执行插入是安全的。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[顶部](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset 类

[Concurrency：： concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)类与类密切相似， `concurrent_unordered_set` 只不过它允许重复值。 它还不同于 `concurrent_unordered_set` 以下方式：

- [Concurrent_unordered_multiset：： insert](reference/concurrent-unordered-multiset-class.md#insert)方法返回一个迭代器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multiset`该类不提供 `operator[]` 和 `at` 方法。

下面的示例演示了使用的基本结构 `concurrent_unordered_multiset` 。 此示例在 [' a '，' i '] 范围内插入字符值。 `concurrent_unordered_multiset`允许多次出现值。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[顶部](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>组合类

[Concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类提供可重用的线程本地存储，使你可以执行细化计算，然后将这些计算合并为最终结果。 你可以将 `combinable` 对象当作 reduction 变量。

`combinable`当你的资源在多个线程或任务间共享时，此类很有用。 `combinable`类通过以无锁方式提供对共享资源的访问权限，有助于消除共享状态。 因此，此类提供了一种替代方法，使用同步机制（例如互斥体）从多个线程同步对共享数据的访问。

### <a name="methods-and-features"></a><a name="combinable-features"></a>方法和功能

下表显示了类的一些重要方法 `combinable` 。 有关所有类方法的详细信息 `combinable` ，请参阅 "[组合类](../../parallel/concrt/reference/combinable-class.md)"。

|方法|描述|
|------------|-----------------|
|[地方](reference/combinable-class.md#local)|检索对与当前线程上下文关联的本地变量的引用。|
|[清除](reference/combinable-class.md#clear)|从对象中移除所有线程本地变量 `combinable` 。|
|[or](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用提供的组合函数从所有线程本地计算的集合中生成最终值。|

`combinable`类是在最终合并的结果中进行参数化的模板类。 如果调用默认构造函数，则 `T` 模板参数类型必须具有默认构造函数和复制构造函数。 如果 `T` 模板参数类型没有默认构造函数，则调用采用初始化函数作为参数的构造函数的重载版本。

`combinable`调用[组合](reference/combinable-class.md#combine)或[combine_each](reference/combinable-class.md#combine_each)方法后，可以将其他数据存储在对象中。 还可以多次调用 `combine` 和 `combine_each` 方法。 如果对象中没有本地值 `combinable` 更改，则 `combine` 和 `combine_each` 方法将在每次调用时生成相同的结果。

### <a name="examples"></a><a name="combinable-examples"></a> 示例

有关如何使用类的示例 `combinable` ，请参阅以下主题：

- [如何：使用可组合来提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [如何：使用可组合的组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[顶部](#top)]

## <a name="related-topics"></a>相关主题

[如何：使用并行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
演示如何使用并行容器以并行方式有效地存储和访问数据。

[如何：使用可组合来提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
演示如何使用 `combinable` 类消除共享状态，从而提高性能。

[如何：使用可组合的组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
演示如何使用 `combine` 函数合并线程本地数据集。

[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
介绍 PPL，它提供了一个强制性编程模型，可提高开发并发应用程序的可伸缩性和易用性。

## <a name="reference"></a>参考

[concurrent_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 类](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 类](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 类](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset 类](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[组合类](../../parallel/concrt/reference/combinable-class.md)
