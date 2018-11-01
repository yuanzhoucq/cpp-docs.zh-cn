---
title: 如何：实现各种制造者-使用者模式
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 1c543e2c80ff9edea417fe8c1254bf9aa5aa37fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658284"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>如何：实现各种制造者-使用者模式

本主题介绍如何在你的应用程序中实现制造者-使用者模式。 在此模式下，制造者向消息块发送消息，使用者从该块读取消息。

本主题演示了两种方案。 在第一个方案中，使用者必须接收制造者发送每条消息。 在第二个方案中，使用者会定期轮询数据，并因此不需要接收每条消息。

本主题中的这两个示例使用代理、 消息块和消息传递函数来传输消息创建方向使用者。 生成者代理使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数来将消息写入[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)对象。 使用使用者代理[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数从中读取消息[concurrency::ISource](../../parallel/concrt/reference/isource-class.md)对象。 这两个代理保存 sentinel 值来协调处理结束。

有关异步代理的详细信息，请参阅[异步代理](../../parallel/concrt/asynchronous-agents.md)。 有关消息块和消息传递函数的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)并[消息传递函数](../../parallel/concrt/message-passing-functions.md)。

## <a name="example"></a>示例

在此示例中，生成者代理将一系列数字发送到使用者代理。 使用者接收其中每个数字，并计算其平均值。 应用程序写入到控制台的平均值。

此示例使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象，以允许生成者能够将队列消息。 `unbounded_buffer`类实现`ITarget`和`ISource`以便制造者和使用者可以发送和接收消息从一个共享缓冲区。 `send`和`receive`函数协调传播给使用者从生成者数据的任务。

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

本示例生成以下输出。

```Output
The average is 50.
```

## <a name="example"></a>示例

在此示例中，生成者代理将一系列的股票报价发送到使用者代理。 使用者代理定期读取当前报价，并将其打印到控制台。

此示例类似于前一个，只不过它使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)对象，以允许生成者与使用者共享一条消息。 如前面的示例中所示`overwrite_buffer`类实现`ITarget`和`ISource`，以便生成者和使用者可以作用于共享的消息缓冲区。

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

此示例生成下面的示例输出。

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

与不同的是与`unbounded_buffer`对象，`receive`函数不会删除从消息`overwrite_buffer`对象。 如果使用者从消息缓冲区中读取多个时间之前生成者将覆盖该消息，接收方获得每次都相同的消息。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`producer-consumer.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 制造者-consumer.cpp**

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
