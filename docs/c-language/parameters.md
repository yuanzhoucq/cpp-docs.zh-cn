---
title: "参数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73e7aa3ff62782c6ebd3b5a8728aa05e78b1784
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="parameters"></a>参数
自变量是通过函数调用传递到函数的值的名称。 形参是函数期望接收的值。 在函数原型中，函数名称后的括号包含函数的参数及其类型的完整列表。 参数声明指定参数中存储的值的类型、大小和标识符。  
  
## <a name="syntax"></a>语法  
 function-definition：  
 declaration-specifiers optattribute-seq optdeclarator declaration-list optcompound-statement  
  
 /\* *attribute-seq* 为 Microsoft 专用 */  
  
 declarator :  
 pointer optdirect-declarator  
  
 direct-declarator：/\* 函数声明符 \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* 新样式声明符 \*/  
  
 parameter-type-list：/\* 参数列表 \*/  
 *parameter-list*  
  
 parameter-list  ,...  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *parameter-declaration*:  
 declaration-specifiers declarator  
  
 *declaration-specifiers abstract-declarator* opt  
  
 parameter-type-list 是一系列以逗号分隔的参数声明。 参数列表中的每个参数的格式如下所示：  
  
```  
[register]  type-specifier [declarator]   
```  
  
 用 auto 特性声明的函数参数会产生错误。 参数的标识符在函数体中使用以引用传递给函数的值。 您可以在原型中命名参数，但名称会超出声明的末尾的范围。 因此，在函数定义中可以用相同或不同的方式分配参数名称。 这些标识符不能在函数体的最外面的块中重新定义，但它们可在内部的嵌套块中定义，就像参数列表位于封闭块中一样。  
  
 parameter-type-list 中的每个标识符的前面必须是其合适的类型说明符，如以下示例所示：  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 如果至少有一个参数出现在参数列表中，则该列表可以以一个逗号后跟三个句点 (, ...) 结尾。此构造称为“省略号表示法”，表示函数的可变数量的自变量。 （有关详细信息，请参阅[使用可变数量的参数进行调用](../c-language/calls-with-a-variable-number-of-arguments.md)。）但是，对函数进行调用时，自变量的数量必须至少与最后一个逗号前面的参数的数量相同。  
  
 如果实参不会传递到函数，则形参的列表将替换为关键字 `void`。 对 `void` 的这种用法不同于将其用作类型说明符。  
  
 参数的顺序和类型（包括省略号表示法的任何用法）在所有函数声明（如果有）和函数定义中都必须相同。 进行常用算术转换后，自变量的类型与对应参数的类型必须是赋值兼容的。 （有关算术转换的信息，请参阅[常用算术转换](../c-language/usual-arithmetic-conversions.md)。）不检查省略号后面的自变量。 参数可以具有任何基础、结构、联合、指针或数组类型。  
  
 如果需要，编译器将独立于每个参数和每个自变量执行常用算术转换。 转换后，没有参数短于 `int` 且没有参数具有 float 类型，除非参数类型在原型中显式指定为 float。 这意味着，例如，将参数声明为 `char` 与将其声明为 `int` 的效果相同。  
  
## <a name="see-also"></a>请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)