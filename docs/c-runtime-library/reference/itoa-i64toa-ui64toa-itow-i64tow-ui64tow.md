---
title: "_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow | Microsoft Docs"
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
  - "_itow"
  - "_i64tow"
  - "_itoa"
  - "_i64toa"
  - "_ui64toa"
  - "_ui64tow"
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
  - "_i64tow"
  - "ui64toa"
  - "ui64tow"
  - "itot"
  - "_itot"
  - "_i64toa"
  - "_itoa"
  - "_itow"
  - "_ui64tow"
  - "i64toa"
  - "i64tow"
  - "itow"
  - "_ui64toa"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_i64toa 函数"
  - "_i64tow 函数"
  - "_itoa 函数"
  - "_itot 函数"
  - "_itow 函数"
  - "_ui64toa 函数"
  - "_ui64tow 函数"
  - "转换整数"
  - "转换数字, 为字符串"
  - "i64toa 函数"
  - "i64tow 函数"
  - "整数, 转换"
  - "itoa 函数"
  - "itot 函数"
  - "itow 函数"
  - "ui64toa 函数"
  - "ui64tow 函数"
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将整数转换为字符串。  有关这些函数的更多安全版本，请参见 [\_itoa\_s、\_i64toa\_s、\_ui64toa\_s、\_itow\_s、\_i64tow\_s、\_ui64tow\_s](../../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)。  
  
## 语法  
  
```  
char *_itoa(  
   int value,  
   char *str,  
   int radix   
);  
char *_i64toa(  
   __int64 value,  
   char *str,  
   int radix   
);  
char * _ui64toa(  
   unsigned _int64 value,  
   char *str,  
   int radix   
);  
wchar_t * _itow(  
   int value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_itoa(  
   int value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char *_i64toa(  
   __int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char * _ui64toa(  
   unsigned _int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _itow(  
   int value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
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
 基于`value`；必须在2\-36范围 之内。  
  
## 返回值  
 这些函数都返回一个指向 `str`的指针。  无错误返回。  
  
## 备注  
 `_itoa`、`_i64toa`和 `_ui64toa` 函数转换特定 `value` 参数的数字为 null 终止的字符串\) 并存储结果 \(最多33 个 `_itoa` 字符和最多65个 `_i64toa` 和 `_ui64toa`字符\) 在 `str`。  如果 `radix` 等于 10，并且 `value` 为负，则存储的字符串的第一个字符为减号 \( `–` \)。  `_itow`、`_i64tow`和 `_ui64tow` 分别为 `_itoa`、`_i64toa`和 `_ui64toa`的宽字符版本。  
  
> [!IMPORTANT]
>  为了避免缓冲区溢出，请确保 `str` 缓冲区足以容纳加后缀的 null 字符和符号字符的转换数字。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_itot`|`_itoa`|`_itoa`|`_itow`|  
|`_i64tot`|`_i64toa`|`_i64toa`|`_i64tow`|  
|`_ui64tot`|`_ui64toa`|`_ui64toa`|`_ui64tow`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_itoa`|\<stdlib.h\>|  
|`_i64toa`|\<stdlib.h\>|  
|`_ui64toa`|\<stdlib.h\>|  
|`_itow`|\<stdlib.h\>|  
|`_i64tow`|\<stdlib.h\>|  
|`_ui64tow`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_itoa.c  
// compile with: /W3  
// This program makes use of the _itoa functions  
// in various examples.  
  
#include <string.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[65];  
   int r;  
   for( r=10; r>=2; --r )  
   {  
     _itoa( -1, buffer, r ); // C4996  
     // Note: _itoa is deprecated; consider using _itoa_s instead  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _i64toa( -1L, buffer, r ); // C4996  
     // Note: _i64toa is deprecated; consider using _i64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _ui64toa( 0xffffffffffffffffL, buffer, r ); // C4996  
     // Note: _ui64toa is deprecated; consider using _ui64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
}  
```  
  
  **基础 10: \-1 \(2 个字符\)**  
**基础 9: 12068657453 \(11 个字符\)**  
**基础 8: 37777777777 \(11 个字符\)**  
**基础 7: 211301422353 \(12 个字符\)**  
**基础 6: 1550104015503 \(13 个字符\)**  
**基础 5: 32244002423140 \(14 个字符\)**  
**基础 4: 3333333333333333 \(16 个字符\)**  
**基础 3: 102002022201221111210 \(21 个字符\)**  
**基础 2: 11111111111111111111111111111111 \(32 个字符\)**  
**基础 10: \-1 \(2 个字符\)**  
**基础 9: 145808576354216723756 \(21 个字符\)**  
**基础 8: 1777777777777777777777 \(22 个字符\)**  
**基础 7: 45012021522523134134601 \(23 个字符\)**  
**基础 6: 3520522010102100444244423 \(25 个字符\)**  
**基础 5: 2214220303114400424121122430 \(28 个字符\)**  
**基础 4: 33333333333333333333333333333333 \(32 个字符\)**  
**基础 3: 11112220022122120101211020120210210211220 \(41 个字符\)**  
**基础 2: 1111111111111111111111111111111111111111111111111111111111111111 \(64 个字符\)**  
**基础 10: 18446744073709551615 \(20 个字符\)**  
**基础 9: 145808576354216723756 \(21 个字符\)**  
**基础 8: 1777777777777777777777 \(22 个字符\)**  
**基础 7: 45012021522523134134601 \(23 个字符\)**  
**基础 6: 3520522010102100444244423 \(25 个字符\)**  
**基础 5: 2214220303114400424121122430 \(28 个字符\)**  
**基础 4: 33333333333333333333333333333333 \(32 个字符\)**  
**基础 3: 11112220022122120101211020120210210211220 \(41 个字符\)**  
**基础 2: 1111111111111111111111111111111111111111111111111111111111111111 \(64 个字符\)**   
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ultoa\_s、\_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)