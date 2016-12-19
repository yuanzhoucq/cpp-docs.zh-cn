---
title: "vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vwprintf_s_l"
  - "vwprintf_s"
  - "_vprintf_s_l"
  - "vprintf_s"
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
  - "vprintf_s"
  - "vwprintf_s"
  - "_vtprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vprintf_s_l 函数"
  - "_vtprintf_s 函数"
  - "_vtprintf_s_l 函数"
  - "_vwprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "vprintf_s 函数"
  - "vprintf_s_l 函数"
  - "vtprintf_s 函数"
  - "vtprintf_s_l 函数"
  - "vwprintf_s 函数"
  - "vwprintf_s_l 函数"
ms.assetid: cf864996-a530-4b40-9c30-54c4cef439c8
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写使用指针参数列表的格式化输出。  [vprintf、\_vprintf\_l、vwprintf、\_vwprintf\_l](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
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
  
#### 参数  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 如果输出有错误，`vprintf_s`和 `vwprintf_s`返回编写的字符数，不包括终止空字符或负值。  如果 `format` 是空指针，或者，如果格式字符串包含无效格式字符，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个函数通过指针指向参数列表，然后布局和编写特定数据到`stdout`。  
  
 这些函数的安全版本与 `vprintf`和`vwprintf` 的不同之处仅在于安全版本检查包含有效格式字符的格式字符串。  
  
 `vwprintf_s` 是 `vprintf_s`的宽字符版本；如果流在 ANSI 模式下是公开的则两个函数具有相同行为。  `vprintf_s` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtprintf_s`|`vprintf_s`|`vprintf_s`|`vwprintf_s`|  
|`_vtprintf_s_l`|`_vprintf_s_l`|`_vprintf_s_l`|`_vwprintf_s_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`vprintf_s`, `_vprintf_s_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`vwprintf_s`, `_vwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)