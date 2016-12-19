---
title: "如何：定期发送消息 | Microsoft Docs"
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
  - "timer 类, 示例"
  - "定期发送消息 [并发运行时]"
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定期发送消息
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此示例演示如何使用并发::[timer 类](../../parallel/concrt/reference/timer-class.md) 定期发送消息。  
  
## <a name="example"></a>示例  
 下面的示例使用 `timer` 冗长操作过程中报告进度的对象。 此示例的链接 `timer` 对象传递给 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 对象。  `call` 对象将进度指示器向控制台输出定期时间间隔。  [Concurrency::timer::start](../Topic/timer::start%20Method.md) 方法在单独的上下文中运行计时器。  `perform_lengthy_operation` 函数调用 [concurrency:: wait](../Topic/wait%20Function.md) 函数对主上下文以模拟耗时操作。  
  
 [!CODE [concrt-report-progress#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-report-progress#1)]  
  
 该示例产生下面的示例输出︰  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到名为 `report-progress.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc report-progress.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)
