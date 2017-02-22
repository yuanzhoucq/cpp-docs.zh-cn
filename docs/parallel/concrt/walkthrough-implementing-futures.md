---
title: "演练：实现 Future | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "实现 Future [并发运行时]"
  - "Future, 实现 [并发运行时]"
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# 演练：实现 Future
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何在您的应用程序中实现 future。 本主题演示如何结合使用现有功能在并发运行时转换的内容的详细信息。  
  
> [!IMPORTANT]
>  为了便于演示，本主题阐释将来的概念。 我们建议你使用 [std:: future](../../standard-library/future-class.md) 或 [concurrency:: task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 当您需要计算该值以备将来使用的异步任务。  
  
 一个 *任务* 是可以分解为更多、 更细粒度的计算的计算。 一个 *将来* 是计算更高版本使用的值是一个异步任务。  
  
 若要实现 future，本主题定义 `async_future` 类。  `async_future` 类使用并发运行时的以下组件︰ [concurrency:: task_group](../Topic/task_group%20Class.md) 类和 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 类。  `async_future` 类使用 `task_group` 类来异步计算值与 `single_assignment` 类来存储计算的结果。 构造函数 `async_future` 类采用计算结果，一个工作函数和 `get` 方法将检索结果。  
  
### <a name="to-implement-the-asyncfuture-class"></a>实现 async_future 类  
  
1.  声明一个名为模板类 `async_future` ，已生成的计算的类型参数化。 添加 `public` 和 `private` 与此类的部分。  
  
 [!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_1.cpp)]  
  
2.  在 `private` 部分 `async_future` 类中，声明 `task_group` 和 `single_assignment` 数据成员。  
  
 [!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_2.cpp)]  
  
3.  在 `public` 部分 `async_future` 类中，实现构造函数。 构造函数是计算结果的工作函数参数化的模板。 以异步方式执行的构造函数中的工作函数 `task_group` 数据成员，并使用 [concurrency:: send](../Topic/send%20Function.md) 函数以将结果写入 `single_assignment` 数据成员。  
  
 [!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_3.cpp)]  
  
4.  在 `public` 部分 `async_future` 类，请实现析构函数。 析构函数等待任务完成。  
  
 [!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_4.cpp)]  
  
5.  在 `public` 部分 `async_future` 类，请实现 `get` 方法。 此方法使用 [concurrency:: receive](../Topic/receive%20Function.md) 函数以检索工作函数的结果。  
  
 [!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_5.cpp)]  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示了完整 `async_future` 类，其用法的示例。  `wmain` 函数创建 std::[向量](../../standard-library/vector-class.md) 对象，其中包含 10000 随机整数值。 然后，它使用 `async_future` 对象查找中包含的最小和最大值 `vector` 对象。  
  
### <a name="code"></a>代码  
 [!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_6.cpp)]  
  
### <a name="comments"></a>注释  
 该示例产生下面的输出：  
  
```Output  
smallest: 0  
largest:  9999  
average:  4981  
```  
  
 该示例使用 `async_future::get` 方法来检索计算结果。  `async_future::get` 方法等待计算完成计算是否仍处于活动状态。  
  
## <a name="robust-programming"></a>可靠编程  
 若要扩展 `async_future` 类来处理工作函数引发的异常，请修改 `async_future::get` 方法来调用 [concurrency::task_group::wait](../Topic/task_group::wait%20Method.md) 方法。  `task_group::wait` 方法将引发生成的工作函数的任何异常。  
  
 下面的示例演示的修改的版本 `async_future` 类。  `wmain` 函数使用 `try`-`catch` 块来输出结果的 `async_future` 对象或要打印的值生成的工作函数的异常。  
  
 [!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_7.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
caught exception: error  
```  
  
 有关并发运行时中的异常处理模型的详细信息，请参阅 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到名为 `futures.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc futures.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [task_group 类](../Topic/task_group%20Class.md)   
 [single_assignment 类](../../parallel/concrt/reference/single-assignment-class.md)
