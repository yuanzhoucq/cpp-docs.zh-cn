---
title: 示例程序
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: fc00ee391fd845039791b8cec727623074a7aeff
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147121"
---
# <a name="example-program"></a>示例程序

下面的 C 源程序包括两个源文件。 它尽可能在 C 程序中提供一些各种声明和定义的概述。 本书后面的节中描述了如何写入这些声明、定义和初始化，以及如何使用 C 关键字（例如，static 和 `extern`）。 在 C 标头文件 STDIO.H. 中声明 `printf` 函数。

假定 `main` 和 `max` 函数在单独的文件中，且程序的执行开始于 `main` 函数。 未在 `main` 之前执行任何显式用户函数。

```
/*****************************************************************
                    FILE1.C - main function
*****************************************************************/

#define ONE     1
#define TWO     2
#define THREE   3
#include <stdio.h>

int a = 1;                       // Defining declarations
int b = 2;                       //  of external variables

extern int max( int a, int b );  // Function prototype

int main()                       // Function definition
{                                //  for main function
    int c;                       // Definitions for
    int d;                       //  two uninitialized
                                 //  local variables

    extern int u;                // Referencing declaration
                                 //  of external variable
                                 //  defined elsewhere
    static int v;                // Definition of variable
                                 //  with continuous lifetime

    int w = ONE, x = TWO, y = THREE;
    int z = 0;

    z = max( x, y );             // Executable statements
    w = max( z, w );
    printf_s( "%d %d\n", z, w );
    return 0;
}

/****************************************************************
            FILE2.C - definition of max function
****************************************************************/

int max( int a, int b )          // Note formal parameters are
                                 //  included in function header
{
    if( a > b )
        return( a );
    else
        return( b );
}
```

FILE1.C 包含 `max` 函数的原型。 这种声明有时称为“前向声明”，因为该函数在使用之前被声明。 `main` 函数的定义包含对 `max` 的调用。

以 `#define` 开始的行是预处理指令。 这些指令告知预处理器通过 FILE1.C.用数字 `ONE`、`TWO` 和 `THREE` 分别替换标识符 `1`、`2` 和 `3`。 但是，此类指令不适用于 FILE2.C，将单独对其进行编译，然后将其与 FILE1.C 链接。 以 `#include` 开始的行告知编译器包含文件 STDIO.H，该文件包含 `printf` 函数的原型。 [预处理器指令](../preprocessor/preprocessor-directives.md)在《预处理器参考》中进行了解释。

FILE1.C 使用定义声明初始化全局变量 `a` 和 `b`。 声明但不初始化局部变量 `c` 和 `d`。 为所有这些变量分配存储。 静态和外部变量 `u` 和 `v` 将自动初始化为 0。 因此，仅 `a`、`b`、`u` 和 `v` 在被声明时包含有意义的值，因为它们被显式或隐式初始化。 FILE2.C 包含 `max` 的函数定义。 此定义满足 FILE1.C. 中对 `max` 的调用。

[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)中讨论了标识符的生存期和可见性。 有关函数的详细信息，请参阅[函数](../c-language/functions-c.md)。

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)
