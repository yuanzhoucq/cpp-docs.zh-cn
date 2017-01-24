---
title: "如何：为 call 和 transformer 类提供工作函数 | Microsoft Docs"
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
  - "call 类, 示例"
  - "使用 transformer 类 [并发运行时]"
  - "使用 call 类 [并发运行时]"
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：为 call 和 transformer 类提供工作函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题阐释几种用于向 [concurrency::call](../../parallel/concrt/reference/call-class.md) 和 [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 类提供工作函数的方式。  
  
 第一个示例说明如何将 lambda 表达式传递给 `call` 对象。  第二个示例说明如何将函数对象传递给 `call` 对象。  第三个示例说明如何将类方法绑定到 `call` 对象。  
  
 出于演示的目的，本主题中的每个示例都使用 `call` 类。  有关使用 `transformer` 类的示例，请参见[如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
## 示例  
 下面的示例说明使用 `call` 类的常见方法。  此示例将 lambda 函数传递给 `call` 构造函数。  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **13为169的平方根。**   
## 示例  
 下面的示例与上一示例类似，只不过下面的示例将 `call` 类与函数对象 \(functor\) 一起使用。  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## 示例  
 下面的示例与上一示例类似，只不过它使用 [std::bind1st](../Topic/bind1st%20Function.md) 和 [std::mem\_fun](../Topic/mem_fun%20Function.md) 函数将 `call` 对象绑定到类方法。  
  
 如果必须将 `call` 或 `transformer` 对象绑定到特定的类方法而不是函数调用运算符 `operator()`，请使用此技术。  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 也可以将 `bind1st` 函数的结果分配给 [std::function](../../standard-library/function-class.md) 对象或使用 `auto` 关键字，如以下示例所示。  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio项目中或一个名为 `call.cpp` 的文件中，然后在Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc call.cpp**  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [call 类](../../parallel/concrt/reference/call-class.md)   
 [transformer 类](../../parallel/concrt/reference/transformer-class.md)