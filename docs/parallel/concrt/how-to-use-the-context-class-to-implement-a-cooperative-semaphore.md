---
title: 如何：使用上下文类实现协作信号量
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 5075052592993f413290242e70206b1e227064aa
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141905"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>如何：使用上下文类实现协作信号量

本主题说明如何使用 concurrency：： Context 类实现协作信号量类。

## <a name="remarks"></a>备注

利用 `Context` 类，您可以阻止或生成当前的执行上下文。 当当前上下文无法继续，因为资源不可用时，阻止或生成当前上下文非常有用。 *信号量*是当前执行上下文必须等待资源变为可用的一种情况的示例。 信号量（如临界区对象）是一个同步对象，该对象使某个上下文中的代码可以独占访问某个资源。 但是，与临界区对象不同的是，信号灯允许多个上下文同时访问该资源。 如果最大上下文数持有信号灯锁，则每个附加上下文都必须等待另一个上下文释放该锁。

### <a name="to-implement-the-semaphore-class"></a>实现信号灯类

1. 声明一个名为 `semaphore`的类。 将 `public` 和 `private` 部分添加到此类。

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. 在 `semaphore` 类的 `private` 节中，声明一个[std：：原子](../../standard-library/atomic-structure.md)变量，该变量包含一个信号量计数和一个[concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)对象，该对象包含必须等待获取信号量的上下文。

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. 在 `semaphore` 类的 `public` 部分，实现构造函数。 构造函数采用 `long long` 值，该值指定可同时持有锁的最大上下文数。

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. 在 `semaphore` 类的 `public` 部分，实现 `acquire` 方法。 此方法以原子操作的形式递减信号量计数。 如果信号量计数变为负值，请将当前上下文添加到等待队列的末尾，并调用[concurrency：： context：： block](reference/context-class.md#block)方法来阻止当前上下文。

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. 在 `semaphore` 类的 `public` 部分，实现 `release` 方法。 此方法以原子操作的形式递增信号量计数。 如果在递增操作之前信号量计数为负，则至少有一个上下文正在等待锁定。 在这种情况下，取消阻止位于等待队列前面的上下文。

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>示例

在此示例中，`semaphore` 类的行为是协同的，因为 `Context::Block` 和 `Context::Yield` 方法会生成执行，以便运行时可以执行其他任务。

`acquire` 方法递减计数器，但在另一个上下文调用 `release` 方法之前，它可能不会完成将上下文添加到等待队列的操作。 为此，`release` 方法使用一个自旋循环，该循环调用[concurrency：： Context：： Yield](reference/context-class.md#yield)方法，以等待 `acquire` 方法完成上下文的添加。

在 `acquire` 方法调用 `Context::Block` 方法之前，`release` 方法可以调用 `Context::Unblock` 方法。 您不必防范此争用条件，因为运行时允许以任意顺序调用这些方法。 如果 `release` 方法在 `acquire` 方法为同一上下文调用 `Context::Block` 之前调用 `Context::Unblock`，则该上下文将保持取消阻止。 运行时只要求对 `Context::Block` 的每个调用都与 `Context::Unblock`的相应调用匹配。

下面的示例演示完整的 `semaphore` 类。 `wmain` 函数显示此类的基本用法。 `wmain` 函数使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法来创建需要访问信号量的多个任务。 因为有三个线程随时可以持有锁，所以某些任务必须等待其他任务完成并释放锁。

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

此示例将生成以下示例输出。

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

有关 `concurrent_queue` 类的详细信息，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。 有关 `parallel_for` 算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `cooperative-semaphore.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc cooperative-semaphore**

## <a name="robust-programming"></a>可靠的编程

可以使用*资源采集为初始化*（RAII）模式，将对 `semaphore` 对象的访问限制到给定作用域。 在 RAII 模式下，在堆栈上分配数据结构。 此数据结构在创建时初始化或获取资源，并在数据结构销毁时销毁或释放该资源。 RAII 模式可确保在封闭范围退出之前调用析构函数。 因此，当引发异常时，或者当函数包含多个 `return` 语句时，将正确管理资源。

下面的示例定义了一个名为 `scoped_lock`的类，该类在 `semaphore` 类的 `public` 部分中定义。 `scoped_lock` 类与[concurrency：： critical_section：： scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类类似。 `semaphore::scoped_lock` 类的构造函数获取给定 `semaphore` 对象的访问权限，析构函数将释放对该对象的访问权限。

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
下面的示例修改传递到 `parallel_for` 算法的工作函数的正文，以便它使用 RAII 来确保在函数返回之前释放信号量。 此方法可确保工作函数为异常安全。

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>另请参阅

[上下文](../../parallel/concrt/contexts.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)
