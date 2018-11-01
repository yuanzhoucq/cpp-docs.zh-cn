---
title: 演练：实现 Future
ms.date: 11/04/2016
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 4c43719199ef4009433ec65d54fcc238d82ac305
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525634"
---
# <a name="walkthrough-implementing-futures"></a>演练：实现 Future

本主题演示如何在应用程序中实现 future。 本主题演示如何合并现有功能在并发运行时转换的内容执行更多。

> [!IMPORTANT]
>  为了便于演示，本主题阐释将来的概念。 我们建议你使用[std:: future](../../standard-library/future-class.md)或[concurrency:: task](../../parallel/concrt/reference/task-class.md)当你需要一个异步任务，计算以供将来使用的值。

一个*任务*是可以分解为更精细的其他计算的计算。 一个*将来*是一个异步任务，计算以供将来使用的值。

若要实现 future，本主题定义`async_future`类。 `async_future`类使用并发运行时这些组件： [concurrency:: task_group](reference/task-group-class.md)类和[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)类。 `async_future`类使用`task_group`类来以异步方式计算值和`single_assignment`类来存储计算的结果。 构造函数`async_future`类会将计算结果，一个工作函数和`get`方法检索结果。

### <a name="to-implement-the-asyncfuture-class"></a>实现 async_future 类

1. 声明一个名为模板类`async_future`上生成的计算的类型参数化。 添加`public`和`private`部分提供了此类。

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. 在中`private`一部分`async_future`类中，声明`task_group`和一个`single_assignment`数据成员。

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. 在中`public`一部分`async_future`类中实现构造函数。 构造函数是计算结果的工作函数参数化的模板。 构造函数以异步方式执行中的工作函数`task_group`数据成员，并使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数以将结果写入`single_assignment`数据成员。

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. 在中`public`一部分`async_future`类，请实现析构函数。 析构函数等待任务完成。

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. 在中`public`一部分`async_future`类，请实现`get`方法。 此方法使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数以检索工作函数的结果。

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例演示完整`async_future`类和其用法的示例。 `wmain`函数创建 std::[向量](../../standard-library/vector-class.md)对象，其中包含 10,000 的随机整数值。 然后，它使用`async_future`对象以查找中包含的最小和最大值`vector`对象。

### <a name="code"></a>代码

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>注释

该示例产生下面的输出：

```Output
smallest: 0
largest:  9999
average:  4981
```

该示例使用`async_future::get`方法来检索计算的结果。 `async_future::get`方法等待计算完成计算是否仍处于活动状态。

## <a name="robust-programming"></a>可靠编程

若要扩展`async_future`类来处理工作函数引发的异常，修改`async_future::get`方法来调用[task_group](reference/task-group-class.md#wait)方法。 `task_group::wait`方法将引发生成的工作函数的任何异常。

下面的示例演示的修改的版本`async_future`类。 `wmain`函数使用`try` - `catch`块来打印的结果`async_future`对象或要打印的工作函数生成的异常值。

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

该示例产生下面的输出：

```Output
caught exception: error
```

有关并发运行时中的异常处理模型的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`futures.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc futures.cpp**

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group 类](reference/task-group-class.md)<br/>
[single_assignment 类](../../parallel/concrt/reference/single-assignment-class.md)
