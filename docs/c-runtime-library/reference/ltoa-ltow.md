---
title: "_ltoa、_ltow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ltoa"
  - "_ltow"
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
  - "ltow"
  - "_ltot"
  - "_ltoa"
  - "_ltow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ltoa 函数"
  - "_ltow 函数"
  - "转换整数"
  - "转换数字, 为字符串"
  - "将长整型转换为字符串"
  - "ltoa 函数"
  - "ltow 函数"
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _ltoa、_ltow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将长整数转换为字符串。  提供这些函数的更多安全版本；请参见 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)。  
  
## 语法  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
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
 `value`基。  
  
## 返回值  
 这些函数都返回一个指向 `str`的指针。  无错误返回。  
  
## 备注  
 `_ltoa` 函数将 `value` 的数值转换为 null 终止字符字符串并将结果 \(33 字节\)存储到`str`。  `radix` 参数指定了 `value`基，其值的范围必须是从 2 到 36。  如果 `radix` 等于 10，并且 `value` 为负，则存储的字符串的第一个字符为减号 \(\-\)。  `_wsetlocale_ltow`  是 `_ltoa`  的宽字符版本，`_ltow` 和第二参数的返回值都是宽字符字符串。  这些函数中的每个计算机将是 Microsoft 的特定。  
  
> [!IMPORTANT]
>  为了避免缓冲区溢出，请确保 `str` 缓冲区足以容纳加后缀的 null 字符和符号字符的转换数字。  
  
 在 C\+\+ 中，这些函数有重载模板。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ltoa`|\<stdlib.h\>|  
|`_ltow`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 示例。  
  
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)