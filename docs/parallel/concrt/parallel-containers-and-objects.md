---
title: "并行容器和对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "并行对象"
  - "并行容器"
  - "并发容器"
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 并行容器和对象
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

并行模式库 (PPL) 包括多个容器和对象，它提供对其元素的线程安全访问。  
  
 一个 *并发容器* 提供对最重要的操作的并发安全的访问。 这些容器的功能类似于所提供的标准模板库 (STL)。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 类类似于 [std:: vector](../../standard-library/vector-class.md) 类，不同之处在于 `concurrent_vector` 类允许您将追加并行中的元素。 在您将需要读取和写入访问权限的同一个容器的并行代码，请使用并行容器。  
  
 一个 *并发对象* 同时由组件共享。 计算并行并发对象的状态的过程将生成与串行计算相同状态的另一个进程相同的结果。  [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 类是并发的对象类型的一个示例。  `combinable` 类，可以并行执行计算，然后将组合成最终结果这些计算。 否则将使用同步机制，例如，一个 mutex，对共享的变量或资源访问进行同步时，请使用并发的对象。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 部分  
 本主题介绍的以下并行容器和详细信息中的对象。  
  
 并发容器︰  
  
-   [concurrent_vector 类](#vector)  
  
    -   [并发向量之间的差异和向量](#vector-differences)  
  
    -   [并发安全的操作](#vector-safety)  
  
    -   [异常安全](#vector-exceptions)  
  
-   [concurrent_queue 类](#queue)  
  
    -   [之间的差异 concurrent_queue 和队列](#queue-differences)  
  
    -   [并发安全的操作](#queue-safety)  
  
    -   [迭代器支持](#queue-iterators)  
  
-   [concurrent_unordered_map 类](#unordered_map)  
  
    -   [之间的差异 concurrent_unordered_map 和 unordered_map](#map-differences)  
  
    -   [并发安全的操作](#map-safety)  
  
-   [concurrent_unordered_multimap 类](#unordered_multimap)  
  
-   [concurrent_unordered_set 类](#unordered_set)  
  
-   [concurrent_unordered_multiset 类](#unordered_multiset)  
  
 并发对象︰  
  
-   [combinable 类](#combinable)  
  
    -   [方法和功能](#combinable-features)  
  
    -   [示例](#combinable-examples)  
  
##  <a name="a-namevectora-concurrentvector-class"></a><a name="vector"></a> concurrent_vector 类  
  [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 类是一个序列容器类，就像 [std:: vector](../../standard-library/vector-class.md) 类，使您可以随机访问其元素。  `concurrent_vector` 类启用并发安全的追加和元素访问操作。 追加操作不会使现有指针或迭代器失效。 迭代器访问和遍历操作也是并发安全的。  
  
###  <a name="a-namevector-differencesa-differences-between-concurrentvector-and-vector"></a><a name="vector-differences"></a> 并发向量之间的差异和向量  
  `concurrent_vector` 类近似 `vector` 类。 追加和元素访问迭代器访问操作上的复杂性 `concurrent_vector` 对象是否相同 `vector` 对象。 以下几点阐释了 `concurrent_vector` 区别 `vector`:  
  
-   追加、 元素访问、 迭代器访问和迭代器遍历操作上 `concurrent_vector` 对象都是并发安全。  
  
-   您可以只向的末尾添加元素 `concurrent_vector` 对象。  `concurrent_vector` 类不提供 `insert` 方法。  
  
-   一个 `concurrent_vector` 对象不使用 [移动语义](../../cpp/rvalue-reference-declarator-amp-amp.md) 附加到它。  
  
-    `concurrent_vector` 类不提供 `erase` 或 `pop_back` 方法。 与 `vector`, ，使用 [清除](../Topic/concurrent_vector::clear%20Method.md) 方法中的所有元素中都移除 `concurrent_vector` 对象。  
  
-    `concurrent_vector` 类不存储它的元素连续内存中。 因此，不能使用 `concurrent_vector` 类中，您可以使用数组的各个方面。 例如，对于一个名为变量 `v` 类型的 `concurrent_vector`, ，该表达式 `&v[0]+2` 产生未定义的行为。  
  
-    `concurrent_vector` 类定义 [grow_by](../Topic/concurrent_vector::grow_by%20Method.md) 和 [grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md) 方法。 这些方法类似于 [调整大小](../Topic/concurrent_vector::resize%20Method.md) 方法，只不过它们是并发安全的。  
  
-   一个 `concurrent_vector` 对象不会不重新定位其元素时将附加到它还是调整其大小。 这使现有指针和迭代器在并发操作期间保持有效。  
  
-   运行时不会定义的专用的版本 `concurrent_vector` 类型 `bool`。  
  
###  <a name="a-namevector-safetya-concurrency-safe-operations"></a><a name="vector-safety"></a> 并发安全的操作  
 将追加到或增加的大小的所有方法 `concurrent_vector` 对象，或访问中的元素 `concurrent_vector` 对象，是并发安全的。 此规则的例外是 `resize` 方法。  
  
 下表显示了常见 `concurrent_vector` 方法和运算符都是并发安全。  
  
||||  
|-|-|-|  
|[在](../Topic/concurrent_vector::at%20Method.md)|[结束](../Topic/concurrent_vector::end%20Method.md)|[运算符 &#91; &#93;](../Topic/concurrent_vector::operatorOperator.md)|  
|[开始](../Topic/concurrent_vector::begin%20Method.md)|[前端](../Topic/concurrent_vector::front%20Method.md)|[push_back](../Topic/concurrent_vector::push_back%20Method.md)|  
|[返回](../Topic/concurrent_vector::back%20Method.md)|[grow_by](../Topic/concurrent_vector::grow_by%20Method.md)|[rbegin](../Topic/concurrent_vector::rbegin%20Method.md)|  
|[容量](../Topic/concurrent_vector::capacity%20Method.md)|[grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|[rend](../Topic/concurrent_vector::rend%20Method.md)|  
|[为空](../Topic/concurrent_vector::empty%20Method.md)|[max_size](../Topic/concurrent_vector::max_size%20Method.md)|[大小](../Topic/concurrent_vector::size%20Method.md)|  
  
 运行时为与 STL 兼容性等提供的操作 `reserve`, ，不是并发安全的。 下表显示通用的方法和运算符不是并发安全的。  
  
|||  
|-|-|  
|[分配](../Topic/concurrent_vector::assign%20Method.md)|[保留](../Topic/concurrent_vector::reserve%20Method.md)|  
|[清除](../Topic/concurrent_vector::clear%20Method.md)|[调整大小](../Topic/concurrent_vector::resize%20Method.md)|  
|[运算符 =](../Topic/concurrent_vector::operator=%20Operator.md)|[shrink_to_fit](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|  
  
 修改现有元素的值的操作不是并发安全。 使用同步对象，例如 [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 对象来同步并发读和写操作的同一个数据元素。 有关同步的对象的详细信息，请参阅 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)。  
  
 转换使用的现有代码时 `vector` 使用 `concurrent_vector`, ，并发操作可能会导致您的应用程序若要更改的行为。 例如，考虑下面的程序，同时执行两个任务上 `concurrent_vector` 对象。 第一个任务将追加到的其他元素 `concurrent_vector` 对象。 第二个任务将计算在同一对象中的所有元素的总和。  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_1.cpp)]  
  
 尽管 `end` 方法是并发安全的并发调用 [push_back](../Topic/concurrent_vector::push_back%20Method.md) 方法将导致返回的值 `end` 更改。 迭代器遍历的元素的数目是不确定的。 因此，此程序可能会产生不同的结果每次运行它。  
  
###  <a name="a-namevector-exceptionsa-exception-safety"></a><a name="vector-exceptions"></a> 异常安全  
 如果增长或赋值操作将引发异常的状态 `concurrent_vector` 对象将失效。 行为 `concurrent_vector` 处于无效状态的对象是不确定的除非另有说明。 但是，析构函数始终释放的内存对象分配，即使该对象处于无效状态。  
  
 矢量元素的数据类型 `T`, ，必须满足以下要求。 否则为的行为 `concurrent_vector` 类未定义。  
  
-   析构函数不得引发。  
  
-   如果默认值或复制构造函数引发，析构函数不能通过使用声明 `virtual` 关键字和它必须用零初始化内存能够正常工作。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namequeuea-concurrentqueue-class"></a><a name="queue"></a> concurrent_queue 类  
  [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 类，就像 [std::queue](../../standard-library/queue-class.md) 类中，允许您访问它的正面和备份元素。  `concurrent_queue` 类启用并发安全排队和取消排队操作。  `concurrent_queue` 类还提供了不是并发安全的迭代器支持。  
  
###  <a name="a-namequeue-differencesa-differences-between-concurrentqueue-and-queue"></a><a name="queue-differences"></a> 之间的差异 concurrent_queue 和队列  
  `concurrent_queue` 类近似 `queue` 类。 以下几点阐释了 `concurrent_queue` 区别 `queue`:  
  
-   排入队列并在取消排队操作 `concurrent_queue` 对象都是并发安全。  
  
-    `concurrent_queue` 类提供了不是并发安全的迭代器支持。  
  
-    `concurrent_queue` 类不提供 `front` 或 `pop` 方法。  `concurrent_queue` 类通过定义替代这些方法 [try_pop](../Topic/concurrent_queue::try_pop%20Method.md) 方法。  
  
-    `concurrent_queue` 类不提供 `back` 方法。 因此，不能引用队列的末尾。  
  
-    `concurrent_queue` 类提供了 [unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md) 方法而不是 `size` 方法。  `unsafe_size` 方法不是并发安全。  
  
###  <a name="a-namequeue-safetya-concurrency-safe-operations"></a><a name="queue-safety"></a> 并发安全的操作  
 所有方法到进行排队或取消排队的 `concurrent_queue` 对象都是并发安全。  
  
 下表显示了常见 `concurrent_queue` 方法和运算符都是并发安全。  
  
|||  
|-|-|  
|[为空](../Topic/concurrent_queue::empty%20Method.md)|[推送](../Topic/concurrent_queue::push%20Method.md)|  
|[get_allocator](../Topic/concurrent_queue::get_allocator%20Method.md)|[try_pop](../Topic/concurrent_queue::try_pop%20Method.md)|  
  
 尽管 `empty` 方法是并发安全的并发操作可能会导致队列扩大或收缩之前 `empty` 方法返回。  
  
 下表显示通用的方法和运算符不是并发安全的。  
  
|||  
|-|-|  
|[清除](../Topic/concurrent_queue::clear%20Method.md)|[unsafe_end](../Topic/concurrent_queue::unsafe_end%20Method.md)|  
|[unsafe_begin](../Topic/concurrent_queue::unsafe_begin%20Method.md)|[unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md)|  
  
###  <a name="a-namequeue-iteratorsa-iterator-support"></a><a name="queue-iterators"></a> 迭代器支持  
  `concurrent_queue` 提供不是并发安全的迭代器。 我们建议仅用于调试使用这些迭代器。  
  
 一个 `concurrent_queue` 迭代器遍历的向前方向中的元素。 下表显示了每个迭代器支持的运算符。  
  
|运算符|描述|  
|--------------|-----------------|  
|[operator + +](http://msdn.microsoft.com/zh-cn/4cfdd07e-927a-42f8-aaa0-d6881687f413)|前进到下一个队列中的项。 此运算符将被重载以提供前递增和后递增语义。|  
|[运算符 *](http://msdn.microsoft.com/zh-cn/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|检索与当前项的引用。|  
|[运算符->](http://msdn.microsoft.com/zh-cn/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|检索当前项的指针。|  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameunorderedmapa-concurrentunorderedmap-class"></a><a name="unordered_map"></a> concurrent_unordered_map 类  
  [超链接"file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default\\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622"concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) 类是一样的关联容器类 [std:: unordered_map](../../standard-library/unordered-map-class.md) 类中，控制的不同长序列的类型的元素 [std::pair \< const 密钥、 Ty >](../../standard-library/pair-structure.md)。 无序映射看作是一个字典，其中您可以添加到的键 / 值对或按的键查找的值。 当有多个线程或需要同时访问共享的容器，将插入它，或更新它的任务时，此类很有用。  
  
 下面的示例显示使用的基本结构 `concurrent_unordered_map`。 此示例中的范围 [a、 i] 插入字符键。 因为的运算顺序是不确定的也是不确定的每个密钥的最终值。 但是，它可安全地并行执行插入操作。  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_2.cpp)]  
  
 有关使用示例， `concurrent_unordered_map` 来执行映射和化简操作的并行，请参阅 [如何︰ 执行映射和降低操作并行](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。  
  
###  <a name="a-namemap-differencesa-differences-between-concurrentunorderedmap-and-unorderedmap"></a><a name="map-differences"></a> 之间的差异 concurrent_unordered_map 和 unordered_map  
  `concurrent_unordered_map` 类近似 `unordered_map` 类。 以下几点阐释了 `concurrent_unordered_map` 区别 `unordered_map`:  
  
-    `erase`, ，`bucket`, ，`bucket_count`, ，和 `bucket_size` 方法名为 `unsafe_erase`, ，`unsafe_bucket`, ，`unsafe_bucket_count`, ，和 `unsafe_bucket_size`, 分别。  `unsafe_` 命名约定指示这些方法不是并发安全的。 有关并发安全的详细信息，请参阅 [并发安全的操作](#map-safety)。  
  
-   插入操作不会使现有指针或迭代器失效，也不更改更改映射中已存在的项的顺序。 插入并逐层进入可同时进行操作。  
  
-   `concurrent_unordered_map` 支持向前迭代仅。  
  
-   插入不会使其无效或更新由返回的迭代器 `equal_range`。 插入可以向范围的末尾追加不相等的项。 开始迭代器指向等于项。  
  
 为了帮助避免死锁，没有方法 `concurrent_unordered_map` 持有的锁时它会调用内存分配器、 哈希函数或其他用户定义的代码。 此外，您必须确保哈希函数始终计算为相同的值相等的键。 最佳的哈希函数将键均匀分散在哈希代码空间。  
  
###  <a name="a-namemap-safetya-concurrency-safe-operations"></a><a name="map-safety"></a> 并发安全的操作  
  `concurrent_unordered_map` 类允许并发安全的插入和元素访问操作。 现有指针或迭代器插入操作不会使失效。 迭代器访问和遍历操作也是并发安全的。 下表显示了常用 `concurrent_unordered_map` 方法和运算符都是并发安全。  
  
|||||  
|-|-|-|-|  
|[在](../Topic/concurrent_unordered_map::at%20Method.md)|`count`|`find`|[key_eq](../Topic/concurrent_unordered_map::key_eq%20Method.md)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[运算符 &#91; &#93;](../Topic/concurrent_unordered_map::operatorOperator.md)|  
|`cend`|`equal_range`|[插入](../Topic/concurrent_unordered_map::insert%20Method.md)|`size`|  
  
 尽管 `count` 从并发运行的线程可以安全地调用方法，不同的线程可以接收不同的结果，如果新值同时插入到容器。  
  
 下表显示了常用的方法和运算符不是并发安全的。  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[运算符 =](../Topic/concurrent_unordered_map::operator=%20Operator.md)|[交换](../Topic/concurrent_unordered_map::swap%20Method.md)|  
  
 除了这些方法，任何方法的开头 `unsafe_` 也不是并发安全的。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameunorderedmultimapa-concurrentunorderedmultimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap 类  
  [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) 类近似 `concurrent_unordered_map` 类相似，只不过它允许多个值映射到相同的密钥。 该字符串也不同于 `concurrent_unordered_map` 通过以下方式︰  
  
-    [Concurrent_unordered_multimap:: insert](../Topic/concurrent_unordered_multimap::insert%20Method.md) 方法返回的迭代器而不是 `std::pair<iterator, bool>`。  
  
-    `concurrent_unordered_multimap` 类不提供 `operator[]` 和 `at` 方法。  
  
 下面的示例显示使用的基本结构 `concurrent_unordered_multimap`。 此示例中的范围 [a、 i] 插入字符键。 `concurrent_unordered_multimap` 使具有多个值的键。  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_3.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameunorderedseta-concurrentunorderedset-class"></a><a name="unordered_set"></a> concurrent_unordered_set 类  
  [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) 类近似 `concurrent_unordered_map` 类相似，只不过它管理而不是键和值对的值。  `concurrent_unordered_set` 类不提供 `operator[]` 和 `at` 方法。  
  
 下面的示例显示使用的基本结构 `concurrent_unordered_set`。 此示例中的范围 [a、 i] 插入字符值。 它可以安全地并行执行插入操作。  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_4.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameunorderedmultiseta-concurrentunorderedmultiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset 类  
  [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) 类近似 `concurrent_unordered_set` 类相似，只不过它允许使用重复的值。 该字符串也不同于 `concurrent_unordered_set` 通过以下方式︰  
  
-    [Concurrent_unordered_multiset:: insert](../Topic/concurrent_unordered_multiset::insert%20Method.md) 方法返回的迭代器而不是 `std::pair<iterator, bool>`。  
  
-    `concurrent_unordered_multiset` 类不提供 `operator[]` 和 `at` 方法。  
  
 下面的示例显示使用的基本结构 `concurrent_unordered_multiset`。 此示例中的范围 [a、 i] 插入字符值。 `concurrent_unordered_multiset` 允许值可能发生多次。  
  
 [!CODE [concrt-unordered-multiset#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-unordered-multiset#1)]  
  
 [[返回页首](#top)]  
  
##  <a name="a-namecombinablea-combinable-class"></a><a name="combinable"></a> combinable 类  
  [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 类提供了可重用的线程本地存储，从而执行精细计算，然后将这些计算合并成最终结果。 你可以将 `combinable` 对象当作 reduction 变量。  
  
  `combinable` 具有在多个线程或任务之间共享的资源时，类非常有用。  `combinable` 类可帮助您取消共享的状态，通过以无锁方式提供对共享资源的访问。 因此，此类提供一种同步机制，例如，一个互斥体，用于从多个线程同步对共享数据的访问的替代方法。  
  
###  <a name="a-namecombinable-featuresa-methods-and-features"></a><a name="combinable-features"></a> 方法和功能  
 下表显示了一些的重要方法 `combinable` 类。 有关所有详细信息 `combinable` 类方法，请参阅 [combinable 类](../../parallel/concrt/reference/combinable-class.md)。  
  
|方法|描述|  
|------------|-----------------|  
|[本地](../Topic/combinable::local%20Method.md)|检索指向与当前线程上下文相关联的本地变量的引用。|  
|[清除](../Topic/combinable::clear%20Method.md)|删除所有线程本地变量从 `combinable` 对象。|  
|[组合](../Topic/combinable::combine%20Method.md)<br /><br /> [combine_each](../Topic/combinable::combine_each%20Method.md)|使用提供的组合函数从集中的所有线程本地计算生成最终值。|  
  
  `combinable` 类是一种模板类，其参数化的最终的合并结果。 如果调用默认构造函数， `T` 模板参数类型必须具有默认构造函数和复制构造函数。 如果 `T` 模板参数类型不具有默认构造函数，调用以初始化函数作为其参数的构造函数的重载的版本。  
  
 您可以存储中的其他数据 `combinable` 对象调用后 [组合](../Topic/combinable::combine%20Method.md) 或 [combine_each](../Topic/combinable::combine_each%20Method.md) 方法。 您还可以调用 `combine` 和 `combine_each` 方法多次。 如果在没有本地值 `combinable` 对象的更改， `combine` 和 `combine_each` 方法将调用它们每次产生相同的结果。  
  
###  <a name="a-namecombinable-examplesa-examples"></a><a name="combinable-examples"></a> 示例  
 有关如何使用示例 `combinable` 类，请参阅以下主题︰  
  
-   [如何︰ 使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [如何︰ 使用 combinable 组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[返回页首](#top)]  
  
## <a name="related-topics"></a>相关主题  
 [如何︰ 使用并行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 演示如何使用并行容器以有效地存储和访问数据并行。  
  
 [如何︰ 使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 演示如何使用 `combinable` 类来取消共享的状态，从而提高性能。  
  
 [如何︰ 使用 combinable 组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 演示如何使用 `combine` 函数合并线程本地数据集。  
  
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
