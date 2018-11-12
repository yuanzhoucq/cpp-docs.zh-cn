---
title: 声明概述
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 4e6c166763afd18db79798024d8b2f159ffed76d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582749"
---
# <a name="overview-of-declarations"></a>声明概述

“声明”指定一组标识符的解释和特性。 还将导致针对标识符命名的对象或函数保留存储的声明将称为“定义”。 用于变量、函数和类型的 C 声明都具有以下语法：

## <a name="syntax"></a>语法

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;declaration-specifiers attribute-seq<sub>opt</sub> init-declarator-list<sub>opt</sub>;

/\* attribute-seq<sub>opt</sub> 是 Microsoft 专用的 */

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;declarator = initializer

> [!NOTE]
> 用于 declaration 的这种语法在以下部分中不重复。 以下部分中的语法通常以 declarator 非终止符开头。

init-declarator-list 中的声明包含已命名的标识符；init 是初始值设定项的缩写。 init-declarator-list 是逗号分隔的声明符序列，其中每个都可具有附加类型信息和/或初始值设定项。 declarator 包含要声明的标识符（如果有）。 declaration-specifiers 非终止符由一列类型和存储类说明符组成，这些说明符指示链接、存储持续时间，并且至少可以指示声明符表示的部分实体类型。 因此，声明由存储类说明符、类型说明符、类型限定符、声明符以及初始值的某种组合构成。

声明可以包含 attribute-seq 中列出的一个或多个可选特性；seq 是序列的缩写。 这些特定于 Microsoft 的特性会执行各种功能（本书中将进行详细介绍）。

在变量声明的常规形式中，type-specifier 提供了变量的数据类型。 当类型由 const 或 `volatile` 修改时，type-specifier 可以是复合形式。 `declarator` 可为变量命名，并可能将其修改以用于声明数组类型或指针类型。 例如，应用于对象的

```C
int const *fp;
```

将名为 `fp` 的变量声明为一个指向不可修改的 (const) `int` 值的指针。 可以使用多个声明符（用逗号分隔）来定义声明中的多个变量。

声明必须至少具有一个声明符，或者其类型说明符必须声明一个结构标记、联合标记或枚举的成员。 声明符提供有关标识符的所有剩余信息。 声明符是一个标识符，可使用方括号 ([ ])、星号 (\*) 或括号 ( ( ) ) 对其进行修改，以分别声明数组、指针或函数类型。 在声明简单变量（例如字符、整数和浮点项）或简单变量的结构和联合时，`declarator` 只是一个标识符。 有关声明符的详细信息，请参阅[声明符和变量声明](../c-language/declarators-and-variable-declarations.md)。

所有定义都为隐式声明，但并非所有声明都为定义声明。 例如，以 `extern` 存储类说明符开头的变量声明是“引用”声明而非“定义”声明。 如果在定义外部变量之前引用它，或者在使用该变量的文件之外的其他源文件中定义它，则 `extern` 声明是必需的。 存储无法由“引用”声明分配，也不能在声明中初始化变量。

变量声明中需要存储类或类型（或者这两者）。 除了 `__declspec`，声明中只允许包含一个存储类说明符，并且并非每一个上下文中都允许存在所有存储类说明符。 `__declspec` 存储类可以与其他存储类说明符一起使用，并且允许多次一起使用。 声明的存储类说明符会影响存储和初始化声明的项的方式，还会影响程序中的哪些部分可以引用该项。

C 中定义的 storage-class-specifier 终止符包括 auto、`extern`、register、static 以及 `typedef`。 此外，Microsoft C 还包括 storage-class-specifier 终止符 `__declspec`。 [存储类](../c-language/c-storage-classes.md)中将讨论除 `typedef` 和 `__declspec` 之外的所有 storage-class-specifier 终止符。 有关 `typedef` 的信息，请参阅 [Typedef 声明](../c-language/typedef-declarations.md)。 有关 `__declspec` 的信息，请参阅[扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)。

源程序中声明的位置以及变量的其他声明存在与否是确定变量生存期的重要因素。 可以有多个重新声明，但只能有一个定义。 但是，定义可以出现在多个翻译单元中。 对于带内部链接的对象，此规则可分别应用到每个翻译单元，因为内部链接的对象对翻译单元是唯一的。 对于带外部链接的对象，此规则适用于整个程序。 有关可见性的详细信息，请参阅[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)。

类型说明符提供了一些有关标识符的数据类型的信息。 默认类型说明符是 `int`。 有关详细信息，请参阅[类型说明符](../c-language/c-type-specifiers.md)。 类型说明符还可以定义类型标记、结构和联合组件名称以及枚举常量。 有关详细信息，请参阅[枚举声明](../c-language/c-enumeration-declarations.md)、[结构声明](../c-language/structure-declarations.md)和[联合声明](../c-language/union-declarations.md)。

type-qualifier 终止符有两种：const 和 `volatile`。 这些限定符指定仅在通过左值访问该类型的对象时才相关的类型的其他属性。 有关 const 和 `volatile` 的详细信息，请参阅[类型限定符](../c-language/type-qualifiers.md)。 有关左值的定义，请参阅[左值和右值表达式](../c-language/l-value-and-r-value-expressions.md)。

## <a name="see-also"></a>请参阅

[C 语言语法摘要](../c-language/c-language-syntax-summary.md)<br/>
[声明和类型](../c-language/declarations-and-types.md)<br/>
[声明摘要](../c-language/summary-of-declarations.md)