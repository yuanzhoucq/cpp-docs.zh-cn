---
title: "vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vfprintf_l"
  - "vfprintf"
  - "vfwprintf"
  - "_vfwprintf_l"
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
  - "vfwprintf"
  - "_vftprintf"
  - "vfprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vfwprintf_l 函数"
  - "_vftprintf 函数"
  - "vfprintf 函数"
  - "_vftprintf_l 函数"
  - "vfprintf_l 函数"
  - "vftprintf_l 函数"
  - "vfwprintf_l 函数"
  - "vftprintf 函数"
  - "vfwprintf 函数"
  - "_vfprintf_l 函数"
  - "格式化文本 [C++]"
ms.assetid: 4443be50-cedf-40b2-b3e2-ff2b3af3b666
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向参数列表的指针写入格式化的输出。 这些函数的更多安全版本存在;请参阅 [vfprintf_s、 _vfprintf_s_l、 vfwprintf_s、 _vfwprintf_s_l](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int vfprintf(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vfwprintf(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关详细信息，请参阅 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="return-value"></a>返回值  
 `vfprintf` 和 `vfwprintf` 返回写入的字符数，不包括终止 null 字符或为负值，如果发生输出错误。 如果任一 `stream` 或 `format` 是 null 指针，则调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些及其他错误代码的信息，请参阅 [_doserrno，errno，_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 其中每个函数采用指向自变量列表，然后格式化和写入到给定的数据 `stream`。  
  
 `vfwprintf` 是宽字符版本的 `vfprintf`; 如果在 ANSI 模式下打开流，则两个函数的行为完全相同。 `vfprintf` 当前不支持到 UNICODE 流中的输出。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftprintf`|`vfprintf`|`vfprintf`|`vfwprintf`|  
|`_vftprintf_l`|`_vfprintf_l`|`_vfprintf_l`|`_vfwprintf_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`vfprintf`, _`vfprintf_l`|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|  
|`vfwprintf`, _`vfwprintf_l`|\<stdio.h> 或 \<wchar.h> 以及 \<stdarg.h>|\<varargs.h>*|  
  
 \* 需要对 UNIX V 兼容性。  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md) 简介中。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、 _fprintf_l、 fwprintf、 _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、 _printf_l、 wprintf、 _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、 _sprintf_l、 swprintf、 _swprintf_l、 \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)