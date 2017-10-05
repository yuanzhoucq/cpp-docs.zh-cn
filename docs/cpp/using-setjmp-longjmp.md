---
title: "使用 setjmp longjmp |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- longjmp
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- SETJMPEX.H
- longjmp function in C++ programs
- SETJMP.H
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 356924c0a93f6d9d21bb417f84836385491b2144
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="using-setjmplongjmp"></a>使用 setjmp/longjmp
当[setjmp](../c-runtime-library/reference/setjmp.md)和[longjmp](../c-runtime-library/reference/longjmp.md)是一起使用时，它们提供一种执行非本地`goto`。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。  
  
> [!CAUTION]
>  但是，由于 `setjmp` 和 `longjmp` 不支持 C++ 对象语义，并且它们可能会阻止局部变量优化从而导致性能降低，因此建议您不要将其用于 C++ 程序。 我们建议你使用`try` / `catch`构造。  
  
 如果你决定使用`setjmp` / `longjmp`在 c + + 程序中，还包括 SETJMP。H 或 SETJMPEX。若要确保函数和 c + + 异常处理之间进行正确交互的 H。 如果你使用[/EH](../build/reference/eh-exception-handling-model.md)进行编译时，本地对象的析构函数调用在堆栈展开过程。 如果你使用**/EHs**进行编译，并且你使用的函数的函数调用之一[nothrow](../cpp/nothrow-cpp.md)和使用的函数`nothrow`调用`longjmp`，则析构函数展开可能不会发生，具体取决于优化器。  
  
 在可移植代码中，当执行调用 `goto` 的非本地 `longjmp` 时，基于框架的对象的正确析构可能是不可靠的。  
  
## <a name="see-also"></a>另请参阅  
 [混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)
