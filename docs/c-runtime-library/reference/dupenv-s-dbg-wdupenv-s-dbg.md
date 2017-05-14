---
title: "_dupenv_s_dbg、_wdupenv_s_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
dev_langs:
- C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: 9
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
ms.openlocfilehash: b478e11cb4b3b04d92a693fca85cd6257b594514
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg、_wdupenv_s_dbg
从当前环境中获取值。  [_dupenv_s、_wdupenv_s](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md) 的版本，使用 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) 来分配内存，以提供其他调试信息。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `buffer`  
 用于存储变量值的缓冲区。  
  
 `numberOfElements`  
 
          `buffer` 的大小。  
  
 `varname`  
 环境变量名称。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向源文件名称的指针或 `NULL`。  
  
 `linenumber`  
 源文件中的行号或 `NULL`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
 这些函数将验证其参数；如果 `buffer` 或 `varname` 是 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 如果这些函数无法分配足够的内存，则它们会将 `buffer` 设置为 `NULL` 并将 `numberOfElements` 设置为 0，然后返回 `ENOMEM`。  
  
## <a name="remarks"></a>备注  
 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg` 函数与 `_dupenv_s` 和 `_wdupenv_s` 完全相同，只是当定义 `_DEBUG` 时，这些函数将使用 [malloc](../../c-runtime-library/reference/malloc.md) 和 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) 的调试版本来为环境变量的值分配内存。 有关 `_malloc_dbg` 调试功能的信息，请参阅 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。 可以改为定义标志 `_CRTDBG_MAP_ALLOC`。 定义 `_CRTDBG_MAP_ALLOC` 后，对 `_dupenv_s` 和 `_wdupenv_s` 的调用将分别重新映射到 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。 因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。 有关块类型的详细信息，请参阅[调试堆中的块类型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s_dbg`|`_dupenv_s_dbg`|`_dupenv_s_dbg`|`_wdupenv_s_dbg`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_dupenv_s_dbg`|\<crtdbg.h>|  
|`_wdupenv_s_dbg`|\<crtdbg.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="sample-output"></a>示例输出  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [环境常量](../../c-runtime-library/environmental-constants.md)   
 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s、_wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)
