---
title: 函数原型
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: 76e8abdaa2e2d0d8ba14209b45982b6a7f63f2e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227850"
---
# <a name="function-prototypes"></a>函数原型

函数声明位于函数定义之前，用来指定函数的名称、返回类型、存储类和其他特性。 若要作为原型，函数声明还必须为函数的参数确定类型和标识符。

## <a name="syntax"></a>语法

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub> **;**

/\* *attribute-seq*<sub>opt</sub> is Microsoft-specific \*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

direct-declarator  : /\* 函数声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**   /\* New-style declarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**  /\* Obsolete-style declarator \*/

原型与函数定义具有相同的形式，只不过前者由紧跟在右括号后的分号结尾，因此没有主体。 在任一情况下，返回类型都必须与函数定义中指定的返回类型一致。

函数原型有下列重要用途：

- 它们为返回除 `int` 以外的类型的函数建立返回类型。 尽管返回 `int` 值的函数不需要原型，但仍建议使用原型。

- 如果没有完整原型，将进行标准转换，但不会尝试使用形参的数量检查实参的类型或数量。

- 原型用于在定义函数之前初始化指向函数的指针。

- 形参列表用于通过函数定义中的形参来检查函数调用中的实参的对应性。

每个形参的转换类型决定函数调用在堆栈上放置的实参的解释。 自变量和参数的类型不匹配可能导致堆栈上的自变量被错误解释。 例如，在 16 位计算机上，如果 16 位指针先作为实参传递，再声明为 `long` 形参，那么堆栈上的前 32 位将解释为 `long` 形参。 此错误不仅会导致 `long` 参数出现问题，而且还会导致其后的所有参数都出现问题。 您可通过声明所有函数的完整函数原型来检测此类错误。

原型将确定函数的特性，以便能检查位于函数定义前面（或者出现在其他源文件中）的函数调用是否存在参数类型和返回类型不匹配。 例如，如果在原型中指定 `static` 存储类说明符，还必须在函数定义中指定 `static` 存储类。

完整参数声明 (`int a`) 可以与抽象声明符 (`int`) 在同一个声明中混合使用。 例如，以下声明是合法的：

```C
int add( int a, int );
```

原型可同时包含作为参数传递的每个表达式的类型和标识符。 但是，此类标识符的范围只到该声明的末尾。 原型也可以反映参数的数量是变量或未传递参数的事实。 如果没有此类列表，则不能显示不匹配项，从而使编译器无法生成有关它们的诊断消息。 有关类型检查的详细信息，请参阅[参数](../c-language/arguments.md)。

使用 /Za  编译器选项进行编译时，Microsoft C 编译器中的原型范围现在符合 ANSI。 也就是说，如果你在原型中声明 `struct` 或 `union` 标记，那么标记是在此范围（而不是全局范围）输入。 例如，为符合 ANSI 而使用 /Za 进行编译时，绝不可能调用此函数而不遇到类型不匹配错误：

```C
void func1( struct S * );
```

若要更正代码，请在函数原型之前在全局范围定义或声明 `struct` 或 `union`：

```C
struct S;
void func1( struct S * );
```

在 /Ze  下，仍将在全局范围内输入标记。

## <a name="see-also"></a>请参阅

[函数](../c-language/functions-c.md)
