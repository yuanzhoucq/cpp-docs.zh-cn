---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854809"
---
# `__thiscall`

**Microsoft 特定**的 **`__thiscall`** 调用约定用于 x86 体系结构上的 c + + 类成员函数。 这是不使用变量参数（函数）的成员函数所使用的默认调用约定 `vararg` 。

在下 **`__thiscall`** ，被调用方清理堆栈，这对于函数是不可能的 `vararg` 。 自变量从右到左推送到堆栈上。 **`this`** 指针通过 REGISTER ECX 传递，而不是在堆栈上传递。

在 ARM、ARM64 和 x64 计算机上， **`__thiscall`** 由编译器接受和忽略。 这是因为它们在默认情况下使用基于寄存器的调用约定。

使用的一个原因 **`__thiscall`** 是在默认情况下，其成员函数使用 **`__clrcall`** 。 在这种情况下，可以使用 **`__thiscall`** 使单个成员函数可从本机代码中调用。

在编译时 [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) ，除非另外指定，否则所有函数和函数指针均为 **`__clrcall`** 。 **`/clr:pure`** 和 **`/clr:safe`** 编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

`vararg`成员函数使用 **`__cdecl`** 调用约定。 所有函数参数都将推送到堆栈上， **`this`** 最后将指针放在堆栈上。

由于此调用约定仅适用于 c + +，因此没有 C 名称修饰方案。

在外定义非静态类成员函数时，请仅在声明中指定调用约定修饰符。 无需在外定义中再次指定它。 编译器使用在定义时在声明期间指定的调用约定。

## <a name="see-also"></a>另请参阅

[参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
