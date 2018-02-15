---
title: "putc、putwc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3c07cab44f6b709affa22f470dfd7a8840b729
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="putc-putwc"></a>putc、putwc
将字符写入流。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要写入的字符。  
  
 `stream`  
 指向**文件**结构的指针。  
  
## <a name="return-value"></a>返回值  
 返回写入的字符。 若要指示错误或文件结尾条件，`putc` 和 `putchar` 返回 `EOF`；`putwc` 和 `putwchar` 返回 **WEOF**。 对于所有四种例程，使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 来检查是否存在错误或文件结尾。 如果向 `stream` 传递的是空指针，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `EOF` 或 **WEOF**，并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `putc` 例程会在当前位置将单个字符 `c` 写入输出 `stream`。 任何整数都可以传递给 `putc`，但是只写入低 8 位。 `putchar` 例程等同于 **putc(** `c`**, stdout )**。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 `putc` 和 `putchar` 分别与 `fputc` 和 `_fputchar` 类似，但是都作为函数和宏实现（请参阅[在函数和宏之间选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)）。 `putwc` 和 `putwchar` 分别是 `putc` 和 `putchar` 的宽字符版本。 如果在 ANSI 模式下打开流，则 `putwc` 和 `putc` 的行为相同。 `putc` 当前不支持到 UNICODE 流中的输出。  
  
 后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 有关详细信息，请参阅 **_putc_nolock、_putwc_nolock**。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`putc`|\<stdio.h>|  
|`putwc`|\<stdio.h> 或 \<wchar.h>|  
  
通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄`stdin`， `stdout`，和`stderr`，必须将重定向，然后 C 运行时函数可以在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_putc.c  
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
   /* Make standard out the stream and write to it. */  
   stream = stdout;  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putc( *p, stream );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)