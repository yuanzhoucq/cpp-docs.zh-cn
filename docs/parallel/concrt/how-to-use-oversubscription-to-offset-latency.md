---
title: 如何：使用过度订阅偏移延迟
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: f5d48b68d03adc25cd5f87122591b52e37da700a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219594"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用过度订阅偏移延迟

过度订阅可以提高包含具有较高延迟的任务的某些应用程序的总体效率。 本主题说明如何使用过度订阅来抵消通过从网络连接读取数据而导致的延迟。

## <a name="example"></a>示例

此示例使用[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)从 HTTP 服务器下载文件。 `http_reader`类派生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md) ，并使用消息传递异步读取要下载的 URL 名称。

`http_reader`类使用[concurrency：： task_group](reference/task-group-class.md)类并发读取每个文件。 每个任务都调用[concurrency：： Context：：未订阅](reference/context-class.md#oversubscribe)的方法，并将 `_BeginOversubscription` 参数设置为， **`true`** 以在当前上下文中启用过度订阅。 然后，每个任务使用 Microsoft 基础类（MFC） [CInternetSession](../../mfc/reference/cinternetsession-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md)类下载该文件。 最后，每个任务都调用 `Context::Oversubscribe` 并将 `_BeginOversubscription` 参数设置为 **`false`** 以禁用过度订阅。

启用过度订阅后，运行时将创建一个要在其中运行任务的其他线程。 其中每个线程还可以订阅当前上下文，从而创建其他线程。 `http_reader`类使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)对象来限制应用程序使用的线程数。 代理使用固定数量的标记值初始化缓冲区。 对于每个下载操作，代理会在操作开始之前从缓冲区读取一个令牌值，然后在操作完成后将该值写入缓冲区。 当缓冲区为空时，代理会等待其中一个下载操作将值写入缓冲区。

下面的示例将同时执行的任务数限制为可用硬件线程数的两倍。 此值是在您试验过度订阅时使用的良好起点。 您可以使用适合特定处理环境的值，也可以动态更改此值以响应实际工作负荷。

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

此示例在具有四个处理器的计算机上产生以下输出：

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

启用了超额订阅后，可以更快地运行此示例，因为其他任务会在其他任务等待潜在操作完成时运行。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为的文件中， `download-oversubscription.cpp` 然后在**Visual Studio 命令提示符**窗口中运行以下命令之一。

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>可靠编程

不再需要过度订阅后，始终将其禁用。 请考虑一个不处理由另一个函数引发的异常的函数。 如果在该函数返回之前未禁用过度订阅，则任何其他并行工作也会在当前上下文中过度订阅。

可以使用*资源采集为初始化*（RAII）模式来限制对给定范围的过度订阅。 在 RAII 模式下，在堆栈上分配数据结构。 此数据结构在创建时初始化或获取资源，并在数据结构销毁时销毁或释放该资源。 RAII 模式可确保在封闭范围退出之前调用析构函数。 因此，当引发异常或函数包含多个语句时，会正确管理资源 **`return`** 。

下面的示例定义了一个名为的结构 `scoped_blocking_signal` 。 结构的构造函数 `scoped_blocking_signal` 启用过度订阅，析构函数禁用过度订阅。

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

下面的示例修改方法的主体 `download` ，以使用 RAII，以确保在函数返回之前禁用超额订阅。 此方法可确保 `download` 方法为异常安全方法。

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>另请参阅

[上下文](../../parallel/concrt/contexts.md)<br/>
[Context::Oversubscribe 方法](reference/context-class.md#oversubscribe)
