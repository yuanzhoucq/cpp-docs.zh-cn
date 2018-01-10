---
title: "fputc、fputwc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
dev_langs: C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06f9fb737ac57ad04a661eb0e8438b3d557c0e3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fputc-fputwc"></a>fputc、fputwc
将字符写入流。  
  
## <a name="syntax"></a>语法  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要写入的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 其中每个函数都会返回写入的字符。 对于 `fputc`，返回值 `EOF` 指示一个错误。 对于 `fputwc`，返回值 `WEOF` 指示一个错误。 如果 `stream` 为 `NULL`，这些函数则会调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数则返回 `EOF`，并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 其中每个函数将单个字符 `c` 在关联文件位置指示器（如果已定义）所指示的位置写入文件，并根据情况提升指示器。 情况下`fputc`和`fputwc`，与关联文件`stream`。 如果文件不支持定位请求，或在追加模式中打开，则该字符将被追加到流的末尾。  
  
 如果在 ANSI 模式下打开流，则这两个函数行为相同。 `fputc` 当前不支持到 UNICODE 流中的输出。  
  
 带 `_nolock` 后缀的版本相同，只不过它们可能受到其他线程的影响。 有关详细信息，请参阅 [_fputc_nolock、_fputwc_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md)。  
  
 下面是例程特定的备注。  
  
|例程所返回的值|备注|  
|-------------|-------------|  
|`fputc`|等效于 `putc`，但仅作为函数实现，而不是同时作为函数和宏实现。|  
|`fputwc`|`fputc` 的宽字符版本。 根据 `stream` 是在文本模式还是二进制模式中打开，将 `c` 编写为多字节字符或宽字符。|  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fputc`|\<stdio.h>|  
|`fputwc`|\<stdio.h> 或 \<wchar.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
```Output  
This is a test of fputc!!  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)