---
title: 消息传递函数
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143295"
---
# <a name="message-passing-functions"></a>消息传递函数

异步代理库提供了几个函数，使你可以在组件之间传递消息。

这些消息传递函数与各种消息块类型一起使用。 有关并发运行时定义的消息块类型的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="top"></a> 部分

本主题介绍以下消息传递函数：

- [send 和 asend](#send)

- [接收和 try_receive](#receive)

- [示例](#examples)

## <a name="send"></a>send 和 asend

[Concurrency：： send](reference/concurrency-namespace-functions.md#send)函数以同步方式将消息发送到指定的目标， [concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函数以异步方式将消息发送到指定的目标。 `send` 和 `asend` 函数都将等待，直到目标指示它最终会接受或拒绝该消息。

`send` 函数将等待，直到目标接受或拒绝消息，然后再返回。 如果消息传递，则 `send` 函数返回**true** ，否则返回**false** 。 由于 `send` 函数同步工作，因此 `send` 函数会等待目标在消息返回之前接收消息。

相反，在返回之前，`asend` 函数不会等待目标接受或拒绝该消息。 相反，如果目标接受消息并最终接收该消息，则 `asend` 函数将返回**true** 。 否则，`asend` 将返回**false** ，以指示目标拒绝消息或推迟有关是否采用消息的决策。

[[返回页首](#top)]

## <a name="receive"></a>接收和 try_receive

[Concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和[concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)函数从给定的源中读取数据。 `receive` 函数等待数据变得可用，而 `try_receive` 函数立即返回。

必须具有数据才能继续时，可使用 `receive` 函数。 如果不一定要阻止当前上下文，或者不必让数据继续运行，请使用 `try_receive` 函数。

[[返回页首](#top)]

## <a name="examples"></a>示例

有关使用 `send` 和 `asend`以及 `receive` 函数的示例，请参阅以下主题：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [如何：为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [如何：在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[返回页首](#top)]

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 函数](reference/concurrency-namespace-functions.md#send)<br/>
[asend 函数](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 函数](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函数](reference/concurrency-namespace-functions.md#try_receive)
