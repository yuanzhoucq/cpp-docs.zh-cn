---
title: "如何：使用上下文类实现协作信号量 | Microsoft Docs"
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
  - "协作信号量实现"
  - "context 类"
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用上下文类实现协作信号量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何使用 concurrency:: context 类实现协作信号量类。  
  
  `Context` 类，可以阻止或退出当前执行上下文。 当前上下文不能继续进行，因为资源不可用时，阻止或退出当前上下文的功能非常有用。 一个 *信号量* 是当前的执行上下文必须等待资源变得可用的一种情况的一个示例。 信号量，如关键部分对象，为使代码在一个上下文中才有对资源的独占访问的同步对象。 但是，与不同的关键部分对象，信号量使多个要同时访问资源的上下文。 如果最大数目的上下文持有信号量锁，每个附加的上下文必须等待另一个上下文才能释放锁。  
  
### <a name="to-implement-the-semaphore-class"></a>若要实现 semaphore 类  
  
1.  声明的类，名为 `semaphore`。 添加 `public` 和 `private` 与此类的部分。  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  在 `private` 部分 `semaphore` 类中，声明 [std:: atomic](../../standard-library/atomic-structure.md) 保存信号量计数的变量和一个 [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 对象，其中包含必须等待获取信号量的上下文。  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  在 `public` 部分 `semaphore` 类中，实现构造函数。 构造函数采用 `long long` 值，该值指定可以同时持有锁的上下文的最大数量。  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  
  
4.  在 `public` 部分 `semaphore` 类，请实现 `acquire` 方法。 此方法可将该信号量计数作为一个原子操作。 如果信号量计数变为负值，将当前上下文添加到末尾的等待队列并调用 [concurrency::Context::Block](../Topic/Context::Block%20Method.md) 方法阻止当前上下文。  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  在 `public` 部分 `semaphore` 类，请实现 `release` 方法。 此方法以原子操作的形式递增的信号量计数。 信号量计数为负递增操作之前，至少一个正在等待锁的上下文。 在这种情况下，取消阻止的等待队列前部的上下文。  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>示例  
  `semaphore` 因为在此示例中的类的行为以协作方式 `Context::Block` 和 `Context::Yield` 方法生成执行，因此，运行时可以执行其他任务。  
  
  `acquire` 计数器，但它可能无法完成将上下文添加到另一个上下文调用之前要等待队列的方法递减 `release` 方法。 考虑到这， `release` 方法使用数值调节钮循环调用 [concurrency::Context::Yield](../Topic/Context::Yield%20Method.md) 方法来等待 `acquire` 方法以完成添加上下文。  
  
  `release` 方法可以调用 `Context::Unblock` 方法，然后再 `acquire` 方法调用 `Context::Block` 方法。 不需要防止此争用条件，因为运行时允许按任意顺序调用这些方法。 如果 `release` 方法调用 `Context::Unblock` 之前 `acquire` 方法调用 `Context::Block` 为相同的上下文，该上下文保持未阻止状态。 运行时只需向每个调用 `Context::Block` 与相应地调用匹配 `Context::Unblock`。  
  
 下面的示例演示了完整 `semaphore` 类。  `wmain` 函数显示此类的基本用法。  `wmain` 函数使用 [concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 算法创建多个需要访问的信号量的任务。 三个线程可以在任何时候持有锁，因为某些任务必须等待另一项任务完成并释放锁。  
  
 [!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]  
  
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
  
 有关详细信息 `concurrent_queue` 类，请参阅 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。 有关详细信息 `parallel_for` 算法，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到名为 `cooperative-semaphore.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc 协作 semaphore.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 您可以使用 *获取资源即初始化* (RAII) 模式，以限制对访问 `semaphore` 对象传递给给定作用域。 在 RAII 模式下，一种数据结构是在堆栈上分配。 该数据结构初始化，或在创建和销毁或销毁数据结构时释放该资源时获取资源。 RAII 模式可确保在封闭范围退出之前被调用的析构函数。 因此，会正确地管理资源时将引发异常，或在一个函数包含多个 `return` 语句。  
  
 下面的示例定义一个名为的类 `scoped_lock`, ，其定义中 `public` 部分 `semaphore` 类。  `scoped_lock` 类类似于 [concurrency::critical_section::scoped_lock](../Topic/critical_section::scoped_lock%20Class.md) 和 [concurrency::reader_writer_lock::scoped_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md) 类。 构造函数 `semaphore::scoped_lock` 类获取对访问给定 `semaphore` 对象和析构函数释放对该对象的访问权。  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]  
  
 下面的示例修改传递给函数的工作函数的正文 `parallel_for` 算法，以便使用 RAII 以确保该函数返回之前释放信号量。 此方法可确保工作函数是异常安全。  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/CPP/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [上下文](../../parallel/concrt/contexts.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

