---
title: 如何：使用上下文类实现协作信号量
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 460a1de03f34cb8ef9753e761aaef37470cd6d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467752"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>如何：使用上下文类实现协作信号量

本主题演示如何使用 concurrency:: context 类实现协作信号量类。

`Context`类，可以阻止或退出当前执行上下文。 当前上下文不能继续，因为资源不可用时，阻止或无法完成当前的上下文非常有用。 一个*信号量*是当前的执行上下文必须等待资源变为可用的一种情况的示例。 一个信号量，如关键部分对象，是一个同步对象，可在一个上下文具有对资源的独占访问权限中的代码。 但是，与不同的关键部分对象，信号量使多个上下文同时访问资源。 如果上下文的最大数目为信号量的锁，每个附加的上下文必须等待另一个上下文才能释放锁。

### <a name="to-implement-the-semaphore-class"></a>若要实现 semaphore 类

1. 声明的类，名为`semaphore`。 添加`public`和`private`部分提供了此类。

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. 在`private`一部分`semaphore`类中，声明[std:: atomic](../../standard-library/atomic-structure.md)保存信号量计数的变量和一个[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)包含上下文对象必须等待获取信号量。

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. 在中`public`一部分`semaphore`类中实现构造函数。 构造函数采用`long long`值，该值指定可以同时持有锁的上下文的最大数目。

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. 在中`public`一部分`semaphore`类，请实现`acquire`方法。 此方法减少信号量计数作为一个原子操作。 如果信号量计数变为负值，将当前上下文添加到的等待队列并调用末尾[concurrency::Context::Block](reference/context-class.md#block)方法阻止当前上下文。

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. 在中`public`一部分`semaphore`类，请实现`release`方法。 此方法以原子操作的方式增加信号量计数。 如果信号量计数为负递增操作之前，没有正在等待锁的至少一个上下文。 在这种情况下，取消阻止等待队列前部的上下文。

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>示例

`semaphore`因为在此示例中的类的行为以协作方式`Context::Block`和`Context::Yield`方法生成执行，以便在运行时可以执行其他任务。

`acquire`计数器，但它可能无法完成将上下文添加到另一个上下文调用之前的等待队列的方法递减`release`方法。 考虑到这一点，`release`方法使用数值调节钮的循环[concurrency::Context::Yield](reference/context-class.md#yield)方法来等待`acquire`方法以完成添加上下文。

`release`方法可以调用`Context::Unblock`方法，然后再`acquire`方法调用`Context::Block`方法。 无需防止此争用条件，因为运行时允许按任意顺序调用这些方法。 如果`release`方法调用`Context::Unblock`之前`acquire`方法调用`Context::Block`相同的上下文中，该上下文保持未阻止状态。 在运行时仅需要每个调用到`Context::Block`相应地调用与匹配`Context::Unblock`。

下面的示例演示完整`semaphore`类。 `wmain`函数显示此类的基本用法。 `wmain`函数使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法创建多个需要访问信号量的任务。 三个线程可以在任何时间保留锁，因为某些任务必须等待另一个任务完成并释放该锁。

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

此示例生成下面的示例输出。

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

有关详细信息`concurrent_queue`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。 有关详细信息`parallel_for`算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`cooperative-semaphore.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 合作 semaphore.cpp**

## <a name="robust-programming"></a>可靠编程

可以使用*资源获取即初始化*(RAII) 模式，以限制对访问`semaphore`给定作用域的对象。 RAII 模式下的数据结构是在堆栈上分配的。 该数据结构初始化，或将它创建和销毁或销毁数据结构时释放该资源时获取资源。 RAII 模式可确保在封闭作用域退出之前调用析构函数。 因此，资源会引发异常时或在一个函数包含多个正常管理`return`语句。

下面的示例定义名为的类`scoped_lock`，其定义中`public`一部分`semaphore`类。 `scoped_lock`类相似[scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)并[scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类。 构造函数`semaphore::scoped_lock`类获取对访问给定`semaphore`对象和析构函数释放对该对象的访问。

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
下面的示例修改传递给工作函数体`parallel_for`以便其使用 RAII 以确保该函数返回之前释放信号量的算法。 此方法可确保工作函数是异常安全。

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>请参阅

[上下文](../../parallel/concrt/contexts.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

