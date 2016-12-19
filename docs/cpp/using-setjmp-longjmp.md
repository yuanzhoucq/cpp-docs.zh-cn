---
title: "使用 setjmp/longjmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "longjmp"
  - "setjmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, setjmp/longjmp 函数"
  - "C++ 程序中的 longjmp 函数"
  - "setjmp 函数"
  - "setjmp 函数, C++ 程序"
  - "SETJMP.H"
  - "SETJMPEX.H"
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 setjmp/longjmp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过将 [setjmp](../c-runtime-library/reference/setjmp.md) 和 [longjmp](../c-runtime-library/reference/longjmp.md) 结合使用，可以执行非本地 `goto`。  它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。  
  
> [!CAUTION]
>  但是，由于 `setjmp` 和 `longjmp` 不支持 C\+\+ 对象语义，并且它们可能会阻止局部变量优化从而导致性能降低，因此建议您不要将其用于 C\+\+ 程序。  建议您改用 `try`\/`catch` 构造。  
  
 如果您决定在 C\+\+ 程序中使用 `setjmp`\/`longjmp`，还请包括 SETJMP.H 或 SETJMPEX.H 以确保函数和 C\+\+ 异常处理之间进行正确交互。  如果使用 [\/EH](../build/reference/eh-exception-handling-model.md) 进行编译，则在堆栈展开过程中，将调用本地对象的析构函数。  如果您使用 **\/EHs** 进行编译，并且您的某个函数调用使用 [nothrow](../cpp/nothrow-cpp.md) 的函数，而使用 `nothrow` 的函数调用 `longjmp`，则析构函数可能不会展开，具体取决于优化程序。  
  
 在可移植代码中，当执行调用 `longjmp` 的非本地 `goto` 时，基于框架的对象的正确析构可能是不可靠的。  
  
## 请参阅  
 [混合 C（结构化）和 C\+\+ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)