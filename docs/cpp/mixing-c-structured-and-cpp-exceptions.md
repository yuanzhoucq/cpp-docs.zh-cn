---
title: 混合使用 C （结构化） 和 c + + 异常 |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 580fb4c96db70b612135ac48e30bd9c0d45c4d1c
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42572455"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合使用 C （结构化） 和 c + + 异常

如果你想要编写可移植代码，不被建议的结构化异常处理 (SEH) 机制在 c + + 程序中使用。 但是，有时可能希望使用进行编译[/EHa](../build/reference/eh-exception-handling-model.md)和混合使用结构化的异常和 c + + 源代码，并需要一些工具来处理这两种类型的异常。 由于结构化的异常处理程序的对象或类型化的异常没有概念，它不能处理 c + + 代码引发的异常。 但是，c + +**捕获**处理程序可以处理结构化的异常。 C + + 异常处理语法 (**尝试**，**引发**，**捕获**) 不被接受由 C 编译器，但结构化的异常处理语法 (**__try**， **__except**， **__finally**) 都支持 c + + 编译器支持。

请参阅[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)有关如何处理结构化的异常作为 c + + 异常的信息。

如果混合使用结构化和 c + + 异常，注意这些潜在的问题：

- 不能在同一函数中混合 C++ 异常和结构化异常。

- 终止处理程序 (**__finally**块) 将始终执行，即使引发异常后的展开过程。

- C + + 异常处理可以捕获并保留展开使用编译的所有模块中的语义[/EH](../build/reference/eh-exception-handling-model.md)编译器选项，哪些启用展开语义。

- 有时候，可能不会针对所有对象调用析构函数。 例如，如果尝试进行函数初始化的函数指针，通过调用时发生结构化的异常并且该函数将作为参数调用前构造的对象，这些对象的析构函数不调用在堆栈展开。

## <a name="next-steps"></a>后续步骤

- [C++ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)

  查看有关使用详细信息`setjmp`和`longjmp`c + + 程序中。

- [处理 c + + 中的结构化的异常](../cpp/exception-handling-differences.md)

  请参阅可用 c + + 来处理结构化异常的方法的示例。

## <a name="see-also"></a>请参阅

[C++ 异常处理](../cpp/cpp-exception-handling.md)  
