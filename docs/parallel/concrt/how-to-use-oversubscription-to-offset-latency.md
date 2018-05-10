---
title: 如何： 使用过度订阅抵消延迟 |Microsoft 文档
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
ms.openlocfilehash: 0c27864d040d0b6ce7b36087cff85ed750aa7ed2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用过度订阅偏移延迟
过度订阅可提高对某些包含很长的延迟的任务的应用程序的整体效率。 本主题演示如何使用过度订阅抵消延迟所致通过网络连接读取数据。  
  
## <a name="example"></a>示例  
 此示例使用[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)从 HTTP 服务器下载文件。 `http_reader`类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)并使用消息传递来异步读取要下载的 URL 名称。  
  
 `http_reader`类使用[concurrency:: task_group](reference/task-group-class.md)类来同时读取每个文件。 每个任务都调用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法替换`_BeginOversubscription`参数设置为`true`以便启用过度订阅当前上下文中的。 每个任务，然后使用 Microsoft 基础类 (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md)类来下载文件。 最后，每个任务调用`Context::Oversubscribe`与`_BeginOversubscription`参数设置为`false`禁用过度订阅。  
  
 启用过度订阅后，运行时将创建一个要在其中运行任务的其他线程。 每个这些线程可以过度订阅当前上下文，从而创建其他线程。 `http_reader`类使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象来限制的应用程序使用的线程数。 代理初始化具有固定数量的标记值的缓冲区。 对于每个下载操作中，代理令牌值从缓冲区中读取操作开始前，然后将该值返回写入缓冲区在操作完成后。 如果缓冲区为空，则代理会等待下载操作将返回到缓冲区写入的值之一。  
  
 下面的示例限制为可用硬件线程数的两倍的同步任务数。 此值为使用过度订阅进行试验时要使用的良好开端。 你可以使用一个值，适合特定处理环境或动态更改此值可响应的实际工作负荷。  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 该示例产生下面的输出具有四个处理器的计算机上：  
  
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
  
 因为其他任务运行其他任务等待延迟操作完成时启用过度订阅时，该示例可以更快地运行。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`download-oversubscription.cpp`，然后运行以下命令之一在 Visual Studio 命令提示符窗口中。  
  
 **cl.exe /EHsc /MD /D"_AFXDLL"download-oversubscription.cpp**  
  
 **cl.exe /EHsc /MT download-oversubscription.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 后不再需要将始终禁用过度订阅。 请考虑不处理由另一个函数引发的异常的函数。 如果函数返回前未禁用过度订阅，则任何其他并行工作也将过度订阅当前上下文。  
  
 你可以使用*获取资源即初始化*(RAII) 模式，以限制为某个给定范围的过度订阅。 下 RAII 模式，在堆栈上分配一种数据结构。 该数据结构初始化，或在创建和销毁或销毁数据结构时释放该资源时，获取一个资源。 RAII 模式可确保在封闭作用域退出之前被调用的析构函数。 因此，资源会引发异常时或当函数包含多个正常管理`return`语句。  
  
 下面的示例定义一个名为`scoped_blocking_signal`。 构造函数`scoped_blocking_signal`结构启用过度订阅和析构函数禁用过度订阅。  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 下面的示例修改的正文`download`方法以使用 RAII 来确保，过度订阅已禁用函数返回前。 此方法可确保`download`方法是异常安全的。  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [上下文](../../parallel/concrt/contexts.md)   
 [Context:: oversubscribe 方法](reference/context-class.md#oversubscribe)


