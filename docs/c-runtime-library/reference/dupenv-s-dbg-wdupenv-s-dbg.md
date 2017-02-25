---
title: "_dupenv_s_dbg、_wdupenv_s_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_dupenv_s_dbg"
  - "_wdupenv_s_dbg"
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
  - "_tdupenv_s_dbg"
  - "_dupenv_s_dbg"
  - "_wdupenv_s_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tdupenv_s_dbg 函数"
  - "dupenv_s_dbg 函数"
  - "_wdupenv_s_dbg 函数"
  - "环境变量"
  - "tdupenv_s_dbg 函数"
  - "wdupenv_s_dbg 函数"
  - "_dupenv_s_dbg 函数"
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _dupenv_s_dbg、_wdupenv_s_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从当前环境获取值。[\_dupenv\_s、\_wdupenv\_s](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md) 版本分配内存给 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) 来附加调试信息。  
  
## 语法  
  
```  
errno_t _dupenv_s_dbg(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
errno_t _wdupenv_s_dbg(  
   wchar_t **buffer,  
   size_t * numberOfElements,  
   const wchar_t *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### 参数  
 `buffer`  
 存储变量值的缓冲区。  
  
 `numberOfElements`  
 `buffer`的大小。  
  
 `varname`  
 环境变量名  
  
 `blockType`  
 内存块的请求类型的：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 源文件名或 `NULL`的指针。  
  
 `linenumber`  
 源文件或 `NULL` 的行号。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
 如果 `buffer` 或 `varname` 是 `NULL`，这些函数验证他们的参数；调用无效参数处理程序,如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则函数将 `errno` 设置为 `EINVAL`，并返回 `EINVAL`。  
  
 如果这些函数不能分配足够的内存，这些设置 `buffer` 到 `NULL` 和设置 `numberOfElements` 为 0，并返回 `ENOMEM`。  
  
## 备注  
 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg`函数与 `_dupenv_s` 和 `_wdupenv_s`相同，除了当 `_DEBUG` 被定义时，这些函数使用[malloc](../../c-runtime-library/reference/malloc.md)，[\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) 的调试版本来给环境变量的值分配内存。  有关如何使用 `_malloc_dbg` 的调试特点的信息，请参见 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在许多情况下您不需要显式调用这些函数。  相反，你可以定义 `_CRTDBG_MAP_ALLOC` 标记。  当 `_CRTDBG_MAP_ALLOC` 被定义，调用 `_dupenv_s` 和 `_wdupenv_s` 重新绘制 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg`，分别，`blockType` 设置到  `_NORMAL_BLOCK`。  因此，你不用显示的调用这些函数除非你想标记堆块为 `_CLIENT_BLOCK`。  关于块类的详细信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tdupenv_s_dbg`|`_dupenv_s_dbg`|`_dupenv_s_dbg`|`_wdupenv_s_dbg`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_dupenv_s_dbg`|\<crtdbg.h\>|  
|`_wdupenv_s_dbg`|\<crtdbg.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_dupenv_s_dbg.c  
#include  <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## 示例输出  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## .NET Framework 等效项  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [环境常量](../../c-runtime-library/environmental-constants.md)   
 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)