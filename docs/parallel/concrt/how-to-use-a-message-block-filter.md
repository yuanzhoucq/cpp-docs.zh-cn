---
title: "如何：使用消息块筛选器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息块筛选器，使用 [并发运行时]"
  - "使用消息块筛选器 [并发运行时]"
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用消息块筛选器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档演示如何使用筛选器函数使异步消息块来接受或拒绝该消息的负载根据一条消息。  
  
 在创建消息块对象时如 [concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md), 、 [concurrency:: call](../../parallel/concrt/reference/call-class.md), ，或 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md), ，您可以提供 *filter 函数* ，它确定消息块是接受还是拒绝一条消息。 筛选器函数是保证的消息块只接收特定值的有用方式。  
  
 筛选器函数非常重要，因为它们使你可以连接消息块来形成 *数据流网络*。 在数据流网络中，消息块处理符合特定条件的那些消息通过控制数据的流。 比较而言，控制流模型，其中通过使用条件语句、 循环，如控制结构调整的数据流，依此类推。  
  
 本文档提供了如何使用消息筛选器的基本示例。 使用消息筛选器和数据流模型连接消息块的其他示例，请参阅 [演练︰ 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) 和 [演练︰ 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
## <a name="example"></a>示例  
 考虑以下函数 `count_primes`, ，其中说明了基本的用法不会筛选传入消息的消息块。 消息块将追加到质数 [std:: vector](../../standard-library/vector-class.md) 对象。  `count_primes` 函数将几个号码发送到消息块，从消息块接收输出值并且将打印到控制台的质数这些数字。  
  
 [!CODE [concrt-primes-filter#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-primes-filter#1)]  
  
  `transformer` 处理所有输入的值的对象; 但是，它要求只有质数的值。 虽然可以编写应用程序，以便消息发件人只发送质数，但不能始终了解消息接收方的要求。  
  
## <a name="example"></a>示例  
 为以下函数， `count_primes_filter`, ，执行相同的任务作为 `count_primes` 函数。 但是， `transformer` 对象在此版本中的使用筛选器函数只接受这些值质数。 执行该操作的函数只接收质数;因此，它不必调用 `is_prime` 函数。  
  
 因为 `transformer` 对象只接收质数， `transformer` 对象本身可以保留这些质数。 换而言之， `transformer` 在此示例中的对象不需要添加到质数 `vector` 对象。  
  
 [!CODE [concrt-primes-filter#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-primes-filter#2)]  
  
  `transformer` 对象现将处理只是质数的那些值。 在上一示例中， `transformer` 对象处理的所有消息。 因此，前面的示例必须接收它将发送的邮件数相同。 此示例中使用的结果 [concurrency:: send](../Topic/send%20Function.md) 函数来确定多少条消息以接收来自 `transformer` 对象。  `send` 函数返回 `true` 消息缓冲区时接受的消息和 `false` 消息缓冲区时拒绝该消息。 因此，消息缓冲区接受消息的次数与相匹配的质数的计数。  
  
## <a name="example"></a>示例  
 以下代码显示完整示例。 该示例同时调用 `count_primes` 函数和 `count_primes_filter` 函数。  
  
 [!CODE [concrt-primes-filter#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-primes-filter#3)]  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到名为 `primes-filter.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc primes filter.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 Filter 函数可以是 lambda 函数、 函数指针或函数对象。 每个筛选器函数采用以下形式之一︰  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 若要消除不必要的情况下复制数据，请使用第二个窗体时您具有传输的值的聚合类型。  
  
## <a name="see-also"></a>另请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [演练︰ 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [演练︰ 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [transformer 类](../../parallel/concrt/reference/transformer-class.md)
