---
title: "strerror_s、_strerror_s、_wcserror_s、__wcserror_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
dev_langs:
- C++
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791f9b7408fded070fe61206d4303c26c8926d3e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s
获取系统错误信息（`strerror_s`、 `_wcserror_s`）或打印用户提供的错误消息（`_strerror_s`、`__wcserror_s`）。 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [strerror、_strerror、_wcserror、\__wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 具有安全性增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 要保存错误字符串的缓冲区。  
  
 `numberOfElements`  
 缓冲区的大小。  
  
 `errnum`  
 错误号。  
  
 `strErrMsg`  
 用户提供的消息。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回零；如果失败，则返回错误代码。  
  
### <a name="error-condtions"></a>错误条件  
  
|`buffer`|`numberOfElements`|`strErrMsg`|`buffer` 的内容|  
|--------------|------------------------|-----------------|--------------------------|  
|`NULL`|任何|任何|n/a|  
|任何|0|任何|未修改|  
  
## <a name="remarks"></a>备注  
 `strerror_s` 函数将 `errnum` 映射到错误消息字符串，并返回 `buffer` 中的字符串。 `_strerror_s` 不采用错误编号；它使用 `errno` 的当前值来确定适当的消息。 实际上，`strerror_s` 和 `_strerror_s` 都不会打印该消息：若要打印消息，需要调用输出函数，例如 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)：  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 如果 `strErrMsg` 为 `NULL`，则 `_strerror_s` 将返回一个 `buffer` 中的字符串，该字符串包含生成错误的最后一个库调用的系统错误消息。 错误消息字符串以换行符 ('\n') 结尾。 如果 `strErrMsg` 不等于 `NULL`，则 `_strerror_s` 将返回一个 `buffer` 中的字符串，该字符串按顺序包含你的字符串消息、冒号、空格、生成错误的最后一个库调用的系统错误消息，以及换行符。 你的字符串消息长度最多可达 94 个字符。  
  
 如果错误消息的长度超过 `numberOfElements` -1，则这些函数将截断错误消息。 `buffer` 中的结果字符串始终以 null 结尾。  
  
 `_strerror_s` 的实际错误编号存储在 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 变量中。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 `_strerror_s` 通过将 `errno` 值用作变量 `_sys_errlist` 的索引来访问相应的错误消息。 变量 [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的值定义为 `_sys_errlist` 数组中元素的最大数。 若要生成准确的结果，请在库例程返回错误后立即调用 `_strerror_s`。 否则，对 `strerror_s` 或 `_strerror_s` 的后续调用可以覆盖 `errno` 值。  
  
 `_wcserror_s` 和 `__wcserror_s` 分别是 `strerror_s` 和 `_strerror_s` 的宽字符版本。  
  
 这些函数验证其参数。 如果缓冲区为 `NULL`，或如果大小参数为 0，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `EINVAL`，并且将 `errno` 设置为 `EINVAL`。  
  
 `_strerror_s``_wcserror_s`，和`__wcserror_s`不是 ANSI 定义的一部分而是改为 Microsoft 扩展。 请不要在需要可移植性的位置使用它们；若要获得 ANSI 兼容性，请改用 `strerror_s`。  
  
 在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`strerror_s`, `_strerror_s`|\<string.h>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [perror](../../c-runtime-library/reference/perror-wperror.md) 示例。  
  
## <a name="see-also"></a>请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)