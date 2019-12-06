---
title: C 函数定义
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 5cf56375df417ac68b3e03d00f2bd7770ee571e8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857133"
---
# <a name="c-function-definitions"></a>C 函数定义

函数定义指定函数的名称、函数期望接收的参数的类型和数量以及函数的返回类型。 函数定义还包括带有局部变量的声明的函数体和确定函数行为的语句。

## <a name="syntax"></a>语法

translation-unit：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

external-declaration: /\* 只允许在外部（文件）范围内 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

function-definition：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**属性-seq*是特定于 Microsoft 的 \*/

原型参数为：

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

declaration-list：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;pointer<sub>opt</sub> direct-declarator

direct-declarator: /\* 函数声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  /\* New-style declarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**  /\* Obsolete-style declarator \*/

定义中的参数列表使用以下语法：

parameter-type-list： /\* 参数列表 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

旧式函数定义中的参数列表使用以下语法：

identifier-list：/\* 在旧式函数定义和声明中使用 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier-list* **,**  *identifier*

函数体的语法为：

compound-statement：<br/>
nchen&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

仅有的可修改函数声明的存储类说明符是 extern 和 static。 extern 说明符表示可以从其他文件引用函数；即，将函数名导出到链接器。 static 说明符表示不能从其他文件引用函数；即，链接器不会导出名称。 如果存储类未在函数定义中出现，则假定 extern。 在任何情况下，从定义点到文件的末尾函数始终可见。

可选的 declaration-specifiers 和必需的 declarator 共同指定函数的返回类型和名称。 declarator 是用来命名函数的标识符与函数名后面的括号的组合。 可选的 attribute-seq 非终止符是在[函数特性](../c-language/function-attributes.md)中定义的 Microsoft 专用功能。

direct-declarator（在 declarator 语法中）指定要定义的函数的名称及其参数的标识符。 如果 direct-declarator 包括 parameter-type-list，则该列表将指定所有参数的类型。 此类声明符还用作以后对函数进行调用时的函数原型。

函数定义中的 declaration-list 内的 declaration 不能包含除 register 之外的 storage-class-specifier。 仅当为 int 类型的值指定 register 存储类时，才能省略 declaration-specifiers 语法中的 type-specifier。

compound-statement 是包含局部变量声明、对在外部声明的项的引用和语句的函数体。

[函数特性](../c-language/function-attributes.md)、[存储类](../c-language/storage-class.md)、[返回类型](../c-language/return-type.md)、[参数](../c-language/parameters.md)和[函数体](../c-language/function-body.md)节详细地描述了函数定义的组成部分。

## <a name="see-also"></a>另请参阅

[函数](../c-language/functions-c.md)
