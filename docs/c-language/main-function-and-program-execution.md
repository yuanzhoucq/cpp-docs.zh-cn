---
title: "main 函数和程序执行 | Microsoft Docs"
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
  - "入口点, 程序"
  - "主函数"
  - "主函数, 程序执行"
  - "程序启动 [C++]"
  - "程序 [C++], 终止"
  - "启动代码, 主函数"
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# main 函数和程序执行
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个 C 程序都有必须命名为 **main** 的主函数。  如果您的代码遵循 Unicode 编程模型，则可以使用 **main** 的宽字符版本 **wmain**。  **main** 函数充当程序执行的起点。  它通常通过将调用定向到程序中的其他函数来控制程序执行。  尽管程序可以因为各种原因在程序的其他点上终止，但它通常在 **main** 的结尾处停止执行。  有时，当检测到某一错误时，您可能希望强制终止程序。  为此，请使用**exit** 函数。  有关使用 [exit](../c-runtime-library/reference/exit-exit-exit.md) 函数的信息和示例，请参阅《运行时库参考》。  
  
## 语法  
  
```  
main( int argc, char *argv[ ], char *envp[ ] )  
```  
  
## 备注  
 源程序中的函数执行一个或多个特定任务。  **main** 参数可调用这些函数来执行其各自的任务。  当 **main** 调用另一函数时，它会将执行控制权交给该函数，以便执行在该函数中的第一个语句处开始。  当执行 `return` 语句或到达某个函数的末尾时，该函数会将控制权返回到 **main**。  
  
 您可以声明任何函数（包括 **main**）以包含参数。  术语“参数”或“形参”指的是接收传递到函数的值的标识符。  有关将实参传递到形参的详细信息，请参阅[参数](../c-language/parameters.md)。  当一个函数调用另一个函数时，被调用的函数将从实施调用的函数接收其参数的值。  这些值称为“实参”。可以将形参声明为 **main**，以便让它使用以下格式从命令行接收实参：  
  
 当您要将信息传递给 **main** 函数时，尽管 C 编译器不需要这些名称，但上述参数在传统上命名为 `argc` 和 `argv`。  `argc` 和 `argv` 的类型由 C 语言定义。  传统上，如果第三个参数传递给 **main**，该参数将命名为 `envp`。  本节后面的示例演示如何使用这三个形参访问命令行实参。  以下各节说明了这些参数。  
  
 有关 **main** 的宽字符版本的说明，请参阅[使用 wmain](../c-language/using-wmain.md)。  
  
## 请参阅  
 [main：程序启动](../cpp/main-program-startup.md)