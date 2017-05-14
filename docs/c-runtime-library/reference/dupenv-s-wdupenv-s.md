---
title: "_dupenv_s、_wdupenv_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
dev_langs:
- C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 3332c33e2d2b79106cf88f143fe99cb91bbce670
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s、_wdupenv_s
从当前环境中获取值。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _dupenv_s(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname  
);  
errno_t _wdupenv_s(  
   wchar_t **buffer,  
   size_t *numberOfElements,  
   const wchar_t *varname  
);  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 用于存储变量值的缓冲区。  
  
 `numberOfElements`  
 
          `buffer` 的大小。  
  
 `varname`  
 环境变量名称。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
 这些函数将验证其参数；如果 `buffer` 或 `varname` 是 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 如果这些函数无法分配足够的内存，则它们会将 `buffer` 设置为 `NULL` 并将 `numberOfElements` 设置为 0，然后返回 `ENOMEM`。  
  
## <a name="remarks"></a>备注  
 `_dupenv_s` 函数将搜索 `varname` 的环境变量列表。 如果找到变量，则 `_dupenv_s` 将分配缓冲区并将变量值复制到该缓冲区中。 缓冲区的地址和长度将在 `buffer` 和 `numberOfElements` 中返回。 通过分配缓冲区本身，`_dupenv_s` 为 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) 提供了更方便的替代方法。  
  
> [!NOTE]
>  调用程序负责通过调用 [free](../../c-runtime-library/reference/free.md) 释放内存。  
  
 如果未找到变量，则将 `buffer` 设置为 `NULL`、将 `numberOfElements` 设置为 0，并且返回值是 0，因为未将这种情况视为错误条件。  
  
 如果你对缓冲区大小不感兴趣，你可以将 `NULL` 传递给 `numberOfElements`。  
  
 在 Windows 操作系统中，`_dupenv_s` 不区分大小写。 `_dupenv_s` 使用由全局变量 `_environ` 指向的环境副本来访问该环境。 请参阅备注中的 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)，了解有关 `_environ` 的讨论。  
  
 `buffer` 中的值是环境变量值的副本；修改它不会影响环境。 请使用 [_putenv_s、_wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md) 函数修改环境变量的值。  
  
 `_wdupenv_s` 是 `_dupenv_s` 的宽字符版本；`_wdupenv_s` 的参数是宽字符字符串。 `_wenviron` 全局变量是 `_environ` 的宽字符版本。 请参阅备注中的 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)了解有关 `_wenviron` 的详细信息。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s`|`_dupenv_s`|`_dupenv_s`|`_wdupenv_s`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_dupenv_s`|\<stdlib.h>|  
|`_wdupenv_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_dupenv_s.c  
#include  <stdlib.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );  
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
 [_dupenv_s_dbg、_wdupenv_s_dbg](../../c-runtime-library/reference/dupenv-s-dbg-wdupenv-s-dbg.md)   
 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s、_wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)
