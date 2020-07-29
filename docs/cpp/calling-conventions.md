---
title: 调用约定
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: d351ae064b8c9bdd0599a1d6981166371a62af58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216604"
---
# <a name="calling-conventions"></a>调用约定

Visual C/C++ 编译器提供了用于调用内部函数和外部函数的几个不同的约定。 了解这些不同的方法有助于调试程序以及将你的代码与汇编语言例程链接。

本主题中的各个主题说明了调用约定之间的差异、如何传递参数以及函数如何返回值。 它们也讨论了裸函数调用以及使你能够写入自己的 prolog 和 epilog 代码的高级功能。

有关调用 x64 处理器约定的信息，请参阅[调用约定](../build/x64-calling-convention.md)。

## <a name="topics-in-this-section"></a>本部分中的主题

- [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)（ **`__cdecl`** 、 **`__stdcall`** 、等 **`__fastcall`** ）

- [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)

- [使用裸函数调用编写自定义 prolog/epilog 代码](../cpp/naked-function-calls.md)

- [浮点协处理器和调用约定](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [已过时调用约定](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>另请参阅

[Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)
