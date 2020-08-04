---
title: 函数调用 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 23531f25128fc267caa3a3cad5f2c52e603a2cc6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229683"
---
# <a name="function-call-c"></a>函数调用 (C)

函数调用  是包含被调用函数的名称或函数指针的值以及（可选）传递给函数的自变量的表达式。

## <a name="syntax"></a>语法

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

postfix-expression  的计算结果必须为函数地址（例如，函数标识符或函数指针值），argument-expression-list  是其值（“参数”）传递到函数的表达式的列表（用逗号分隔）。 argument-expression-list 参数可以为空。

function-call 表达式具有函数的返回值的值和类型。 函数不能返回数组类型的对象。 如果函数的返回类型是 `void`（即函数已被声明为永不返回值），那么函数调用表达式的类型也是 `void`。 （有关详细信息，请参阅[函数调用](../c-language/function-calls.md)。）

## <a name="see-also"></a>请参阅

[函数调用运算符：()](../cpp/function-call-operator-parens.md)
