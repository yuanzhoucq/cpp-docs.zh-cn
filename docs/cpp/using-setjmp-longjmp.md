---
title: 使用 setjmp-longjmp |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68cd13304e73282735ad1227510b289b19caed8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939762"
---
# <a name="using-setjmplongjmp"></a>使用 setjmp/longjmp
当[setjmp](../c-runtime-library/reference/setjmp.md)并[longjmp](../c-runtime-library/reference/longjmp.md)是一起使用时，它们提供一种方法来执行非本地**goto**。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。  
  
> [!CAUTION]
>  但是，由于 `setjmp` 和 `longjmp` 不支持 C++ 对象语义，并且它们可能会阻止局部变量优化从而导致性能降低，因此建议您不要将其用于 C++ 程序。 我们建议你使用**尝试**/**捕获**构造。  
  
 如果你决定使用`setjmp` / `longjmp`在 C++ 程序中，还包括\<setjmp.h > 或\<setjmpex.h > 若要确保函数和 C++ 异常处理之间进行正确交互。 如果您使用[/EH](../build/reference/eh-exception-handling-model.md)进行编译，本地对象的析构函数调用在堆栈展开过程。 如果您使用 **/EHs**进行编译，并且使用的函数在函数调用之一[nothrow](../cpp/nothrow-cpp.md)使用的函数**nothrow**调用`longjmp`，则析构函数可能不会展开，具体取决于优化程序。  
  
 在可移植代码中，当非本地**goto**的调用`longjmp`执行时，基于框架的对象的正确析构可能是不可靠。  
  
## <a name="see-also"></a>请参阅  
 [混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)