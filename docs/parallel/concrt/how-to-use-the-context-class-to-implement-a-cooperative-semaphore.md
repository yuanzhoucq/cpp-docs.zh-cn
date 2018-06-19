---
title: 如何： 使用上下文类实现协作信号量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 481c5f092becee7f455294437bdc695a6e1e4057
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693739"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>如何：使用上下文类实现协作信号量
本主题演示如何使用 concurrency::Context 类实现协作信号量类。  
  
 `Context`类，可以阻止或退出当前执行上下文。 当前上下文无法继续，因为资源不可用时，阻止或退出当前上下文的功能非常有用。 A*信号量*是当前的执行上下文必须等待资源变得可用的一种情况的示例。 信号量，如关键部分对象，为使代码在能够对资源的独占访问的上下文中的同步对象。 但是，和关键部分对象，不同的信号量允许多个上下文同时访问资源。 如果最大数目的上下文持有的信号量锁，每个其他上下文必须等待另一个上下文释放锁。  
  
### <a name="to-implement-the-semaphore-class"></a>若要实现 semaphore 类  
  
1.  声明一个名为的类`semaphore`。 添加`public`和`private`与此类的部分。  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  在`private`部分`semaphore`类中，声明[std::atomic](../../standard-library/atomic-structure.md)保留信号量计数的变量和一个[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)对象，其中包含上下文必须等到获取信号量。  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  在`public`部分`semaphore`类中，实现构造函数。 构造函数采用`long long`值，该值指定可以同时持有锁的上下文中的最大的数。  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  

4.  在`public`部分`semaphore`类中，实现`acquire`方法。 此方法可将作为一个原子操作的信号量计数。 如果信号量计数变为负值，将当前上下文添加到末尾的等待队列调用[concurrency::Context::Block](reference/context-class.md#block)方法进行阻止当前上下文。  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  在`public`部分`semaphore`类中，实现`release`方法。 此方法作为一个原子操作递增的信号量计数。 信号量计数为负递增操作之前，正在等待锁的至少一个上下文。 在这种情况下，取消阻止位于等待队列的开头的上下文。  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>示例  
 `semaphore`类在此示例中，其行为以协作方式因为`Context::Block`和`Context::Yield`方法生成执行，以便运行时可以执行其他任务。  
  
 `acquire`计数器，但它可能无法完成将上下文添加到另一个上下文调用之前要等待队列的方法递减`release`方法。 若要为此，帐户`release`方法使用数值调节钮循环调用[concurrency::Context::Yield](reference/context-class.md#yield)方法来等待`acquire`方法以完成添加上下文。  
  
 `release`方法可以调用`Context::Unblock`方法，然后才能`acquire`方法调用`Context::Block`方法。 无需防止此争用条件，因为运行时允许按任意顺序调用这些方法。 如果`release`方法调用`Context::Unblock`之前`acquire`方法调用`Context::Block`对于相同的上下文中，该上下文保持取消阻止。 运行时仅要求每个调用到`Context::Block`与相应地调用匹配`Context::Unblock`。  
  
 下面的示例演示完整`semaphore`类。 `wmain`函数显示此类的基本用法。 `wmain`函数使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法创建多个需要访问信号量的任务。 三个线程可以随时持有锁，因为某些任务必须等待另一个任务完成，然后释放锁。  
  
 [!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]  
  
 该示例产生下面的示例输出。  
  
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
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`cooperative-semaphore.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 协作 semaphore.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 你可以使用*获取资源即初始化*(RAII) 模式，以限制对访问`semaphore`为某个给定范围的对象。 下 RAII 模式，在堆栈上分配一种数据结构。 该数据结构初始化，或在创建和销毁或销毁数据结构时释放该资源时，获取一个资源。 RAII 模式可确保在封闭作用域退出之前被调用的析构函数。 因此，资源会引发异常时或当函数包含多个正常管理`return`语句。  
  
 下面的示例定义了名为一个类`scoped_lock`中, 定义`public`部分`semaphore`类。 `scoped_lock`类类似于[concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类。 构造函数`semaphore::scoped_lock`类获取对访问给定`semaphore`对象和析构函数释放对该对象的访问。  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]    
 下面的示例修改传递给工作函数体`parallel_for`，以便使用 RAII 以确保函数返回前释放信号量的算法。 此方法可确保工作函数是异常安全。  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [上下文](../../parallel/concrt/contexts.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

