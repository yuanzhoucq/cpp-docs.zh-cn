---
title: 如何： 使用过度订阅偏移延迟 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f96a8a27b511c1a93114c32d048043aa9562fe1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392954"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用过度订阅偏移延迟

过度订阅可以提高包含的延迟时间很长的任务的一些应用程序的整体效率。 本主题说明了如何使用过度订阅偏移延迟导致通过网络连接读取数据。

## <a name="example"></a>示例

此示例使用[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)从 HTTP 服务器下载文件。 `http_reader`类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)并使用消息传递来异步读取要下载的 URL 名称。

`http_reader`类使用[concurrency:: task_group](reference/task-group-class.md)类来同时读取每个文件。 每个任务将调用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法替换`_BeginOversubscription`参数设置为`true`启用过度订阅当前上下文中的。 然后，每个任务使用 Microsoft 基础类 (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md)并[CHttpFile](../../mfc/reference/chttpfile-class.md)类，以下载该文件。 最后，调用每个任务`Context::Oversubscribe`与`_BeginOversubscription`参数设置为`false`禁用过度订阅。

启用过度订阅后，运行时将创建要在其中运行任务的一个其他线程。 每个线程可以过度订阅当前上下文，从而创建其他线程。 `http_reader`类使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象来限制应用程序使用的线程数。 代理初始化具有固定数量的令牌值的缓冲区。 对于每个下载操作，该代理令牌值从缓冲区中读取之前该操作将启动，然后将该值返回写入缓冲区在操作完成后。 如果缓冲区为空，则代理会等待下载操作将返回到缓冲区中写入值之一。

下面的示例限制到两倍的可用硬件线程数的同步任务数。 此值是您尝试使用过度订阅时要使用的良好开端。 可以使用，使其满足特定的处理环境，也可以动态更改此值可响应的实际工作负荷。

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

此示例生成了四个处理器的计算机上的以下输出：

```Output
Downloading http://www.adatum.com/...
Downloading http://www.adventure-works.com/...
Downloading http://www.alpineskihouse.com/...
Downloading http://www.cpandl.com/...
Downloading http://www.cohovineyard.com/...
Downloading http://www.cohowinery.com/...
Downloading http://www.cohovineyardandwinery.com/...
Downloading http://www.contoso.com/...
Downloading http://www.consolidatedmessenger.com/...
Downloading http://www.fabrikam.com/...
Downloading http://www.fourthcoffee.com/...
Downloading http://www.graphicdesigninstitute.com/...
Downloading http://www.humongousinsurance.com/...
Downloading http://www.litwareinc.com/...
Downloading http://www.lucernepublishing.com/...
Downloading http://www.margiestravel.com/...
Downloading http://www.northwindtraders.com/...
Downloading http://www.proseware.com/...
Downloading http://www.fineartschool.net...
Downloading http://www.tailspintoys.com/...
Downloaded 1801040 bytes in 3276 ms.
```

当启用过度订阅，因为其他任务运行其他任务等待延迟操作完成时，可以更快地运行该示例。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`download-oversubscription.cpp`，然后运行的以下一项在 Visual Studio 命令提示符窗口中的命令。

**cl.exe /EHsc /MD /D"_AFXDLL"download-oversubscription.cpp**

**cl.exe /EHsc /MT download-oversubscription.cpp**

## <a name="robust-programming"></a>可靠编程

始终禁用过度订阅后不再需要。 请考虑不处理由另一个函数引发的异常的函数。 如果该函数返回之前未禁用过度订阅，任何其他的并行工作也将过度订阅当前上下文。

可以使用*资源获取即初始化*(RAII) 模式，以限制到给定作用域的过度订阅。 RAII 模式下的数据结构是在堆栈上分配的。 该数据结构初始化，或将它创建和销毁或销毁数据结构时释放该资源时获取资源。 RAII 模式可确保在封闭作用域退出之前调用析构函数。 因此，资源会引发异常时或在一个函数包含多个正常管理`return`语句。

下面的示例定义名为结构`scoped_blocking_signal`。 构造函数`scoped_blocking_signal`结构启用过度订阅和析构函数禁用过度订阅。

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

下面的示例修改的正文`download`之前该函数将返回方法，以使用 RAII 来确保，过度订阅将被禁用。 这种技术确保`download`方法不会出现异常。

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>请参阅

[上下文](../../parallel/concrt/contexts.md)<br/>
[Context:: oversubscribe 方法](reference/context-class.md#oversubscribe)

