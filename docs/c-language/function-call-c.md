---
title: 函数调用 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48ddb3724e4c93135be57d1404ec51d5e885d4fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069815"
---
# <a name="function-call-c"></a>函数调用 (C)

函数调用是包含被调用函数的名称或函数指针的值以及（可选）传递给函数的自变量的表达式。

## <a name="syntax"></a>语法

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

postfix-expression 的计算结果必须为函数地址（例如，函数标识符或函数指针值），argument-expression-list 是其值（“参数”）传递到函数的表达式的列表（用逗号分隔）。 argument-expression-list 参数可以为空。

function-call 表达式具有函数的返回值的值和类型。 函数不能返回数组类型的对象。 如果函数的返回类型是 `void`（即该函数已被声明为从不返回值），则 function-call 表达式也具有 `void` 类型。 （有关详细信息，请参阅[函数调用](../c-language/function-calls.md)。）

## <a name="see-also"></a>请参阅

[函数调用运算符：()](../cpp/function-call-operator-parens.md)