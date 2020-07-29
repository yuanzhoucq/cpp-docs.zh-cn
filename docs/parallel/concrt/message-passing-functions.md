---
title: 消息传递函数
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 3709e7b5280b96b2b77ec850a06ed15d0e42a7e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194623"
---
# <a name="message-passing-functions"></a>消息传递函数

异步代理库提供了几个函数，使你可以在组件之间传递消息。

这些消息传递函数与各种消息块类型一起使用。 有关并发运行时定义的消息块类型的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="sections"></a><a name="top"></a>个

本主题介绍以下消息传递函数：

- [send 和 asend](#send)

- [接收和 try_receive](#receive)

- [示例](#examples)

## <a name="send-and-asend"></a><a name="send"></a>send 和 asend

[Concurrency：： send](reference/concurrency-namespace-functions.md#send)函数以同步方式将消息发送到指定的目标， [concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函数以异步方式将消息发送到指定的目标。 `send`和函数都 `asend` 一直等待，直到目标指示它最终会接受或拒绝该消息。

`send`函数会等待，直到目标接受或拒绝消息，然后再返回。 `send` **`true`** 如果消息已传递，则函数将返回 **`false`** ; 否则返回。 由于 `send` 函数以同步方式运行，因此该函数将在 `send` 返回前等待目标接收消息。

相反， `asend` 函数不会等到目标接受或拒绝消息，然后再返回。 相反， `asend` **`true`** 如果目标接受消息并最终接收该消息，则该函数将返回。 否则， `asend` **`false`** 将返回以指示目标拒绝消息或推迟有关是否采用消息的决策。

[[顶部](#top)]

## <a name="receive-and-try_receive"></a><a name="receive"></a>接收和 try_receive

[Concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和[concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)函数从给定的源中读取数据。 `receive`函数等待数据变为可用，而 `try_receive` 函数立即返回。

`receive`必须具有数据才能继续时，可使用函数。 `try_receive`如果不一定要阻止当前上下文，或者不必让数据继续运行，请使用函数。

[[顶部](#top)]

## <a name="examples"></a><a name="examples"></a> 示例

有关使用和和函数的示例 `send` `asend` `receive` ，请参阅以下主题：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [如何：向调用和转换器类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [如何：在已完成的任务之间进行选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[顶部](#top)]

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 函数](reference/concurrency-namespace-functions.md#send)<br/>
[asend 函数](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 函数](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函数](reference/concurrency-namespace-functions.md#try_receive)
