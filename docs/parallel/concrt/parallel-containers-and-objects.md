---
title: "并行容器和对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9159b9c8170ee73afd8bee5305506a842368a231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="parallel-containers-and-objects"></a>并行容器和对象
并行模式库 (PPL) 包括多个容器和对象，它提供对其元素的线程安全访问。  
  
 A*并发容器*提供对最重要的操作的并发安全访问权限。 这些容器的功能类似于 c + + 标准库提供的那些。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类类似于[std:: vector](../../standard-library/vector-class.md)类，只不过`concurrent_vector`类可追加并行中的元素。 如果您具有需要读到的同一容器的写访问权限的并行代码，请使用并发容器。  
  
 A*并发对象*同时由组件共享。 计算并行并发对象的状态的过程将生成与串行计算的相同状态的另一个进程相同的结果。 [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类是并发的对象类型的一个示例。 `combinable`类允许你以并行执行计算，然后将组合成最终结果这些计算。 否则将使用同步机制，例如，一个 mutex，对共享的变量或资源访问进行同步时，请使用并发的对象。  
  
##  <a name="top"></a> 部分  
 本主题介绍以下并行容器和详细信息中的对象。  
  
 并发容器：  
  
-   [concurrent_vector 类](#ctor)  
  
    -   [之间的差异 concurrent_vector 和向量](#ctor)  
  
    -   [并发安全操作，](#ctor)  
  
    -   [异常安全](#ctor)  
  
-   [concurrent_queue 类](#queue)  
  
    -   [之间的差异 concurrent_queue 和队列](#queue-differences)  
  
    -   [并发安全操作，](#queue-safety)  
  
    -   [迭代器支持](#queue-iterators)  
  
-   [concurrent_unordered_map 类](#unordered_map)  
  
    -   [之间的差异 concurrent_unordered_map 和 unordered_map](#map-differences)  
  
    -   [并发安全操作，](#map-safety)  
  
-   [concurrent_unordered_multimap 类](#unordered_multimap)  
  
-   [concurrent_unordered_set 类](#unordered_set)  
  
-   [concurrent_unordered_multiset 类](#unordered_multiset)  
  
 并发对象：  
  
-   [combinable 类](#combinable)  
  
    -   [方法和功能](#combinable-features)  
  
    -   [示例](#combinable-examples)  
  
##  <a name="vector"></a>concurrent_vector 类  
 [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类是序列容器类，它，就像[std:: vector](../../standard-library/vector-class.md)类，还可让你随机访问其元素。 `concurrent_vector`类启用并发安全追加和元素访问操作。 追加操作不会使现有指针或迭代器失效。 迭代器访问和遍历操作也是并发安全。  
  
###  <a name="vector-differences"></a>之间的差异 concurrent_vector 和向量  
 `concurrent_vector`类十分类似于`vector`类。 追加、 元素访问和迭代器访问操作的复杂性`concurrent_vector`对象是否相同`vector`对象。 以下几点阐释了`concurrent_vector`区别`vector`:  
  
-   追加、 元素访问、 迭代器访问和迭代器遍历操作上`concurrent_vector`对象是并发安全。  
  
-   你可以仅向的末尾添加元素`concurrent_vector`对象。 `concurrent_vector`类不提供`insert`方法。  
  
-   A`concurrent_vector`对象不使用[移动语义](../../cpp/rvalue-reference-declarator-amp-amp.md)时将追加到它。  
  

-   `concurrent_vector`类不提供`erase`或`pop_back`方法。 与`vector`，使用[清除](reference/concurrent-vector-class.md#clear)方法移除所有元素从`concurrent_vector`对象。  
  
-   `concurrent_vector`类不会存储其元素连续内存中。 因此，不能使用`concurrent_vector`类在你可以使用数组的所有方面。 例如，对于一个名为变量`v`类型的`concurrent_vector`，表达式`&v[0]+2`产生未定义的行为。  
  
-   `concurrent_vector`类定义[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 这些方法类似于[调整大小](reference/concurrent-vector-class.md#resize)方法，只不过它们是并发安全。  
  
-   A`concurrent_vector`对象不会不重新定位其元素时向其追加或者调整其大小。 这使现有指针和迭代器在并发操作期间保持有效。  
  
-   运行时不会定义一个专门`concurrent_vector`类型`bool`。  
  
###  <a name="vector-safety"></a>并发安全操作，  
 将追加到或增加的大小的所有方法`concurrent_vector`对象，或访问中的元素`concurrent_vector`对象，是并发安全的。 此规则的例外是`resize`方法。  
  
 下表显示了常见`concurrent_vector`方法和运算符都是并发安全。  
  
||||  
|-|-|-|  

|[在](reference/concurrent-vector-class.md#at)|[结束](reference/concurrent-vector-class.md#end)|[运算符 &#91; &#93;](reference/concurrent-vector-class.md#operator_at)|  
|[开始](reference/concurrent-vector-class.md#begin)|[前面](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|  
|[返回](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|  
|[容量](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|  
|[空](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[大小](reference/concurrent-vector-class.md#size)|  

  
 运行时为兼容性与 c + + 标准库，例如，提供的操作`reserve`，不是并发安全。 下表显示了常见的方法和不是并发安全的运算符。  
  
|||  
|-|-|  

|[分配](reference/concurrent-vector-class.md#assign)|[保留](reference/concurrent-vector-class.md#reserve)|  
|[清除](reference/concurrent-vector-class.md#clear)|[调整大小](reference/concurrent-vector-class.md#resize)|  
|[运算符 =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|  
  
 修改现有元素的值的操作不是并发安全。 使用的同步对象，如[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象同步并发读取和写入到相同的数据元素的操作。 有关同步对象的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)。  
  
 当你还将使用的现有代码转换`vector`使用`concurrent_vector`，并发操作可能会导致应用程序，若要更改的行为。 例如，考虑下面的程序，同时执行两个任务`concurrent_vector`对象。 第一个任务将追加到的其他元素`concurrent_vector`对象。 第二个任务将计算在同一对象的所有元素的总和。  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]  
  

 尽管`end`方法是并发安全并发调用[push_back](reference/concurrent-vector-class.md#push_back)方法使返回的值`end`更改。 迭代器遍历的元素数是不确定的。 因此，此程序可以生成不同的结果每次运行它。  
  
###  <a name="vector-exceptions"></a>异常安全  
 如果增长或赋值操作引发异常的状态`concurrent_vector`对象将变为无效。 行为`concurrent_vector`处于无效状态的对象是不确定的除非另有说明。 但是，析构函数始终释放的内存分配的对象，即使此对象处于无效状态。  
  
 矢量元素的数据类型`T`，必须满足以下要求。 否则为的行为`concurrent_vector`未定义类。  
  
-   析构函数不得引发。  
  
-   如果默认值或复制构造函数引发，析构函数不能通过使用声明`virtual`关键字和它必须用零初始化内存中正常工作。  
  
 [[返回页首](#top)]  
  
##  <a name="queue"></a>concurrent_queue 类  
 [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)类，就像[std::queue](../../standard-library/queue-class.md)类，还可让你访问其前和备份元素。 `concurrent_queue`类启用并发安全排入队列，并取消排队操作。 `concurrent_queue`类还提供了不是并发安全的迭代器支持。  
  
###  <a name="queue-differences"></a>之间的差异 concurrent_queue 和队列  
 `concurrent_queue`类十分类似于`queue`类。 以下几点阐释了`concurrent_queue`区别`queue`:  
  
-   排入队列和上取消排队操作`concurrent_queue`对象是并发安全。  
  
-   `concurrent_queue`类提供不是并发安全的迭代器支持。  
  

-   `concurrent_queue`类不提供`front`或`pop`方法。 `concurrent_queue`类定义替换这些方法[try_pop](reference/concurrent-queue-class.md#try_pop)方法。  
  
-   `concurrent_queue`类不提供`back`方法。 因此，不能引用队列的末尾。  
  
-   `concurrent_queue`类提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法而不是`size`方法。 `unsafe_size`方法不是并发安全。  

  
###  <a name="queue-safety"></a>并发安全操作，  
 所有方法到进行排队或取消排队的`concurrent_queue`对象是并发安全。  
  
 下表显示了常见`concurrent_queue`方法和运算符都是并发安全。  
  
|||  
|-|-|  
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|  
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|  


  
 尽管`empty`方法是并发安全的并发操作可能会导致队列来增加或缩减之前`empty`方法返回。  
  
 下表显示了常见的方法和不是并发安全的运算符。  
  
|||  
|-|-|  
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|  
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|  


  
###  <a name="queue-iterators"></a>迭代器支持  
 `concurrent_queue`提供不是并发安全的迭代器。 我们建议为仅限调试使用这些迭代器。  
  
 A`concurrent_queue`迭代器遍历中的向前方向的元素。 下表显示了每个迭代器支持的运算符。  
  
|运算符|描述|  
|--------------|-----------------|  
|[operator++](http://msdn.microsoft.com/en-us/4cfdd07e-927a-42f8-aaa0-d6881687f413)|前进到队列中的下一项。 此运算符将被重载以提供前递增和后递增语义。|  
|[operator*](http://msdn.microsoft.com/en-us/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|检索对当前项的引用。|  
|[operator->](http://msdn.microsoft.com/en-us/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|检索指向当前项。|  
  
 [[返回页首](#top)]  
  
##  <a name="unordered_map"></a>concurrent_unordered_map 类  
 [超链接"file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default\\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622"concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)类是关联容器类，它，就像[std:: unordered_map](../../standard-library/unordered-map-class.md)类中，控件类型的元素的长短序列[std:: pair\<const 密钥、 Ty >](../../standard-library/pair-structure.md)。 无序映射看作是一个字典，其中你可以添加到的键 / 值对或按的键查找的值。 当你具有多个线程或需要同时访问共享的容器，将插入它，或更新它的任务时，此类很有用。  
  
 下面的示例演示使用的基本结构`concurrent_unordered_map`。 此示例在范围 ['a'，' i'] 中插入字符键。 因为的运算顺序是不确定，每个键的最终值也是不确定的。 但是，它可安全地并行执行插入操作。  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]  
  
 有关示例，使用`concurrent_unordered_map`来执行映射和化简并行操作，请参阅[如何： 执行映射和减少操作并行](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。  
  
###  <a name="map-differences"></a>之间的差异 concurrent_unordered_map 和 unordered_map  
 `concurrent_unordered_map`类十分类似于`unordered_map`类。 以下几点阐释了`concurrent_unordered_map`区别`unordered_map`:  
  
-   `erase`， `bucket`， `bucket_count`，和`bucket_size`方法的命名`unsafe_erase`， `unsafe_bucket`， `unsafe_bucket_count`，和`unsafe_bucket_size`分别。 `unsafe_`命名约定指示这些方法不是并发安全。 有关并发安全的详细信息，请参阅[并发安全操作，](#map-safety)。  
  
-   插入操作不会使现有指针或迭代器，失效，也不更改更改在映射中已存在的项的顺序。 插入和遍历操作可以同时发生。  
  
-   `concurrent_unordered_map`支持转发仅迭代。  
  
-   插入不会使其无效或更新由迭代器`equal_range`。 插入可以将不相等的项追加到范围的末尾。 开始迭代器指向相等的项。  
  
 为了帮助避免死锁，没有方法`concurrent_unordered_map`持有一个锁，当它调用的内存分配器、 哈希函数或其他用户定义的代码。 此外，你必须确保哈希函数始终计算结果为相同的值相等的密钥。 最佳的哈希函数在哈希代码空间之间均匀分发键。  
  
###  <a name="map-safety"></a>并发安全操作，  
 `concurrent_unordered_map`类启用并发安全 insert 和元素访问操作。 现有的指针或迭代器插入操作不会使失效。 迭代器访问和遍历操作也是并发安全。 下表显示了常用`concurrent_unordered_map`方法和运算符都是并发安全。  
  
|||||  
|-|-|-|-|  
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[operator[]](reference/concurrent-unordered-map-class.md#operator_at)|  
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|  
  
 尽管`count`方法可以安全地调用从线程并发运行时，不同的线程可以接收不同的结果，如果新值同时插入到容器。  
  
 下表显示了常用的方法和不是并发安全的运算符。  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq) 


  
 除了这些方法中，任何方法的开头`unsafe_`也不是并发安全。  
  
 [[返回页首](#top)]  
  
##  <a name="unordered_multimap"></a>concurrent_unordered_multimap 类  
 [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)类十分类似于`concurrent_unordered_map`类相似，只不过它允许多个值将映射到相同的密钥。 它也不同于`concurrent_unordered_map`通过以下方式：  
  
-   [Concurrent_unordered_multimap:: insert](reference/concurrent-unordered-multimap-class.md#insert)方法返回的迭代器，而不是`std::pair<iterator, bool>`。  

  
-   `concurrent_unordered_multimap`类不提供`operator[]`也不`at`方法。  
  
 下面的示例演示使用的基本结构`concurrent_unordered_multimap`。 此示例在范围 ['a'，' i'] 中插入字符键。 `concurrent_unordered_multimap`使具有多个值的键。  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="unordered_set"></a>concurrent_unordered_set 类  
 [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)类十分类似于`concurrent_unordered_map`类相似，只不过它管理而不是键和值对的值。 `concurrent_unordered_set`类不提供`operator[]`也不`at`方法。  
  
 下面的示例演示使用的基本结构`concurrent_unordered_set`。 此示例在范围 ['a'，' i'] 中插入字符值。 则可以安全地并行执行插入操作。  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="unordered_multiset"></a>concurrent_unordered_multiset 类  
 [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)类十分类似于`concurrent_unordered_set`类相似，只不过它允许重复值。 它也不同于`concurrent_unordered_set`通过以下方式：  
  

-   [Concurrent_unordered_multiset:: insert](reference/concurrent-unordered-multiset-class.md#insert)方法返回的迭代器，而不是`std::pair<iterator, bool>`。  

  
-   `concurrent_unordered_multiset`类不提供`operator[]`也不`at`方法。  
  
 下面的示例演示使用的基本结构`concurrent_unordered_multiset`。 此示例在范围 ['a'，' i'] 中插入字符值。 `concurrent_unordered_multiset`启用要发生多次的值。  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="combinable"></a>combinable 类  
 [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类提供允许你执行细化的计算，然后将这些计算合并为最终的结果的可重用的线程本地存储。 你可以将 `combinable` 对象当作 reduction 变量。  
  
 `combinable`必须在多个线程或任务之间共享的资源类很有用。 `combinable`类可帮助您取消共享的状态，通过以无锁方式提供对共享资源的访问。 因此，此类提供一种同步机制，例如，一个 mutex，用于从多个线程同步对共享数据的访问的替代方法。  
  
###  <a name="combinable-features"></a>方法和功能  
 下表显示了一些重要的方法`combinable`类。 有关所有详细信息`combinable`类方法，请参阅[combinable 类](../../parallel/concrt/reference/combinable-class.md)。  
  
|方法|描述|  
|------------|-----------------|  
|[本地](reference/combinable-class.md#local)|检索与当前线程上下文关联的本地变量的引用。|  
|[clear](reference/combinable-class.md#clear)|删除所有线程本地变量，从`combinable`对象。|  
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用提供的组合函数来从组的所有线程本地计算生成一个最终值。|  
  
 `combinable`类是在最终的合并结果参数化的模板类。 如果调用默认构造函数，`T`模板参数类型必须具有默认构造函数和复制构造函数。 如果`T`模板参数类型不具有默认构造函数，调用以初始化函数作为其参数的构造函数的重载的版本。  
  
 你可以存储中的其他数据`combinable`对象后调用[组合](reference/combinable-class.md#combine)或[combine_each](reference/combinable-class.md#combine_each)方法。 你还可以调用`combine`和`combine_each`方法多次。 如果在没有本地值`combinable`对象更改，`combine`和`combine_each`方法将产生相同的结果调用它们每次。  
  
###  <a name="combinable-examples"></a>示例  
 有关如何使用示例`combinable`类，请参阅以下主题：  
  
-   [如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [如何：使用 combinable 来组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[返回页首](#top)]  
  
## <a name="related-topics"></a>相关主题  
 [如何：使用并行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 演示如何使用并行容器来高效地存储和访问数据并行。  
  
 [如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 演示如何使用`combinable`类来取消共享的状态，并因此改进性能。  
  
 [如何：使用 combinable 来组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 演示如何使用`combine`函数合并线程本地数据集。  
  
 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 介绍 PPL，它提供命令式编程模型。  
  
## <a name="reference"></a>参考  
 [concurrent_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map 类](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap 类](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set 类](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset 类](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable 类](../../parallel/concrt/reference/combinable-class.md)
