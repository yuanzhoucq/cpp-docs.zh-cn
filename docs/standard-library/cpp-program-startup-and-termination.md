---
title: "C++ 程序启动和终止 | Microsoft Docs"
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
  - "控制文本流"
  - "函数 Main 过程"
  - "主函数, 程序启动"
  - "标准 C++ 库, 程序启动和终止"
  - "启动代码, 和 C++ 程序终止"
  - "终止执行"
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 程序启动和终止
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用 . C\+\+ 程序执行与 C. 执行程序在程序启动并在程序停止操作，并概述一些示。  
  
 在目标环境中调用函数 `main`之前，并且，然后再存储所有常量值后您在具有静态的持续时间对应的所有对象指定，则程序执行此静态对象的剩余的构造函数。  执行顺序不指定在翻译单元之间，但是，可以假定，但这些对象供 [iostreams](../standard-library/iostreams-conventions.md) 正确地初始化这些静态构造函数。  这些控件文本是流：  
  
-   [cin](../Topic/cin.md) \- 标准输入的。  
  
-   [cout](../Topic/cout.md) \- 标准输出。  
  
-   [cerr](../Topic/cerr.md) \- 未缓冲的标准错误输出。  
  
-   [障碍物](../Topic/clog.md) \(缓存的标准错误输出。  
  
 可以为静态对象也使用。在程序停止时调用的，析构函数中的这些对象。  
  
 C，返回从 `main` 或调用 `exit` 调用任何函数注册与注册表以反向顺序的 `atexit`。  注册从引发的异常的函数调用 `terminate`。  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)