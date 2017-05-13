---
title: "putchar、putwchar | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- putchar
- putwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- putchar
- putwchar
- _puttchar
dev_langs:
- C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 1d1cf554b7d359c3bd761656df60881c4be514b8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="putchar-putwchar"></a>putchar、putwchar
将字符写入 **stdout**。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int putchar(  
   int c   
);  
wint_t putwchar(  
   wchar_t c   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要写入的字符。  
  
## <a name="return-value"></a>返回值  
 返回写入的字符。 若要指示错误或文件结尾条件，`putc` 和 `putchar` 返回 `EOF`；`putwc` 和 `putwchar` 返回 **WEOF**。 对于所有四种例程，使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 来检查是否存在错误或文件结尾。 如果为 `stream` 传递了空指针，则这些函数会生成一个无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回 `EOF` 或 **WEOF**，并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `putc` 例程会在当前位置将单个字符 `c` 写入输出 `stream`。 任何整数都可以传递给 `putc`，但是只写入低 8 位。 `putchar` 例程等同于 **putc(** `c`**, stdout )**。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 `putc` 和 `putchar` 分别与 `fputc` 和 `_fputchar` 类似，但是都作为函数和宏实现（请参阅[在函数和宏之间选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)）。 `putwc` 和 `putwchar` 分别是 `putc` 和 `putchar` 的宽字符版本。  
  
 后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttchar`|`putchar`|`putchar`|**putwchar**|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`putchar`|\<stdio.h>|  
|`putwchar`|\<stdio.h> 或 \<wchar.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_putchar.c  
/* This program uses putc to write buffer  
 * to a stream. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putchar( *p );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)
