---
title: C 复合赋值 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4450682abbb5efd739b5eb08d228b4c55d00ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029320"
---
# <a name="c-compound-assignment"></a>C 复合赋值

复合赋值运算符将简单赋值运算符与另一个二元运算符相结合。 复合赋值运算符执行其他运算符指定的运算，然后将结果赋给左操作数。 例如，一个复合赋值表达式，如

> *expression1* **+=** *expression2*

可以理解为

> *expression1* **=** *expression1* **+** *expression2*

但是，复合赋值表达式不等于扩展版本，因为复合赋值表达式只计算 *expression1* 一次，而扩展版本将计算 *expression1* 两次：在加法运算和赋值运算中。

复合赋值运算符的操作数必须为整型或浮点型。 每个复合赋值运算符都将执行对应的二元运算符所执行的转换并相应地限制其操作数的类型。 加法赋值 (`+=`) 和减法赋值 (**-=**) 运算符还可以具有指针类型的左操作数，在此情况下，右操作数必须为整型类型。 复合赋值运算的结果具有左操作数的值和类型。

```C
#define MASK 0xff00

n &= MASK;
```

在此示例中，对 `n` 和 `MASK` 执行了按位“与”运算，并将结果赋给了 `n`。 使用 [#define](../preprocessor/hash-define-directive-c-cpp.md) 预处理器指令定义了清单常量 `MASK`。

## <a name="see-also"></a>请参阅

[C 赋值运算符](../c-language/c-assignment-operators.md)