---
title: 如何：使用消息块筛选器
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 1bfa11953d27dc7e013e715b3f58111f124caeaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321931"
---
# <a name="how-to-use-a-message-block-filter"></a>如何：使用消息块筛选器

本文档演示如何使用筛选器函数来启用异步消息块来接受或拒绝该消息的负载根据一条消息。

当创建一个消息块对象如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)即[concurrency:: call](../../parallel/concrt/reference/call-class.md)，或[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)，可以提供*筛选器函数*，它确定消息块是接受还是拒绝消息。 筛选器函数是有用的方式，以保证的消息块只接收特定值。

筛选器函数非常重要，因为它们使您能够连接消息块来形成*数据流网络*。 在数据流网络中，消息块控制通过处理符合特定条件的那些消息的数据流。 这与控制流模型，其中使用控制结构，如条件语句、 循环、 受监管的数据流，依此类推。

本文档提供了如何使用消息筛选器的基本示例。 使用消息筛选器和数据流模型连接消息块的其他示例，请参阅[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)和[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

## <a name="example"></a>示例

请考虑以下函数， `count_primes`，该图说明了不会筛选传入消息的消息块的基本用法。 消息块将追加到质数[std:: vector](../../standard-library/vector-class.md)对象。 `count_primes`函数向消息块发送多个数字，从消息块接收的输出值并将打印到控制台的质数这些数字。

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer`对象处理所有输入的值; 但是，它需要的是质数的值。 虽然可以编写的应用程序，以便将消息发送方发送仅质数，但不能始终知道消息接收方的要求。

## <a name="example"></a>示例

以下函数， `count_primes_filter`，执行相同的任务`count_primes`函数。 但是，`transformer`对象在此版本中的使用筛选器函数接受的质数的值。 执行的操作的函数仅接收质数;因此，它无需调用`is_prime`函数。

因为`transformer`对象接收仅是质数，`transformer`对象本身可以保留这些质数。 换而言之，`transformer`在此示例中的对象不需要添加到质数`vector`对象。

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer`对象现将处理的是质数的值。 在上一示例中，`transformer`对象处理的所有消息。 因此，前面的示例必须接收相同的发送的消息数。 此示例使用的结果[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数来确定从接收的消息数`transformer`对象。 `send`函数返回**true**的消息缓冲区时接受该消息并**false**时的消息缓冲区会拒绝该消息。 因此，消息缓冲区接受消息的次数匹配质数的计数。

## <a name="example"></a>示例

以下代码显示完整示例。 该示例调用两`count_primes`函数和`count_primes_filter`函数。

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`primes-filter.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc primes filter.cpp**

## <a name="robust-programming"></a>可靠编程

筛选器函数可以是 lambda 函数、 函数指针或函数对象。 每个筛选器函数采用以下形式之一：

```Output
bool (T)
bool (T const &)
```

若要消除不必要的数据复制，使用第二个窗体时您具有传输的值的聚合类型。

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer 类](../../parallel/concrt/reference/transformer-class.md)
