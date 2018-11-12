---
title: 函数声明和定义的过时形式
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 4822ee75c9a1112aff7c7b54dffb745325f56001
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444234"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>函数声明和定义的过时形式

旧式函数声明和定义使用与 ANSI C 标准建议的语法略微不同的规则来声明参数。 首先，旧式声明不具有参数列表。 第二，在函数定义中，列出了参数，但未在参数列表中声明其类型。 类型声明在构成函数主体的复合语句之前。 该旧式语法已过时，不应在新代码中使用。 但仍支持使用旧式语法的代码。 此示例阐释声明和定义的过时形式：

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

返回与 `int` 的大小相同的整数或指针的函数不需要具有声明，但建议具有声明。

为了遵循 ANSI C 标准，使用省略号的旧式函数声明现在会在使用 /Za 选项进行编译是生成错误，并在使用 /Ze 进行编译时生成 4 级别警告。 例如:

```
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

您应将此声明重写为原型：

```
void funct1( int a, ... )
{
}
```

旧式函数声明也会生成警告（如果您随后声明或定义具有省略号或具有与其提升的类型不同的类型的参数的相同函数）。

下一节（[C 函数定义](../c-language/c-function-definitions.md)）显示函数定义的语法（包括旧式语法）。 旧式语法中的参数列表的非终止符是 identifier-list。

## <a name="see-also"></a>请参阅

[函数概述](../c-language/overview-of-functions.md)