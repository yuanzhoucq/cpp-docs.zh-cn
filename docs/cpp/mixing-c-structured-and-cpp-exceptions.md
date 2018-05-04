---
title: 混合使用 C （结构化） 和 C++ 异常 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e9544e10ff0af41c0ff08fa51293c67c9977f2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合使用 C（结构化）和 C++ 异常
若要编写可移植性更高的代码，建议不要在 C++ 程序中使用结构化异常处理。 但是，有时可能希望使用编译 **/EHa**和混合使用结构化的异常和 C++ 源代码，并且需要用于处理这两种异常的一些设备。 由于结构化的异常处理程序没有对象或类型化的异常的概念，它无法处理 C++ 代码; 引发的异常但是，C++**捕获**处理程序可以处理结构化的异常。 为此类中，C++ 异常处理语法 (**重**， `throw`，**捕获**) 不接受 C 编译器，但结构化的异常处理语法 (`__try`， `__except`， `__finally`)C++ 编译器支持。  
  
 请参阅[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)有关处理结构化的异常作为 C++ 异常信息。  
  
 如果将结构化异常和 C++ 异常混合，请注意以下几点：  
  
1.  不能在同一函数中混合 C++ 异常和结构化异常。  
  
2.  始终执行终止处理程序（`__finally` 块），甚至在引发异常后的展开过程中也是如此。  
  
3.  C++ 异常处理可以捕获并保留展开使用编译的所有模块中的语义[/EH](../build/reference/eh-exception-handling-model.md)编译器选项 (此选项启用展开语义)。  
  
4.  可以存在一些不为所有对象调用析构函数的情况。 例如，如果在尝试通过未初始化的函数指针进行函数调用时发生结构化异常，并且该函数将调用前构造的对象用作参数，则在堆栈展开过程中将不会调用这些对象的析构函数。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [C++ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)  
  
-   [SEH 和 C++ EH 之间的差异](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 异常处理](../cpp/cpp-exception-handling.md)