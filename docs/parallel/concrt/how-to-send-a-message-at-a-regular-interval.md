---
title: "如何： 定期发送消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c5c10ba2a1fee400ef99799c7c83a3bdcacd084f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：定期发送消息
此示例演示如何使用并发::[计时器类](../../parallel/concrt/reference/timer-class.md)定期发送消息。  
  
## <a name="example"></a>示例  

 下面的示例使用`timer`期间较长的操作报告进度的对象。 此示例的链接`timer`对象传递给[concurrency:: call](../../parallel/concrt/reference/call-class.md)对象。 `call`对象将进度指示器向控制台输出定期时间间隔。 [Concurrency::timer::start](reference/timer-class.md#start)方法在单独的上下文中运行计时器。 `perform_lengthy_operation`函数调用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数对主上下文，以模拟耗时的操作。  

  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 该示例产生下面的示例输出：  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`report-progress.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc report-progress.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)
