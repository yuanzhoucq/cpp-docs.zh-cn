---
title: "rand_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rand_s"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "rand_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "加密型安全随机数"
  - "生成伪随机数"
  - "数字, 生成伪随机"
  - "数字, 伪随机"
  - "伪随机数"
  - "rand_s 函数"
  - "随机数, 加密型安全"
  - "随机数, 生成"
ms.assetid: d6a0be60-997d-4904-8411-8aea6839cc94
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rand_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成一个伪随机数。  [rand](../../c-runtime-library/reference/rand.md) 的一个版本提供安全增强功能，正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
errno_t rand_s(   unsigned int* randomValue);  
```  
  
## 返回值  
 如果成功，则为零；否则为错误代码。  如果输入指针 `randomValue` 是null指针，则这些函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  如果函数为其他原因失败，\*`randomValue` 设置为 0。  
  
## 备注  
 `rand_s` 函数将在范围 0 的一伪随机整数为 `UINT_MAX` 输入为指针。  `rand_s` 函数使用操作系统生成加密随机数安全。  它不使用 [srand](../../c-runtime-library/reference/srand.md) 函数生成的种子，也不影响 `rand`使用的随机数的序列。  
  
 `rand_s` 函数在下列示例中的常量 `_CRT_RAND_S` 定义在中声明的函数包括之前，语句：  
  
```  
#define _CRT_RAND_S  
#include <stdlib.h>  
```  
  
 `rand_s` 依赖于 [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) API，只能在 Windows XP 和更高版本中提供。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`rand_s`|\<stdlib.h\>|  
  
 有关更多信息，请参见[Compatibility](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_rand_s.c  
// This program illustrates how to generate random  
// integer or floating point numbers in a specified range.  
  
// Remembering to define _CRT_RAND_S prior  
// to inclusion statement.  
#define _CRT_RAND_S  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <limits.h>  
  
int main( void )  
{  
    int             i;  
    unsigned int    number;  
    double          max = 100.0;  
    errno_t         err;  
  
    // Display 10 random integers in the range [ 1,10 ].  
    for( i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %u\n", (unsigned int) ((double)number /  
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);  
    }  
  
    printf_s("\n");  
  
    // Display 10 random doubles in [0, max).  
    for (i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %g\n", (double) number /   
                          ((double) UINT_MAX + 1) * max );  
    }  
}  
```  
  
## 示例输出  
  
```  
10  
4  
5  
2  
8  
2  
5  
6  
1  
1  
  
32.6617  
29.4471  
11.5413  
6.41924  
20.711  
60.2878  
61.0094  
20.1222  
80.9192  
65.0712  
```  
  
## .NET Framework 等效项  
 [系统唯一的类](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [srand](../../c-runtime-library/reference/srand.md)