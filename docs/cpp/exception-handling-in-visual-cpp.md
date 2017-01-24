---
title: "Visual C++ 中的异常处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "try-catch 关键字 [C++], 异常处理"
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 中的异常处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

异常是一个可能超出程序的控制范围的错误条件，它会阻止程序继续沿其常规执行路径执行。  某些操作（包括对象创建、文件输入\/输出以及从其他模块中进行的函数调用）都可能是异常的来源，设置在你的程序正常运行时也是如此。  可靠代码可预见并处理异常。  
  
 若要检测单个程序或模块内的逻辑错误，请使用断言而不是异常（请参阅[使用断言](../Topic/C-C++%20Assertions.md)）。  
  
 Visual C\+\+ 支持三种异常处理：  
  
-   [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)  
  
     对于大多数 C\+\+ 程序，你应使用类型安全的 C\+\+ 异常处理，该处理可确保在堆栈展开过程中调用对象析构函数。  
  
-   [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)  
  
     Windows 提供其自己的称为 SEH 的异常机制。  建议不要将该机制用于 C\+\+ 或 MFC 编程。  仅在非 MFC C 程序中使用 SEH。  
  
-   [MFC 异常](../mfc/exception-handling-in-mfc.md)  
  
     自 3.0 版开始，MFC 已使用 C\+\+ 异常，但仍支持其较早的异常处理宏，这些宏在形式上与 C\+\+ 异常类似。  虽然建议不要将这些宏用于新编程，但仍可使用它们实现向后兼容。  在已使用宏的程序中，你也可以随意使用 C\+\+ 异常。  从 Visual C\+\+ 2.0 版开始，在预处理期间，宏的计算结果为 C\+\+ 语言的 Visual C\+\+ 实现中定义的异常处理关键字。  当你开始使用 C\+\+ 异常时，可以保留现有异常宏。  
  
 使用 [\/EH](../build/reference/eh-exception-handling-model.md) 编译器选项指定要在项目中使用的异常处理的类型；C\+\+ 异常处理是默认值。  不要混合错误处理机制；例如，不要将 C\+\+ 异常用于结构化异常处理。  使用 C\+\+ 异常处理可以使你的代码更具可移植性，并且它使你可以处理任何类型的异常。  有关结构化异常处理的缺点的详细信息，请参阅[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)。  有关将 MFC 宏和 C\+\+ 异常组合的建议，请参阅[异常：使用 MFC 宏和 C\+\+ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。  
  
 有关在 CLR 应用程序中处理异常的信息，请参阅 [异常处理](../windows/exception-handling-cpp-component-extensions.md)。  
  
 有关 x64 处理器上的异常处理的信息，请参阅[异常处理 \(x64\)](../build/exception-handling-x64.md)。  
  
## 请参阅  
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)