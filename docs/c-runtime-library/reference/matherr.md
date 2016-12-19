---
title: "_matherr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_matherr"
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
  - "_matherr"
  - "matherr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_matherr 函数"
  - "matherr 函数"
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _matherr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数学错误处理。  
  
## 语法  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### 参数  
 *except*  
 指向包含消息信息的结构的指针。  
  
## 返回值  
 **matherr** 返回0表示错误或返回非零值表示成功。  如果\_**matherr** 返回 0，错误消息可能显示，并且 `errno` 设置为适当的错误值。  如果\_**matherr** 返回一个非零值，错误消息不会显示，并且不更改 `errno`。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 数学库的浮点函数生成\_的**matherr** 函数处理错误。  这些函数调用\_**matherr**，在检测到错误。  
  
 对于特定错误处理，可以提供的\_**matherr**不同的定义。  如果使用 C 运行库 \(Msvcr90.dll\) 的动态链接的版本，则可以用用户定义的版本替换在客户端执行的默认**matherr** \_例程。  但是，您不能替换在的 DLL Msvcr90.dll 客户端的默认 `_matherr` 实例。  
  
 当错误在算术例程时，**matherr** 调用\_与 **\_exception** 类型结构的指针 \(定义在 Math.h\) 作为参数。  该**\_exception**结构包含以下元素：  
  
 **int type**  
 异常类型。  
  
 **char \*name**  
 错误函数的名称。  
  
 **double arg1**，**arg2**  
 指向函数的第一个和第二个参数 \(如果有\)。  
  
 **double retval**  
 由函数返回的值。  
  
 **类型** 指定数学错误类型。  它是下列值之一，在 Math.h 定义。  
  
 `_DOMAIN`  
 域参数错误。  
  
 `_SING`  
 奇点参数。  
  
 `_OVERFLOW`  
 溢出范围错误都。  
  
 `_PLOSS`  
 重要部分丢失。  
  
 `_TLOSS`  
 发生全部有效位丢失。  
  
 `_UNDERFLOW`  
 结果太小而无法表示。目前不支持此属性。  
  
 结构成员 **name** 是指向包含导致错误函数名的 null 终止的字符串。  结构成员 **arg1** 和 **arg2** 指定导致错误值。\(如果只有一个参数为，它在 **arg1**中。\)  
  
 给定的默认返回值为 **retval\(V\)**。  如果更改返回值，所以必须指定错误是否实际发生了  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_matherr`|\<math.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_matherr.c  
/* illustrates writing an error routine for math   
 * functions. The error function must be:  
 *      _matherr  
 */  
  
#include <math.h>  
#include <string.h>  
#include <stdio.h>  
  
int main()  
{  
    /* Do several math operations that cause errors. The _matherr  
     * routine handles _DOMAIN errors, but lets the system handle  
     * other errors normally.  
     */  
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );  
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );  
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );  
}  
  
/* Handle several math errors caused by passing a negative argument  
 * to log or log10 (_DOMAIN errors). When this happens, _matherr  
 * returns the natural or base-10 logarithm of the absolute value  
 * of the argument and suppresses the usual error message.  
 */  
int _matherr( struct _exception *except )  
{  
    /* Handle _DOMAIN errors for log or log10. */  
    if( except->type == _DOMAIN )  
    {  
        if( strcmp( except->name, "log" ) == 0 )  
        {  
            except->retval = log( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
        else if( strcmp( except->name, "log10" ) == 0 )  
        {  
            except->retval = log10( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
    }  
    printf( "Normal: " );  
    return 0;    /* Else use the default actions */  
}  
```  
  
## Output  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [长双精度](../../misc/long-double.md)