---
title: 表达式计算 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233842"
---
# <a name="expression-evaluation-c"></a>表达式计算 (C)

涉及赋值、一元递增、一元递减或调用函数的表达式可能具有其计算附带的结果（副作用）。 当达到“序列点”时，确保对序列点后面的任何内容执行计算之前已计算序列点前面的所有内容（包括任何副作用）。

“副作用”是由表达式的计算引起的更改。 只要表达式计算更改变量的值，就会出现副作用。 所有赋值运算都具有副作用。 如果函数调用通过直接赋值或使用指针进行间接赋值来更改外部可见项的值，则函数调用还会产生副作用。

## <a name="see-also"></a>请参阅

[操作数和表达式](../c-language/operands-and-expressions.md)
