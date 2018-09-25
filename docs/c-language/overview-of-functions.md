---
title: 函数概述 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b03357ed094684bb561eff9b790c090a1ebb0712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033623"
---
# <a name="overview-of-functions"></a>函数概述

函数必须具有定义且应具有声明，尽管定义可用作声明（如果声明在调用函数前出现）。 函数定义包含函数主体（调用函数时执行的代码）。

函数声明为程序中其他位置定义的函数建立名称、返回类型和特性。 函数声明必须在对函数的调用之前。 这就是为什么在调用运行时函数之前将包含运行时函数的声明的头文件包含在您的代码中的原因。 如果声明包含有关参数的类型和数目的信息，则该声明为原型。 有关详细信息，请参阅[函数原型](../c-language/function-prototypes.md)。

编译器使用原型来比较随后通过函数的参数对函数进行的调用中的自变量类型，并在需要时，将自变量类型转换为参数类型。

函数调用将执行控制从正在调用的函数传递到已调用函数。 通过值将参数（如果有）传递给已调用函数。 已调用函数中的 `return` 语句的执行将返回控制，并且可能将一个值返回给正在调用的函数。

## <a name="see-also"></a>请参阅

[函数](../c-language/functions-c.md)