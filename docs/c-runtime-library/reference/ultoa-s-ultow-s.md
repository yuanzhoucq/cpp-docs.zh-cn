---
title: "_ultoa_s、_ultow_s | Microsoft Docs"
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
  - "_ultow_s"
  - "_ultoa_s"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ultow_s"
  - "ultoa_s"
  - "ultow_s"
  - "_ultoa_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ultoa_s 函数"
  - "_ultow_s 函数"
  - "转换整数"
  - "转换数字, 为字符串"
  - "整数, 转换"
  - "ultoa_s 函数"
  - "ultow_s 函数"
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ultoa_s、_ultow_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将无符号 long 整数转换为字符串。  [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### 参数  
 `value`  
 数字可被转换.  
  
 `str`  
 字符串结果。  
  
 `sizeOfstr`  
 `str` 的大小对于`_ultoa_s` 为字节或对于 `_ultow_s`为字。  
  
 `radix`  
 `value`基。  
  
## 返回值  
 如果函数运行成功或代码错误，则为零。  
  
## 备注  
 `_ultoa_s` 函数将 `value` 的数值转换为 null 终止字符字符串并将结果 \(33 字节\)存储到`str`。  `radix` 参数指定了 `value`基，其值的范围必须是从 2 到 36。  `_ultow_s` 是 `_ultoa_s` 的宽字符版本；`_ultow_s` 的第二个参数是宽字符串。  
  
 如果`str` 是一个 `NULL` 指针， 或者如果 `sizeOfstr` 小于等于零，将调用无效参数处理程序， 正如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，这些函数返回 \-1 并将 `errno` 设置为 `EINVAL` 或如果 `value` 或 `str` 超出长整数范围，这些函数将返回 a\-1 并将 `errno` 设置为 `ERANGE`。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ultoa_s`|\<stdlib.h\>|  
|`_ultow_s`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)