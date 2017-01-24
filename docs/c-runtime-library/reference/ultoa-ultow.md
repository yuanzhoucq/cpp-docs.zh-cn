---
title: "_ultoa、_ultow | Microsoft Docs"
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
  - "_ultoa"
  - "_ultow"
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
  - "ultot"
  - "ultow"
  - "_ultoa"
  - "_ultow"
  - "_ultot"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ultoa 函数"
  - "_ultot 函数"
  - "_ultow 函数"
  - "转换整数"
  - "转换数字, 为字符串"
  - "整数, 转换"
  - "ultot 函数"
  - "ultow 函数"
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ultoa、_ultow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将无符号 long 整数转换为字符串。  提供这些函数的更多安全版本；请参见 [\_ultoa\_s、\_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)。  
  
## 语法  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
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
  
 `radix`  
 基于`value`*.*  
  
## 返回值  
 这些函数都返回一个指向 `str`的指针。  无错误返回。  
  
## 备注  
 `_ultoa` 函数将 `value` 转换为 null 终止字符字符串并将结果 \(33 字节\)存储到`str`。  不执行溢出检查。  `radix` 制定 `value` 的基；`radix` 必须是在 2 \- 36 范围之内。  `_ultow` 是 `_ultoa`的宽字符版本。  
  
> [!IMPORTANT]
>  为了避免缓冲区溢出，请确保 `str` 缓冲区足以容纳加后缀的空字符和符号字符的转换数字。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ultoa`|\<stdlib.h\>|  
|`_ultow`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 示例。  
  
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)