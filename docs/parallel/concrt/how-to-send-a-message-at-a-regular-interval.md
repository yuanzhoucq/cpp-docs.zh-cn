---
title: 如何：定期发送消息
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142467"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：定期发送消息

此示例演示如何使用 concurrency：：[timer 类](../../parallel/concrt/reference/timer-class.md)定期发送消息。

## <a name="example"></a>示例

下面的示例使用 `timer` 对象在长时间的操作过程中报告进度。 此示例将 `timer` 对象链接到[concurrency：： call](../../parallel/concrt/reference/call-class.md)对象。 `call` 对象定期将进度指示器打印到控制台。 [Concurrency：： timer：： start](reference/timer-class.md#start)方法在单独的上下文中运行计时器。 `perform_lengthy_operation` 函数对主上下文调用[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函数来模拟耗时的操作。

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

此示例将生成以下示例输出：

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `report-progress.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc report-progress**

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
