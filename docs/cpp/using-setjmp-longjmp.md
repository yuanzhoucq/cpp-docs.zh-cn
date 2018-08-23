---
title: 使用 setjmp 和 longjmp |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: a83253fb98506bb586af2b52ef3321bada7ca01f
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42573320"
---
# <a name="using-setjmp-and-longjmp"></a>使用 setjmp 和 longjmp

当[setjmp](../c-runtime-library/reference/setjmp.md)并[longjmp](../c-runtime-library/reference/longjmp.md)是一起使用时，它们提供一种方法来执行非本地**goto**。 它们通常用于在 C 代码中将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用标准调用或返回约定。

> [!CAUTION]
> 因为`setjmp`和`longjmp`不支持 c + + 编译器之间移植的堆栈帧对象的正确析构和通过阻止局部变量优化，它们可能会降低性能，因为我们不建议在 c + + 中的使用它们程序。 我们建议你使用**尝试**并**捕获**构造。

如果您决定使用`setjmp`并`longjmp`在 c + + 程序中，还包括\<setjmp.h > 或\<setjmpex.h > 若要确保正确交互之间的函数和结构化异常处理 (SEH) 或 c + + 异常处理。

**Microsoft 专用**

如果您使用[/EH](../build/reference/eh-exception-handling-model.md)选项编译 c + + 代码中，在堆栈展开期间调用本地对象的析构函数。 但是，如果您使用 **/EHs**或 **/EHsc**进行编译，并且使用你的函数的一种[noexcept](../cpp/noexcept-cpp.md)调用`longjmp`，然后为该函数展开析构函数可能不会出现，具体取决于优化器状态。

在可移植代码中，当`longjmp`基于框架的对象的正确析构显式不保证由标准，和其他编译器可能不支持执行调用。 若要让您知道，在警告等级 4，调用`setjmp`导致警告 C4611: _setjmp 和 c + + 对象析构之间的交互是不可移植。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
