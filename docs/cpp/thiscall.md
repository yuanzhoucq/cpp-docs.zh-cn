---
title: __thiscall |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704398"
---
# <a name="thiscall"></a>__thiscall

**Microsoft 专用**

`__thiscall`调用约定成员函数上使用，并且是由不使用变量自变量的 C++ 成员函数的默认调用约定。 下`__thiscall`，被调用方将清理堆栈，这是不可能`vararg`函数。 自变量推送到堆栈上从右向左，与`this`通过寄存器 ECX，而不是在 x86 上的堆栈，传递的指针体系结构。

若要使用的一个原因`__thiscall`在其成员函数使用的类`__clrcall`默认情况下。 在这种情况下，你可以使用`__thiscall`将各个成员函数可从本机代码调用。

使用编译时[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)，所有函数和函数指针`__clrcall`除非另有指定。 **/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

在 Visual c + + 2005 中之前, 的版本中`__thiscall`调用约定无法显式指定在程序中，因为`__thiscall`不是一个关键字。

`vararg` 成员函数使用`__cdecl`调用约定。 所有函数参数都推送到堆栈上，使用`this`指针将位于堆栈上上一次

由于此调用约定仅适用于 C++，没有任何 C 名称修饰方案。

在 ARM 和 x64 的计算机，`__thiscall`接受和忽略由编译器。

对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

- [自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
