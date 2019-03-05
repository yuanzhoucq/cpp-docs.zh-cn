---
title: 如何：在固定时间间隔发送一条消息
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: 0bf5f93e2a570761874232a88a23289e59e58d94
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257613"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：在固定时间间隔发送一条消息

此示例演示如何使用并发::[timer 类](../../parallel/concrt/reference/timer-class.md)定期发送一条消息。

## <a name="example"></a>示例

下面的示例使用`timer`耗时较长操作期间报告进度的对象。 此示例的链接`timer`对象传递给[concurrency:: call](../../parallel/concrt/reference/call-class.md)对象。 `call`对象一定的时间间隔将输出到控制台的进度指示器。 [Concurrency::timer::start](reference/timer-class.md#start)方法在单独的上下文中运行计时器。 `perform_lengthy_operation`函数调用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数对主上下文以模拟耗时操作。

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

此示例产生下面的示例输出：

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`report-progress.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc report-progress.cpp**

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
