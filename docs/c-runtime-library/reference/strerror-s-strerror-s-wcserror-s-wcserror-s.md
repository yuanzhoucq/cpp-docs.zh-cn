---
title: "strerror_s、_strerror_s、_wcserror_s、__wcserror_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wcserror_s"
  - "_strerror_s"
  - "_wcserror_s"
  - "strerror_s"
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
  - "wcserror_s"
  - "__wcserror_s"
  - "_tcserror_s"
  - "_wcserror_s"
  - "tcserror_s"
  - "strerror_s"
  - "_strerror_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__wcserror_s 函数"
  - "_strerror_s 函数"
  - "_tcserror_s 函数"
  - "_wcserror_s 函数"
  - "错误信息, 获取"
  - "错误信息, 打印"
  - "打印错误消息"
  - "strerror_s 函数"
  - "tcserror_s 函数"
  - "wcserror_s 函数"
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strerror_s、_strerror_s、_wcserror_s、__wcserror_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取系统错误信息 \(`strerror_s`，`_wcserror_s`\) 或打印一个用户提供的错误消息 \(`_strerror_s`，`__wcserror_s`\)。  [strerror、\_strerror、\_wcserror、\_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
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
  
#### 参数  
 `buffer`  
 保存错误字符串的缓冲区。  
  
 `numberOfElements`  
 缓冲区大小  
  
 `errnum`  
 错误号。  
  
 `strErrMsg`  
 用户提供的消息  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### 错误情况  
  
|`buffer`|`numberOfElements`|`strErrMsg`|`buffer` 的内容|  
|--------------|------------------------|-----------------|------------------|  
|`NULL`|any|any|无|  
|any|0|any|未修改|  
  
## 备注  
 `strerror_s` 函数映射 `errnum` 到错误消息字符串，返回字符串 `buffer`。  `_strerror_s` 不采用错误号；它使用当前值 `errno` 确定相应的消息。  `strerror_s` 和 `_strerror_s` 实际上不打印消息：为此，您需要调用一种输出功能 \(如 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 如果 `strErrMsg` 是 `NULL`，`_strerror_s` 返回包含调用该生成错误最后一个库的系统错误信息的一个字符串 `buffer` 。  错误消息字符串由换行符 \(“\\n”\)终止。  如果 `strErrMsg` 与 `NULL`不相等，则 `_strerror_s` 返回包含（按顺序）您的字符串消息，冒号，空格，最后一个库调用产生错误的系统错误信息和换行符的 `buffer` 的一个字符串。  您的字符串消息可以是至多不超过94字符的长度。  
  
 如果其长度超过 `numberOfElements` \-1，这些功能截断错误消息。  在 `buffer` 的结果字符串始终以null结尾。  
  
 `_strerror_s` 的实际错误数量存储在变量 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。  系统错误信息通过变量的 [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)获取，是一组消息命令错误数字。  `_strerror_s` 通过使用 `errno` 值作为变量 `_sys_errlist`的索引来访问相应的错误消息。  变量 [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的值定义为 `_sys_errlist` 数组中元素的最大个数。  如果要产生正确结果，需要在库实例返回一个错误之后立刻调用 `_strerror_s`。  否则，后续调用 `strerror_s` 或 `_strerror_s` 会覆盖 `errno` 值。  
  
 `_wcserror_s` `和 __wcserror_s`  **分别为**  `strerror_s` 和 `_strerror_s`的宽字符版本。  
  
 这些函数验证其参数。  如果缓冲区是 `NULL` 或大小参数为0，无效参数处理程序被调用，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则函数返回 `EINVAL` 并设置 `errno` 为 `EINVAL`。  
  
 `_strerror_s, _wcserror_s,` 和 `__wcserror_s` 不是 ANSI 定义的部分，而是基于微软扩展到它。  需要移植的位置不要使用它们；对于 ANSI 兼容性，请使用 `strerror_s` 。  
  
 在 C\+\+ 中，使用这些功能由模板超载简化；超载可能自动推断缓冲区长度，而无需指定范围参数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strerror_s`, `_strerror_s`|\<string.h\>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[中将字符串转换成浮点数](../../c-runtime-library/reference/perror-wperror.md)示例。  
  
## .NET Framework 等效项  
 [System::Exception::Message](https://msdn.microsoft.com/en-us/library/system.exception.message.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)