---
title: "perror、_wperror | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wperror"
  - "perror"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wperror"
  - "_tperror"
  - "perror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tperror 函数"
  - "_wperror 函数"
  - "错误信息, 打印"
  - "perror 函数"
  - "打印错误消息"
  - "tperror 函数"
  - "wperror 函数"
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# perror、_wperror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

输出错误消息。  
  
## 语法  
  
```  
  
      void perror(  
   const char *string   
);  
void _wperror(  
   const wchar_t *string   
);  
```  
  
#### 参数  
 `string`  
 输出字符串消息。  
  
## 备注  
 `perror` 函数输出错误消息给 `stderr`。  `_wperror`是**\_perror**的宽字符版本；`_wperror`的 `string` 参数是宽字符字符串。  除此以外，`_wperror`和**\_perror**的行为完全相同。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的\_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tperror`|`perror`|`perror`|`_wperror`|  
  
 首先打印`string`，后面加上冒号，然后是导致错误的最后库调用的系统错误消息，最后是换行符。  如果 `string` 为 null 指针或指针指向空字符串，则 `perror` 仅打印系统错误消息。  
  
 错误号存储在变量[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) \(在 ERRNO.H中定义\)。  系统错误信息通过变量的 [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)获取，是一组消息命令错误数字。  `perror` 打印相应的错误消息，它使用 `errno` 值作为索引传递给 `_sys_errlist`。  变量 [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的值定义为 `_sys_errlist` 数组中元素的最大个数。  
  
 如果要产生正确结果，在库实例返回一个错误之后立刻调用 `perror`。  否则，后续调用会覆盖 `errno`值。  
  
 在 Windows 操作系统中，不使用`errno` ERRNO.H中列出的那些值。  这些值保留给 UNIX 操作系统使用。  关于Windows 操作系统使用的`errno` 值列表，请参见 [\_doserrno、errno、\_sys\_errlist 和\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  `perror`打印这些平台不使用`errno` 值的一个空字符串。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`perror`|\<stdio.h\> 或 \<stdlib.h\>|  
|`_wperror`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_perror.c  
// compile with: /W3  
/* This program attempts to open a file named  
 * NOSUCHF.ILE. Because this file probably doesn't exist,  
 * an error message is displayed. The same message is  
 * created using perror, strerror, and _strerror.  
 */  
  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh;  
  
   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )  
   {  
      /* Three ways to create error message: */  
      perror( "perror says open failed" );  
      printf( "strerror says open failed: %s\n",  
         strerror( errno ) ); // C4996  
      printf( _strerror( "_strerror says open failed" ) ); // C4996  
      // Note: strerror and _strerror are deprecated; consider  
      // using strerror_s and _strerror_s instead.  
   }  
   else  
   {  
      printf( "open succeeded on input file\n" );  
      _close( fh );  
   }  
}  
```  
  
## Output  
  
```  
perror says open failed: No such file or directory  
strerror says open failed: No such file or directory  
_strerror says open failed: No such file or directory  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [strerror、\_strerror、\_wcserror、\_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)