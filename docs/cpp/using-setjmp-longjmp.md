---
title: 使用 setjmp 和 longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 6adbe22eb684c9a1dda080f6d35a99c55d6c3d30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226992"
---
# <a name="using-setjmp-and-longjmp"></a>使用 setjmp 和 longjmp

当[setjmp](../c-runtime-library/reference/setjmp.md)和[longjmp](../c-runtime-library/reference/longjmp.md)一起使用时，它们提供了一种方法来执行非本地 **`goto`** 。 它们通常在 C 代码中用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。

> [!CAUTION]
> 由于 `setjmp` 和 `longjmp` 不支持在 c + + 编译器之间移植正确销毁堆栈帧对象，并且由于在局部变量上阻止优化，它们可能会降低性能，因此我们不建议在 c + + 程序中使用它们。 建议 **`try`** **`catch`** 改用和构造。

如果您决定 `setjmp` `longjmp` 在 c + + 程序中使用和，还可以包括 \<setjmp.h> 或 \<setjmpex.h> 以确保函数和结构化异常处理（SEH）或 c + + 异常处理之间的正确交互。

**Microsoft 专用**

如果使用[/EH](../build/reference/eh-exception-handling-model.md)选项编译 c + + 代码，则在堆栈展开过程中将调用本地对象的析构函数。 但是，如果使用 **/ehs**或 **/ehsc**进行编译，并使用了使用[noexcept](../cpp/noexcept-cpp.md)调用的函数之一，则 `longjmp` 可能不会发生该函数的析构函数展开，具体情况视优化器状态而定。

在可移植代码中， `longjmp` 执行调用时，标准不保证正确销毁基于帧的对象，并且其他编译器可能不支持此方法。 为了让你知道，在警告等级4，对的调用 `setjmp` 会导致警告 C4611： "_setjmp" 和 c + + 对象析构之间的交互是不可移植的。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[混合 C （结构化）和 c + + 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)
