---
title: 混合 C （结构化）和 c + + 异常
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 72ddde9bc284a005c77694d599a8e9a3908cb2d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233686"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C （结构化）和 c + + 异常

如果要编写可移植代码，则建议不要在 c + + 程序中使用结构化异常处理（SEH）。 但是，有时您可能想要使用[/eha](../build/reference/eh-exception-handling-model.md)进行编译，并混合使用结构化异常和 c + + 源代码，并且需要使用某种工具来处理这两种异常。 由于结构化异常处理程序没有对象或类型化异常的概念，因此它无法处理 c + + 代码引发的异常。 但是，c + + **`catch`** 处理程序可以处理结构化异常。 C + + 编译器不接受 c + + 异常处理语法（ **`try`** 、 **`throw`** 、 **`catch`** ），但 c # 编译器支持结构化异常处理语法（**__try**、 **`__except`** 、 **`__finally`** ）。

有关如何处理结构化异常作为 c + + 异常的信息，请参阅[_set_se_translator](../c-runtime-library/reference/set-se-translator.md) 。

如果混合使用结构化异常和 c + + 异常，请注意以下潜在问题：

- 不能在同一函数中混合 C++ 异常和结构化异常。

- **`__finally`** 即使在引发异常后，也会始终执行终止处理程序（块）。

- C + + 异常处理可以捕获并保留使用[/EH](../build/reference/eh-exception-handling-model.md)编译器选项编译的所有模块中的展开语义，这会启用展开语义。

- 可以存在一些不为所有对象调用析构函数的情况。 例如，如果在尝试通过未初始化的函数指针进行函数调用时出现结构化异常，并且该函数采用在调用之前构造的参数对象，则在堆栈展开过程中不会调用这些对象的析构函数。

## <a name="next-steps"></a>后续步骤

- [在 C++ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)

  请参阅在 `setjmp` `longjmp` c + + 程序中使用和的详细信息。

- [处理 C++ 中的结构性异常](../cpp/exception-handling-differences.md)

  请参阅使用 c + + 处理结构化异常的方式的示例。

## <a name="see-also"></a>另请参阅

[异常和错误处理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)
