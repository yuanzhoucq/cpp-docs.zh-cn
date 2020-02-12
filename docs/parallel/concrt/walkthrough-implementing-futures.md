---
title: 演练：实现 Future
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141976"
---
# <a name="walkthrough-implementing-futures"></a>演练：实现 Future

本主题演示如何在应用程序中实现先期备货。 本主题演示如何将并发运行时中的现有功能合并到执行更多操作的内容中。

> [!IMPORTANT]
> 为了便于演示，本主题阐释将来的概念。 如果需要一个计算值以供将来使用的异步任务，建议使用[std：：未来](../../standard-library/future-class.md)或[concurrency：： task](../../parallel/concrt/reference/task-class.md) 。

*任务*是一种计算，可分解为其他更细化的计算。 *将来*是计算值以供将来使用的异步任务。

为了实现先期，本主题定义了 `async_future` 类。 `async_future` 类使用并发运行时的以下组件： [concurrency：： task_group](reference/task-group-class.md)类和[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)类。 `async_future` 类使用 `task_group` 类异步计算值，并使用 `single_assignment` 类来存储计算的结果。 `async_future` 类的构造函数使用计算结果的工作函数，并且 `get` 方法检索结果。

### <a name="to-implement-the-async_future-class"></a>实现 async_future 类

1. 声明一个名为 `async_future` 的模板类，该模板类在生成的计算的类型上被参数化。 将 `public` 和 `private` 部分添加到此类。

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. 在 `async_future` 类的 `private` 部分，声明 `task_group` 和 `single_assignment` 数据成员。

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. 在 `async_future` 类的 `public` 部分，实现构造函数。 构造函数是一个在计算结果的工作函数中参数化的模板。 构造函数在 `task_group` 数据成员中异步执行工作函数，并使用[concurrency：： send](reference/concurrency-namespace-functions.md#send)函数将结果写入 `single_assignment` 数据成员。

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. 在 `async_future` 类的 `public` 部分，实现析构函数。 析构函数会等待任务完成。

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. 在 `async_future` 类的 `public` 部分，实现 `get` 方法。 此方法使用[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函数检索工作函数的结果。

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的示例演示完整的 `async_future` 类及其用法的示例。 `wmain` 函数创建一个包含10000随机整数值的 std：：[vector](../../standard-library/vector-class.md)对象。 然后，它使用 `async_future` 对象查找 `vector` 对象中包含的最小值和最大值。

### <a name="code"></a>代码

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Comments

该示例产生下面的输出：

```Output
smallest: 0
largest:  9999
average:  4981
```

该示例使用 `async_future::get` 方法来检索计算结果。 如果计算仍处于活动状态，`async_future::get` 方法将等待计算结束。

## <a name="robust-programming"></a>可靠的编程

若要扩展 `async_future` 类来处理由工作函数引发的异常，请修改 `async_future::get` 方法以调用[concurrency：： task_group：： wait](reference/task-group-class.md#wait)方法。 `task_group::wait` 方法会引发工作函数生成的任何异常。

下面的示例演示 `async_future` 类的修改版本。 `wmain` 函数使用 `try`-`catch` 块来打印 `async_future` 对象的结果，或者打印工作函数生成的异常值。

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

该示例产生下面的输出：

```Output
caught exception: error
```

有关并发运行时中的异常处理模型的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `futures.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl/EHsc 先期备货**

## <a name="see-also"></a>另请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group 类](reference/task-group-class.md)<br/>
[single_assignment 类](../../parallel/concrt/reference/single-assignment-class.md)
