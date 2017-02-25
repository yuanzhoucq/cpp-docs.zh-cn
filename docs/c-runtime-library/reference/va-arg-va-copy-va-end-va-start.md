---
title: "va_arg、va_copy、va_end、va_start | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "va_arg"
  - "va_end"
  - "va_copy"
  - "va_start"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "va_arg"
  - "va_start"
  - "va_list"
  - "va_alist"
  - "va_dcl"
  - "va_copy"
  - "va_end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "变量自变量列表访问"
  - "va_start 宏"
  - "va_arg 宏"
  - "va_end 宏"
  - "参数 [c + +]，自变量列表"
  - "va_list 宏"
  - "va_dcl 宏"
  - "va_alist 宏"
  - "va_copy 宏"
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# va_arg、va_copy、va_end、va_start
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

访问变量自变量列表。  
  
## <a name="syntax"></a>语法  
  
```  
  
      type va_arg(  
   va_list arg_ptr,  
   type   
);void va_copy(  
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
);  // (Pre-ANSI C89 standardization version)  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 要检索的参数的类型。  
  
 `arg_ptr`  
 指向参数列表的指针。  
  
 `dest`  
 自变量从初始化列表的指针 `src`  
  
 `src`  
 指向要将复制到自变量的初始化列表 `dest`。  
  
 `prev_param`  
 之前的第一个可选参数的参数。  
  
## <a name="return-value"></a>返回值  
 `va_arg` 返回当前的自变量。 `va_copy`, `va_start` 和 `va_end` 不返回值。  
  
## <a name="remarks"></a>备注  
  `va_arg`, ，`va_copy`, ，`va_end`, ，和 `va_start` 宏提供可移植的方式时该函数采用数目可变的参数访问函数的自变量。 有两个版本的宏︰ STDARG 中定义的宏。H 符合 ISO C99 标准;在 VARARGS 中定义的宏。H 已弃用，但将保留用于向后兼容性在 ANSI C89 标准之前编写的代码。  
  
 这些宏将假定该函数采用固定的数量的跟可选的参数个数可变的所需参数。 所需的参数声明为函数的普通参数，并且可以通过参数名称。 通过在 STDARG 宏访问的可选自变量。H （或 VARARGS。已在 ANSI C89 标准之前编写的代码，H)，这将指针设置为第一个可选参数在参数列表中，从列表中，检索自变量和自变量处理完成时重置指针。  
  
 C 标准宏，STDARG 中定义。H，使用方式如下︰  
  
-   `va_start` 设置 `arg_ptr` 到传递给函数的参数列表中第一个可选参数。 自变量 `arg_ptr` 必须具有 `va_list` 类型。 自变量 `prev_param` 是所需的参数列表中紧跟第一个可选参数的参数的名称。 如果 `prev_param` 声明使用寄存器存储类，则该宏的行为是不确定。 `va_start` 必须使用之前 `va_arg` 首次使用。  
  
-   `va_arg` 检索一个值的 `type` 从给定的位置 `arg_ptr`, ，、 增量 `arg_ptr` 若要使用的大小指向列表中的下一步参数 `type` 确定下一个参数从何处开始。 `va_arg` 可以是用于任意次数函数中，从列表中检索自变量。  
  
-   `va_copy` 在其当前状态生成的参数列表的副本。  `src` 参数必须已使用初始化 `va_start`; 它可能已使用的更新 `va_arg` 调用，但必须不已重置与 `va_end`。 通过检索下一个参数 `va_arg` 从 `dest` 从检索到的下一步自变量相同 `src`。  
  
-   检索所有自变量后， `va_end` 重置到指针 **NULL**。 `va_end` 必须对使用初始化每个自变量列表调用 `va_start` 或 `va_copy` 函数返回之前。  
  
> [!NOTE]
>  VARARGS 中的宏。H 被否决，并且是仅为保留向后与 ANSI C89 标准之前编写的代码兼容。 在所有其他情况下，在 STDARGS 中使用的宏。H。  
  
 它们使用的编译时 [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md), ，使用这些宏的程序可能生成意外的结果，由于本机和公共语言运行时 (CLR) 类型系统之间的差异。 请考虑此程序︰  
  
```  
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
}  
  
int main()  
{  
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int  
    testit(1, NULL);       // 2nd problem: NULL is not a char*  
}  
```  
  
 请注意， `testit` 第二个参数可以是以下之一应 `int` 或 `char*`。 传递的自变量是 0xffffffff ( `unsigned int`, ，而不 `int`) 和 `NULL` (实际 `int`, ，而不 `char*`)。 对于本机代码编译的程序时，它将生成此输出︰  
  
```Output  
-1  
  
(null)  
```  
  
 但是，程序编译使用 **/clr: pure**, ，类型不匹配会导致它生成异常。 解决方案是使用显式强制转换︰  
  
```  
int main()  
{  
   testit( 0, (int)0xFFFFFFFF ); // cast unsigned to int  
   testit( 1, (char*)NULL );     // cast int to char*  
}  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \<.h > 和 \< g.h >  
  
 **不推荐使用的标头︰** \< varargs.h >  
  
## <a name="libraries"></a>库  
 所有版本的 [C 运行时库](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_va.c  
/* Compile with: cl /W3 /Tc crt_va.c  
 * The program below illustrates passing a variable  
 * number of arguments using the following macros:  
 *      va_start            va_arg              va_copy  
 *      va_end              va_list  
 */  
  
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
  
## <a name="output"></a>输出  
  
```Output  
Deviation is: 0.816497  
Deviation is: 2.236068  
Deviation is: 0.000000  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 [System::ParamArrayAttribute 类](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)  
  
## <a name="see-also"></a>请参阅  
 [自变量访问](../../c-runtime-library/argument-access.md)   
 [vfprintf、 _vfprintf_l、 vfwprintf、 _vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)