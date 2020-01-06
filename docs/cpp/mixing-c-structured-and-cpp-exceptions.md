---
title: 混合 C （结构化） C++和异常
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246458"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C （结构化） C++和异常

如果要编写可移植代码，则不建议在C++程序中使用结构化异常处理（SEH）。 但是，有时可能需要使用[/eha](../build/reference/eh-exception-handling-model.md)进行编译，并混合使用结构化C++异常和源代码，并需要使用某种工具来处理这两种异常。 由于结构化异常处理程序没有对象或类型化异常的概念，因此它无法处理由C++代码引发的异常。 但是， C++ **catch**处理程序可以处理结构化异常。 C++C 编译器不接受异常处理语法（**try**、 **throw**、 **catch**），但C++编译器支持结构化异常处理语法（ **__try**、 **__except** **__finally**）。

有关如何处理结构化异常作为C++异常的信息，请参阅 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md)。

如果混合了结构化C++和异常，请注意以下潜在问题：

- 不能在同一函数中混合 C++ 异常和结构化异常。

- 始终会执行终止处理程序（ **__finally**块），即使在引发异常后在展开过程中也是如此。

- C++异常处理可以捕获并保留使用[/EH](../build/reference/eh-exception-handling-model.md)编译器选项编译的所有模块中的展开语义，这会启用展开语义。

- 有时候，可能不会针对所有对象调用析构函数。 例如，如果在尝试通过未初始化的函数指针进行函数调用时出现结构化异常，并且该函数采用在调用之前构造的参数对象，则不会调用这些对象的析构函数堆栈展开期间。

## <a name="next-steps"></a>后续步骤

- [C++ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)

  详细了解如何在程序中C++使用 `setjmp` 和 `longjmp`。

- [处理 C++ 中的结构性异常](../cpp/exception-handling-differences.md)

  请参阅可用于C++处理结构化异常的方式的示例。

## <a name="see-also"></a>请参阅

[异常C++和错误处理的新式最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)
