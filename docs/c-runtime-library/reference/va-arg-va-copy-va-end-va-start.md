---
title: va_arg、va_copy、va_end、va_start | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- va_arg
- va_end
- va_copy
- va_start
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f634e713bcf87aa6d97ed4e49595e4c0f8b72ab3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg、va_copy、va_end、va_start

访问变量参数列表。

## <a name="syntax"></a>语法

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>参数

*type*<br/>
要检索的参数类型。

*arg_ptr*<br/>
指向参数列表的指针。

*dest*<br/>
指向自变量从初始化列表*src*

*src*<br/>
指向要将复制到自变量的初始化列表*dest*。

*prev_param*<br/>
位于第一个可选实参之前的形参。

## <a name="return-value"></a>返回值

**va_arg**返回当前的自变量。 **va_copy**， **va_start**和**va_end**不返回值。

## <a name="remarks"></a>备注

**Va_arg**， **va_copy**， **va_end**，和**va_start**宏提供用于访问函数的自变量的可移植方法时函数采用数目可变的参数。 有两种版本的宏：STDARG.H 中定义的宏符合 ISO C99 标准；弃用了 VARARGS.H 中定义的宏但是将其保留以保证与写于 ANSI C89 标准之前的代码的后向兼容性。

这些宏假定函数采用固定数量的必需参数，后面是可变数量的可选参数。 将必需参数声明为函数的普通参数，且可通过参数名称访问它们。 可选参数可通过 STDARG.H 中的宏访问（对于在 ANSI C89 标准之前编写的代码，通过 VARARGS.H），其将指针设置为参数列表中的第一个可选参数、检索列表中的参数并在参数处理完成后重置指针。

STDARG.H 中定义的 C 标准宏使用方法如下：

- **va_start**设置*arg_ptr*到传递给函数的参数列表中第一个可选参数。 自变量*arg_ptr*必须具有**va_list**类型。 自变量*prev_param*是所需的参数列表中紧跟第一个可选参数的参数的名称。 如果*prev_param*声明使用寄存器存储类，则该宏的行为是不确定。 **va_start**之前，必须使用**va_arg**首次使用。

- **va_arg**检索的值*类型*从给定的位置*arg_ptr*，、 增量*arg_ptr*以指向按列表中的下一个参数使用的大小*类型*确定下一个参数从何处开始。 **va_arg**可以是用于任意次数函数中，从列表中检索自变量。

- **va_copy**在其当前状态生成的参数列表的副本。 *Src*参数必须已使用初始化**va_start**; 它可能已使用的更新**va_arg**调用，但必须不已重置与**va_end**. 通过检索下一个参数**va_arg**从*dest*从检索到的下一步自变量相同*src*。

- 检索所有自变量后， **va_end**重置到指针**NULL**。 **va_end**必须对使用初始化每个自变量列表调用**va_start**或**va_copy**函数返回之前。

> [!NOTE]
> VARARGS.H 中的宏已弃用，将其保留只为保证与写于 ANSI C89 标准之前的代码的后向兼容性。 在所有其他情况下，请使用 STDARGS.H 中的宏。

它们使用 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)编译时，使用这些宏的程序可能会因为本机和公共语言运行时 (CLR) 类型系统之间的差异而生成意外的结果。 考虑此程序：

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

请注意， **testit**第二个参数可以是以下之一应**int**或**char\***。 传递的自变量是 0xffffffff (**无符号** **int**，而不**int**) 和**NULL** (实际**int**，而不**char\***)。 为本机代码编译程序后，其生成以下输出：

```Output
-1

(null)
```

## <a name="requirements"></a>要求

**标头：** \<stdio.h> 和 \<stdarg.h>

**弃用的标头：** \<varargs.h>

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>请参阅

[参数访问](../../c-runtime-library/argument-access.md)<br/>
[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
