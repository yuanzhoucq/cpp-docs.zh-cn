---
title: 提高时间关键代码的技巧
ms.date: 11/04/2016
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
ms.openlocfilehash: 039b86eec024daf8e3473bba5d89f190507f3cfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335459"
---
# <a name="tips-for-improving-time-critical-code"></a>提高时间关键代码的技巧

编写快速代码需要了解应用程序的所有方面和它如何与系统交互。 此主题建议的方法可替代一些更明显的编码方法，帮助确保代码的时间关键部分满意地执行。

总而言之，提高时间关键代码需要：

- 知道程序的哪个部分必须快。

- 知道代码的大小和速度。

- 知道新功能的成本。

- 知道完成工作所需的最小工作量。

若要收集有关代码性能的信息，可以使用性能监视器 (perfmon.exe)。

## <a name="sections-in-this-article"></a>本文章有以下部分

- [缓存未命中和页错误](#_core_cache_hits_and_page_faults)

- [排序和搜索](#_core_sorting_and_searching)

- [MFC 和类库](#_core_mfc_and_class_libraries)

- [共享库](#vcovrsharedlibraries)

- [堆](#_core_heaps)

- [线程](#_core_threads)

- [小工作集](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a>缓存未命中和页面错误

缓存未命中不论出现在内部缓存中，还是出现在外部缓存中，都会降低程序的性能；而页错误由于会转到二级存储中获得程序指令和数据，也会降低程序的性能。

CPU 缓存命中可能会花费程序 10-20 个时钟周期。 外部缓存命中可能会花费 20-40 个时钟周期。 页错误可以花费 1,000,000 个时钟周期（假定处理器每秒处理 500,000,000 个指令并且一个页错误是 2 毫秒）。 因此，编写减少缓存未命中和页错误数的代码对程序执行最重要。

程序慢的一个原因是它们接受的页错误比需要的多，或者未命中缓存的频率比需要的高。 为避免此问题，使用具有良好引用地址的数据结构很重要，这意味着将相关的事物合在一起。 有时看上去很棒的数据结构由于引用地址不好而变得很糟，有时正好相反。 这里是两个示例：

- 动态分配的链接表可以降低程序性能，因为当搜索项或者在表中遍历到末尾时，每个跳过的链接都可能未命中缓存或导致页错误。 基于简单数组的表实现由于较好的缓存和较少的页错误，实际上可能快得多，即使考虑到数组更难增长的事实，它仍然可能更快。

- 使用动态分配的链接表的哈希表可以降低性能。 通过扩展，使用动态分配的链接表存储内容的哈希表的性能可能显著降低。 事实上，在最后的分析中，通过数组的简单线性搜索实际上可能更快（取决于具体的情况）。 基于数组的哈希表（所谓的“关闭散列”）是通常具有极佳的性能但却经常被忽略的实现。

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a>排序和搜索

与许多典型的操作相比，排序本身就很耗时。 避免不必要减速的最好办法是避免在关键时间排序。 你可能能够执行以下操作：

- 延迟排序，直到非性能关键时间。

- 在较早的非性能关键时间对数据进行排序。

- 只排序数据中真正需要排序的部分。

有时，可以按排序顺序生成列表。 注意，因为如果需要按排序顺序插入数据，则可能需要具有较差引用地址的更复杂的数据结构，从而导致缓存未命中和页错误。 没有适用于所有情况的方法。 试用几种方法并测试差异。

这里有一些通用的排序技巧：

- 使用常用排序将 Bug 减到最少。

- 任何可以预先减少排序复杂性的工作都是值得做的。 如果一次性经过数据可简化比较和减少从 O(n log n) 到 O(n) 的排序，则几乎可以肯定将先行一步。

- 考虑排序算法的引用地址和预期其涉及的数据。

与排序相比搜索的选择更少。 如果搜索是时间关键的，二进制搜索或者哈希表查找几乎总是最好的，但是与排序一样，必须记住地址。 如果二进制搜索通过的数据结构具有许多导致页错误或缓存未命中的指针，则通过小数组的线性搜索可以比二进制搜索快。

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a>MFC 和类库

Microsoft 基础类 (MFC) 可以在很大程度上简化代码的编写。 当编写时间关键代码时，应该注意一些类中的固有系统开销。 检查时间关键代码使用的 MFC 代码，查看它是否满足性能需求。 下面的列表标识了应该注意的 MFC 类和函数：

- `CString`MFC 调用 C 运行时库以动态分配[CString](../atl-mfc-shared/reference/cstringt-class.md)的内存。 一般而言，`CString` 与其他任何动态分配的字符串一样有效。 与任何动态分配的字符串一样，它也有动态分配和释放的系统开销。 堆栈上的简单 `char` 数组通常可以用于相同的目的并且更快。 不要使用 `CString` 存储常数字符串。 请改用 `const char *`。 使用 `CString` 对象执行的任何操作都有一些系统开销。 使用运行时库[字符串函数](../c-runtime-library/string-manipulation-crt.md)可能更快。

- `CArray`[CArray](../mfc/reference/carray-class.md)提供了常规数组没有的灵活性，但程序可能不需要它。 如果知道数组的特定限制，反而可以使用全局固定数组。 如果使用 `CArray`，当需要重新分配时，使用 `CArray::SetSize` 建立它的大小并指定增长的元素数。 否则，添加元素可能导致数组经常重新分配和复制，这样做效率很低而且可能产生内存碎片。 还需注意的是，如果将一项插入数组中，则 `CArray` 移动内存中后面的项并且可能需要增长数组。 这些操作可能导致缓存未命中和页错误。 如果浏览 MFC 使用的代码，你可能会发现可编写一些更特定于方案的内容以提高性能。 例如，由于 `CArray` 是一个模板，可以提供特定类型的 `CArray` 专用化。

- `CList`[CList](../mfc/reference/clist-class.md)是双链接列表，因此元素插入在列表的头部、尾部和已知位置 （）`POSITION`中是快速的。 按值或索引查找需要顺序搜索，但是，如果列表很长，则搜索速度可能会较慢。 如果代码不要求双向链接列表，则可能需要重新考虑使用 `CList`。 使用单向链接表可省去更新所有操作的附加指针以及该指针的内存的系统开销。 这种附加内存不太好，但却是解决缓存未命中或页错误的另一种可能的方法。

- `IsKindOf`此函数可以生成许多调用，并在不同的数据区域访问大量内存，从而导致引用的局部性错误。 它对于调试版本是有用的（例如，在 ASSERT 调用中），但应尽量避免在发布版本中使用它。

- `PreTranslateMessage`当`PreTranslateMessage`特定窗口树需要不同的键盘加速器或必须将消息处理插入到消息泵时，请使用。 `PreTranslateMessage` 更改 MFC 调度消息。 如果重写 `PreTranslateMessage`，只在需要的级别上这样做。 例如，如果只对转到特定视图子级的消息感兴趣，则不必重写 `CMainFrame::PreTranslateMessage`。 而应重写视图类的 `PreTranslateMessage`。

   不要为了规避正常调度路径而使用 `PreTranslateMessage` 处理发送到任何窗口的任何消息。 为此，请使用[窗口过程](../mfc/registering-window-classes.md)和 MFC 消息映射。

- `OnIdle`空闲事件可能发生在您不期望的时间，例如和`WM_KEYDOWN``WM_KEYUP`事件之间。 计时器可能是触发代码的更有效方法。 不要强制 `OnIdle` 通过生成错误信息或者总是从 `TRUE` 的重写返回 `OnIdle` 被反复调用，它从来都不允许线程休眠。 同样，计时器或者单独的线程可能更合适。

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a>共享库

代码重用是需要的。 然而，如果打算使用他人的代码，则应确保完全知道此代码在那些性能对你很重要的情况中的作用。 了解这一点的最好方法是通过单步执行源代码，或者用 PView 或性能监视器这类工具测量。

## <a name="heaps"></a><a name="_core_heaps"></a>堆

使用多个堆来做出判断。 使用 `HeapCreate` 和 `HeapAlloc` 创建的附加堆使你可以管理并因而释放一组相关分配。 不要分配出太多内存。 如果使用多个堆，特别注意开始时分配出的内存量。

作为替代使用多个堆的方法，可以使用 Helper 函数在代码和默认堆之间建立连接。 Helper 函数有利于可以提高应用程序性能的自定义分配策略。 例如，如果经常执行小的分配，可能需要将这些分配固定在默认堆的一部分内。 可以分配大的内存块，然后使用 Helper 函数从该块子分配。 如果这样做，由于分配出自默认堆，所以没有包含未用内存的附加堆。

然而，在某些情况下，使用默认堆可以减少引用地址。 使用 Process Viewer、Spy++ 或性能监视器测量在堆之间移动对象的效果。

测量堆以便可以解决堆上的每个分配。 使用 C 运行时[调试堆例程](/visualstudio/debugger/crt-debug-heap-details)检查点和转储堆。 可以将输出读入像 Microsoft Excel 这样的电子表格程序并使用数据透视表查看结果。 注意分配的总数、大小和分布。 将这些数据同工作集的大小进行比较。 还要注意相关大小对象的群集。

还可以使用性能计数器监视内存使用。

## <a name="threads"></a><a name="_core_threads"></a>线程

对于后台任务，有效的事件空闲处理可能比使用线程更快。 了解单线程程序中的引用地址更容易。

好的经验法则是仅当阻止的操作系统通知是后台工作的根本时才使用线程。 在这种情况下，线程是最好的解决方法，因为阻止事件的主线程是不实际的。

线程也提出了通信问题。 必须用消息列表或者通过分配和使用共享内存，管理线程间的通信链接。 管理通信链接通常需要同步以避免争用条件和死锁问题。 此复杂性可以很容易转变为 Bug 和性能问题。

有关详细信息，请参阅[空闲循环处理](../mfc/idle-loop-processing.md)和[多线程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="small-working-set"></a><a name="_core_small_working_set"></a>小型工作套

较小的工作集意味着更好的引用地址、更少的页错误和更多的缓存命中。 进程工作集是操作系统为测量引用地址直接提供的最接近的尺度。

- 要设置工作集的上限和下限，请使用[SetProcess工作设置大小](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize)。

- 要获取工作集的上限和下限，请使用[GetProcess工作设置大小](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize)。

- 若要查看工作集的大小，请使用 Spy++。

## <a name="see-also"></a>另请参阅

[优化代码](optimizing-your-code.md)
