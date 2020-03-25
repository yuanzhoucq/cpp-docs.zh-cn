---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188150"
---
# <a name="__thiscall"></a>__thiscall

**Microsoft 专用**

**__Thiscall**调用约定用于成员函数，是不使用变量参数的C++成员函数所使用的默认调用约定。 在 **__thiscall**下，被调用方清理堆栈，这对于 `vararg` 函数是不可能的。 自变量按从右到左推送到堆栈上，**此**指针通过 register ECX 传入，而不是在 x86 体系结构上的堆栈上。

使用 **__thiscall**的一个原因是在默认情况下，其成员函数使用 `__clrcall` 的类。 在这种情况下，可以使用 **__thiscall**使单个成员函数可从本机代码中调用。

用[/clr： pure](../build/reference/clr-common-language-runtime-compilation.md)进行编译时，除非另外指定，否则 `__clrcall` 所有函数和函数指针。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

在 Visual Studio 2005 之前的版本中，无法在程序中显式指定 **__thiscall**调用约定，因为 **__thiscall**不是关键字。

`vararg` 成员函数使用 **__cdecl**调用约定。 所有函数参数都将推送到堆栈上，并将**此**指针放在堆栈上最后

由于此调用约定仅适用于 C++，没有任何 C 名称修饰方案。

在 ARM 和 x64 计算机上，编译器接受并忽略 **__thiscall** 。

对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
