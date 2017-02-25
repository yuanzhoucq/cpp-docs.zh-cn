---
title: "如何：使用过度订阅偏移延迟 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "过度订阅, 使用 [并发运行时]"
  - "使用过度订阅 [并发运行时]"
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：使用过度订阅偏移延迟
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对于一些所含任务存在大量延迟的应用程序，过度订阅可以提高这些应用程序的整体效率。  本主题阐释如何使用过度订阅来抵消通过网络连接读取数据导致的延迟。  
  
## 示例  
 此示例使用[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)从 HTTP 服务器下载文件。  `http_reader` 类从 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 派生，并使用消息传递来异步读取要下载的 URL 名称。  
  
 `http_reader` 类使用 [concurrency::task\_group](../Topic/task_group%20Class.md) 类来同时读取每个文件。  每个任务都调用 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法（其 `_BeginOversubscription` 参数设置为 `true`），以便在当前上下文中启用过度订阅。  然后，每个任务使用 Microsoft 基础类 \(MFC\) [CInternetSession](../../mfc/reference/cinternetsession-class.md) 和 [CHttpFile](../../mfc/reference/chttpfile-class.md) 类来下载文件。  最后，每个任务在 `_BeginOversubscription` 参数设置为 `false` 的情况下调用 `Context::Oversubscribe` 以禁用过度订阅。  
  
 启用过度订阅后，运行时会创建一个在其中运行任务的附加线程。  此外，每个线程都可以过度订阅当前上下文，从而创建附加线程。  `http_reader` 类使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 对象来限制应用程序所使用的线程数。  代理将使用固定数目的标记值来初始化缓冲区。  对于每个下载操作，代理会在操作开始前读取缓冲区中的一个标记值，然后在操作完成后将该值写回到缓冲区中。  当缓冲区为空时，代理会等待其中的某个下载操作将值写回到缓冲区。  
  
 下面的示例将同步任务数限制为可用硬件线程数的两倍。  在试验过度订阅时，这个值很适合于初次使用。  可以使用适合特定处理环境的值，也可以动态更改此值以响应实际工作负载。  
  
 [!CODE [concrt-download-oversubscription#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-download-oversubscription#1)]  
  
 此示例将在具有四个处理器的计算机上产生以下输出：  
  
  **下载中 http:\/\/www.adatum.com\/...**  
**下载中 http:\/\/www.adventure\-works.com\/...**  
**下载中 http:\/\/www.alpineskihouse.com\/...**  
**下载中 http:\/\/www.cpandl.com\/...**  
**下载中 http:\/\/www.cohovineyard.com\/...**  
**下载中 http:\/\/www.cohowinery.com\/...**  
**下载中 http:\/\/www.cohovineyardandwinery.com\/...**  
**下载中http:\/\/www.contoso.com\/...**  
**下载中 http:\/\/www.consolidatedmessenger.com\/...**  
**下载中 http:\/\/www.fabrikam.com\/...**  
**下载中 http:\/\/www.fourthcoffee.com\/...**  
**下载中 http:\/\/www.graphicdesigninstitute.com\/...**  
**下载中 http:\/\/www.humongousinsurance.com\/...**  
**下载中 http:\/\/www.litwareinc.com\/...**  
**下载中 http:\/\/www.lucernepublishing.com\/...**  
**下载中 http:\/\/www.margiestravel.com\/...**  
**下载中 http:\/\/www.northwindtraders.com\/...**  
**下载中 http:\/\/www.proseware.com\/...**  
**下载中 http:\/\/www.fineartschool.net...**  
**下载中 http:\/\/www.tailspintoys.com\/...**  
**在 3276 毫秒内下载了1801040 字节。** 当启用过度订阅时，此示例运行的速度会更快，这是因为当其他任务等待延迟操作完成时，将会运行附加任务。  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio项目中或一个名为`download-oversubscription.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行下列命令之一。  
  
 **cl.exe \/EHsc \/MD \/D "\_AFXDLL" download\-oversubscription.cpp**  
  
 **cl.exe \/EHsc \/MT download\-oversubscription.cpp**  
  
## 可靠编程  
 当不再需要过度订阅时，始终禁用过度订阅。  考虑一个不处理由另一个函数引发的异常的函数。  如果在此函数返回之前不禁用过度订阅，则任何附加的并行工作也将过度订阅当前上下文。  
  
 可以使用“获取资源即初始化”\(RAII\) 模式，将过度订阅限制为某个给定范围。  在 RAII 模式下，将在堆栈上分配一个数据结构。  该数据结构在创建时将会初始化或获取一个资源，而且该数据结构在销毁时将会销毁或释放该资源。  RAII 模式可确保在封闭范围退出之前调用析构函数。  因此，在引发异常时或在函数包含多个 `return` 语句时，将可以正确地管理资源。  
  
 下面的示例定义了一个名为 `scoped_blocking_signal` 的结构。  `scoped_blocking_signal` 结构的构造函数启用过度订阅，而析构函数禁用过度订阅。  
  
 [!CODE [concrt-download-oversubscription#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-download-oversubscription#2)]  
  
 下面的示例修改 `download` 方法的主体以使用 RAII 来确保在函数返回之前禁用过度订阅。  这项技术可确保 `download` 方法不会出现异常。  
  
 [!CODE [concrt-download-oversubscription#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-download-oversubscription#3)]  
  
## 请参阅  
 [上下文](../../parallel/concrt/contexts.md)   
 [Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)