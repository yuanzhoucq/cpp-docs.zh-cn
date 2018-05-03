---
title: 混合使用 C （结构化） 和 C++ 异常 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 375f954f3df300b50a11067b009614ff8879b9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合使用 C（结构化）和 C++ 异常
若要编写可移植性更高的代码，建议不要在 C++ 程序中使用结构化异常处理。 但是，有时可能希望使用**/EHa**编译和混合使用结构化的异常和 C++ 源代码，并且需要用于处理这两种异常的一些设备。 由于结构化异常处理程序没有对象或类型化异常概念，它无法处理 C++ 代码抛出的异常；但是，C++**catch**处理程序可以处理结构化的异常。 同样的，C++ 异常处理语法 (**try**， `throw`，**catch**) 无法被 C 编译器认可，但结构化的异常处理语法 (`__try`， `__except`， `__finally`)被C++编译器支持。  
  
 请参阅[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)同C++异常一样处理结构化异常。  
  
 如果将结构化异常和 C++ 异常混合，请注意以下几点：  
  
1.  不能在同一函数中混合 C++ 异常和结构化异常。  
  
2.  始终执行终止处理程序（`__finally` 块），甚至在引发异常后的展开过程中也是如此。  
  
3.  C++ 异常处理可以捕获并保留在所有模块用[/EH](../build/reference/eh-exception-handling-model.md)编译器选项编译时展开语义 (此选项启用展开语义)。  
  
4.  可能在所有对象中存在一些没有调用析构函数的情况。 例如，如果该函数在构造函数之前调用参数对象，使用未初始化函数指针尝试进行函数调用时发生结构化异常，则在堆栈展开过程中将不会调用这些对象的析构函数。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [C++ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)  
  
-   [SEH 和 C++ EH 之间的差异](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 异常处理](../cpp/cpp-exception-handling.md)
