---
title: "vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vwprintf_s_l
- vwprintf_s
- _vprintf_s_l
- vprintf_s
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
- vprintf_s
- vwprintf_s
- _vtprintf_s
dev_langs:
- C++
helpviewer_keywords:
- vwprintf_s_l function
- _vwprintf_s_l function
- vwprintf_s function
- _vtprintf_s_l function
- vprintf_s_l function
- vtprintf_s_l function
- _vtprintf_s function
- vtprintf_s function
- _vprintf_s_l function
- formatted text [C++]
- vprintf_s function
ms.assetid: cf864996-a530-4b40-9c30-54c4cef439c8
caps.latest.revision: 20
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
ms.openlocfilehash: 51c8be555df33252cb35465fc11fe13e06d17485
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="vprintfs-vprintfsl-vwprintfs-vwprintfsl"></a>vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l
使用指向参数列表的指针编写格式化输出。 这些版本的 [vprintf、_vprintf_l、vwprintf、_vwprintf_l](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
int vprintf_s(  
   const char *format,  
   va_list argptr   
);  
int _vprintf_s_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vwprintf_s(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vwprintf_s_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>参数  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关详细信息，请参阅[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="return-value"></a>返回值  
 `vprintf_s` 和 `vwprintf_s` 返回写入的字符数，不包括终止的 null 字符；如果发生输出错误，则返回负值。 如果 `format` 为 null 指针，或如果格式字符串包含无效格式字符，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 每个函数均采用一个指向参数列表的指针，然后将给定数据格式化并写入到 `stdout`。  
  
 这些函数的安全版本与 `vprintf` 和 `vwprintf` 的差异仅在于格式字符串包含有效格式化字符的安全版本检查。  
  
 `vwprintf_s` 是 `vprintf_s` 的宽字符版本；如果在 ANSI 模式下打开流，则这两个函数的行为相同。 `vprintf_s` 当前不支持到 UNICODE 流中的输出。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtprintf_s`|`vprintf_s`|`vprintf_s`|`vwprintf_s`|  
|`_vtprintf_s_l`|`_vprintf_s_l`|`_vprintf_s_l`|`_vwprintf_s_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`vprintf_s`, `_vprintf_s_l`|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|  
|`vwprintf_s`, `_vwprintf_s_l`|\<stdio.h> 或 \<wchar.h> 和 \<stdarg.h>|\<varargs.h>*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、va_copy、va_end、va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
