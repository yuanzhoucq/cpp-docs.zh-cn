---
title: "C++ 异常处理 | Microsoft Docs"
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
  - "C++ 异常处理"
  - "Visual C++, 异常处理"
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 异常处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 语言为引发和捕获异常提供内置支持。  使用 C\+\+ 编程时，你几乎总会用到本节所述的内置 C\+\+ 异常支持。  
  
 若要在你的代码中启用 C\+\+ 异常处理，请使用 [\/EHsc](../build/reference/eh-exception-handling-model.md)。  
  
## 本节内容  
 有关 C\+\+ 异常处理的该论述包括：  
  
-   [try、catch 和 throw 语句](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [catch 块如何计算](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [异常和堆栈展开](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [异常规范](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [未处理的 C\+\+ 异常](../cpp/unhandled-cpp-exceptions.md)  
  
-   [混合使用 C（结构化）和 C\+\+ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## 支持较早的 MFC 异常  
 从 4.0 版本开始，MFC 开始使用 C\+\+ 异常处理机制。  虽然鼓励你在新代码中使用 C\+\+ 异常处理，但是 MFC 4.0 和更高版本保留 MFC 早期版本中的宏，以免破坏旧代码。  这些宏和新机制也能结合起来。  有关混合使用宏和 C\+\+ 异常处理以及转换旧代码以使用新机制的信息，请参阅文章[异常：使用 MFC 宏和 C\+\+ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)与[异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  较早的 MFC 异常宏（如果你仍在使用它们）的计算结果为 C\+\+ 异常关键字。  请参阅[异常：3.0 版本中异常宏的修改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。  
  
## 请参阅  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)