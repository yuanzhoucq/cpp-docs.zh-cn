---
title: "ungetc、ungetwc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d65453f1254e4c42658ef6f27d7c90d2ad0022b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ungetc-ungetwc"></a>ungetc、ungetwc
将字符重新推送到流上。  
  
## <a name="syntax"></a>语法  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要推送的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，其中每个函数将返回字符自变量`c`。 如果无法推送回 `c` 或未读取任何字符，则输入流不改变且 `ungetc` 返回 `EOF`；`ungetwc` 返回 `WEOF`。 如果 `stream` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回 `EOF` 或 `WEOF`并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `ungetc` 函数将字符 `c` 重新推送到 `stream` 上，并清除文件结尾指示符。 流必须打开以供读取。 在进行的后续读取操作`stream`开头`c`。 将忽略尝试使用 `ungetc` 将 `EOF` 重新推送到流上。  
  
 如果从流中读取此字符前调用了 `fflush`、`fseek`、`fsetpos`、或 `rewind`，则可能会消除 `ungetc` 在流上放置的字符。 文件位置指示符将拥有将字符推送回之前的值。 对应流的外部存储未改变。 对文本流的 `ungetc` 调用成功后，将不指定文件位置指示符，直至读取或弃用推送回的所有字符。 每次对二进制流的 `ungetc` 调用成功后，文件位置指示符将减少；如果调用前其值为 0，则调用后不定义此值。  
  
 如果调用了 `ungetc` 两次且在两次调用之间没有读取或文件定位操作，则结果不可预知。 调用 `fscanf` 后，对 `ungetc` 的调用可能会失败，除非已执行其他读取操作（例如 `getc`）。 这是因为 `fscanf` 自身会调用 `ungetc`。  
  
 `ungetwc` 是 `ungetc` 的宽字符版本。 但是，每次对文本或二进制流的 `ungetwc` 调用成功后，将不指定文件位置指示符的值，直至读取或弃用推送回的所有字符。  
  
 这些函数线程安全并会在执行期间锁定敏感数据。 有关非锁定版本，请参阅 [_ungetc_nolock、_ungetwc_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`ungetc`|\<stdio.h>|  
|`ungetwc`|\<stdio.h> 或 \<wchar.h>|  
  
通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄`stdin`， `stdout`，和`stderr`，必须将重定向，然后 C 运行时函数可以在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。
  
## <a name="example"></a>示例  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
```Output  
  
      521aNumber = 521  
Next character in stream = 'a'  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)