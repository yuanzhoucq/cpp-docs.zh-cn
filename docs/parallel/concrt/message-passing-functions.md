---
title: 消息传递函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b7a7afb25d46fa3b521353c4577fbed66e69fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436983"
---
# <a name="message-passing-functions"></a>消息传递函数

异步代理库提供了几个函数，可将各组件之间的消息传递。

这些消息传递函数用于各种消息块类型。 有关由并发运行时定义的消息块类型的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

##  <a name="top"></a> 部分

本主题介绍了以下消息传递函数：

- [send 和 asend](#send)

- [接收和 try_receive](#receive)

- [示例](#examples)

##  <a name="send"></a> send 和 asend

[Concurrency:: send](reference/concurrency-namespace-functions.md#send)函数将消息同步发送到指定的目标和[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函数将消息异步发送到指定的目标。 同时`send`和`asend`函数等待，直到目标指示它最终将接受或拒绝该消息。

`send`函数等待，直到目标接受或拒绝该消息才会返回。 `send`函数返回`true`如果消息传递和`false`否则为。 因为`send`同步，工作函数`send`函数等待要接收的消息，在返回之前的目标。

相反，`asend`函数不会等待要接受或拒绝该消息，在返回之前的目标。 相反，`asend`函数返回`true`如果目标接受消息，并且最终将采用它。 否则为`asend`返回`false`以指示目标是拒绝了消息或推迟是否使该消息的决策。

[[返回页首](#top)]

##  <a name="receive"></a> 接收和 try_receive

[Concurrency:: receive](reference/concurrency-namespace-functions.md#receive)并[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)函数从给定源读取数据。 `receive`函数等待数据变得可用，而`try_receive`函数将立即返回。

使用`receive`函数时必须具有数据才能继续。 使用`try_receive`函数如果您不能阻止当前上下文或不需要具有继续的数据。

[[返回页首](#top)]

##  <a name="examples"></a>示例

有关示例，请使用`send`并`asend`，和`receive`函数，请参阅以下主题：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [如何：为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [如何：在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 函数](reference/concurrency-namespace-functions.md#send)<br/>
[asend 函数](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 函数](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函数](reference/concurrency-namespace-functions.md#try_receive)

