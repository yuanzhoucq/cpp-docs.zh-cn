---
title: "_matherr | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _matherr
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
- _matherr
- matherr
dev_langs:
- C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: bd2ab4ac1c6772a06a2da6ac15f7f4b29f83c120
ms.lasthandoff: 02/24/2017

---
# <a name="matherr"></a>_matherr
处理数学错误。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### <a name="parameters"></a>参数  
 *except*  
 指向包含错误信息的结构的指针。  
  
## <a name="return-value"></a>返回值  
 _**matherr** 将返回 0 指示错误，或返回非零值指示成功。 如果 \_**matherr** 返回 0，则可能显示错误消息，并且 `errno` 将设置为适当的错误值。 如果 \_**matherr** 返回非零值，则将不会显示错误消息，并且 `errno` 将保持不变。  
  
 有关返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 _**matherr** 函数将处理数学库的浮点函数生成的错误。 检测到错误时这些函数将调用 \_**matherr**。  
  
 对于特定错误处理，可以为 _**matherr** 提供不同定义。 如果你使用 C 运行库 (Msvcr90.dll) 的动态链接版本，则可以将客户端可执行文件中的默认 \_**matherr** 例程替换为用户定义的版本。 但是，您不能替换 Msvcr90.dll 的 DLL 客户端中的默认 `_matherr` 例程。  
  
 如果数学例程中出错，则将使用作为自变量的指向 **_exception** 类型结构（在 Math.h 中定义）的指针调用 _**matherr**。 **_exception** 结构包含下列元素。  
  
 **int type**  
 异常类型。  
  
 **char \*name**  
 出错函数的名称。  
  
 **double arg1**、**arg2**  
 函数的第一个和第二个自变量（如果有）。  
  
 **double retval**  
 函数返回的值。  
  
 **type** 指定数学错误的类型。 它是下列在 Math.h 中定义的值之一。  
  
 `_DOMAIN`  
 自变量域错误。  
  
 `_SING`  
 自变量奇点。  
  
 `_OVERFLOW`  
 溢出范围错误。  
  
 `_PLOSS`  
 基数部分丢失。  
  
 `_TLOSS`  
 基数全部丢失。  
  
 `_UNDERFLOW`  
 结果太小无法表示。 （目前不支持此条件。）  
  
 结构成员 **name** 是指针，指向包含导致错误的函数名称的以 null 结尾的字符串。 结构成员 **arg1** 和 **arg2** 指定导致错误的值。 （如果只提供一个参数，则它将存储在 **arg1** 中。）  
  
 给定错误的默认返回值为 **retval**。 如果更改返回值，则必须指定是否实际出现了错误。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_matherr`|\<math.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="output"></a>输出  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
