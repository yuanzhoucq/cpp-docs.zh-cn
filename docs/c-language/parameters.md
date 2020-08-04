---
title: 参数
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 57648747bbb50ffe46b199a03563757c331f088a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229566"
---
# <a name="parameters"></a>参数

自变量是通过函数调用传递到函数的值的名称。 形参是函数期望接收的值。 在函数原型中，函数名称后的括号包含函数的参数及其类型的完整列表。 参数声明指定参数中存储的值的类型、大小和标识符。

## <a name="syntax"></a>语法

*`function-definition`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`declaration-specifiers`<sub>opt</sub> `attribute-seq`<sub>opt</sub> `declarator` `declaration-list`<sub>opt</sub> `compound-statement`

/\* `attribute-seq` 是特定于 Microsoft 的 \*/

*`declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`pointer`<sub>opt</sub> `direct-declarator`

`direct-declarator`: /\* 函数声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`direct-declarator`  `(`  `parameter-type-list`  `)` /\* 新样式声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`direct-declarator`  `(`  `identifier-list`<sub>opt</sub> `)` /\* 已过时样式声明符 \*/

`parameter-type-list`: /\* 参数列表 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`* <br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`* **`, ...`**

*`parameter-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`* **`,`**  *`parameter-declaration`*

*`parameter-declaration`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`declaration-specifiers` `abstract-declarator`<sub>opt</sub>

`parameter-type-list` 是以逗号分隔的参数声明序列。 参数列表中的每个参数的格式如下所示：

> `register`<sub>opt</sub> `type-specifier` `declarator`<sub>opt</sub>

使用 `auto` 特性声明的函数参数生成错误。 参数的标识符在函数体中使用以引用传递给函数的值。 您可以在原型中命名参数，但名称会超出声明的末尾的范围。 也就是说，可以在函数定义中以相同或不同的方式分配参数名称。 这些标识符不能在函数主体的最外层块中重新定义，但它们可在内部的嵌套块中重新定义，就像参数列表是封闭块一样。

`parameter-type-list` 中的每个标识符前面都必须有适当的类型说明符，如下面的示例所示：

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

如果至少有一个参数出现在参数列表中，此列表的结尾可以是一个逗号后跟三个句点 (`, ...`)。 此构造称为“省略号表示法”，表示函数的可变数量的自变量。 （有关详细信息，请参阅[参数数量可变的调用](../c-language/calls-with-a-variable-number-of-arguments.md)。）但是，对函数进行调用时，自变量的数量必须至少与最后一个逗号前面的参数的数量相同。

如果没有参数要传递给函数，那么参数列表将被关键字 `void` 替换。 `void` 的这种用法与作为类型说明符的用法不同。

参数的顺序和类型（包括省略号表示法的任何用法）在所有函数声明（如果有）和函数定义中都必须相同。 进行常用算术转换后，自变量的类型与对应参数的类型必须是赋值兼容的。 （有关算术转换的信息，请参阅[常用算术转换](../c-language/usual-arithmetic-conversions.md)。）不检查省略号后面的参数。 参数可以具有任何基础、结构、联合、指针或数组类型。

如果需要，编译器将独立于每个参数和每个自变量执行常用算术转换。 转换后，没有参数短于 `int`，且没有参数的类型为 `float`，除非参数类型在原型中被显式指定为 `float`。 也就是说，例如，将参数声明为 `char` 与声明为 `int` 的效果相同。

## <a name="see-also"></a>请参阅

[C 函数定义](../c-language/c-function-definitions.md)
