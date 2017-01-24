---
title: "_itoa_s、_i64toa_s、_ui64toa_s、_itow_s、_i64tow_s、_ui64tow_s | Microsoft Docs"
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
  - "_ui64tow_s"
  - "_itoa_s"
  - "_itow_s"
  - "_ui64toa_s"
  - "_i64tow_s"
  - "_i64toa_s"
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
  - "i64tot_s"
  - "itow_s"
  - "_ui64tow_s"
  - "_itow_s"
  - "ui64tot_s"
  - "_ui64toa_s"
  - "itoa_s"
  - "_i64tow_s"
  - "_i64tot_s"
  - "_itot_s"
  - "_i64toa_s"
  - "_itoa_s"
  - "ui64toa_s"
  - "i64toa_s"
  - "_ui64tot_s"
  - "i64tow_s"
  - "itot_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_i64toa_s 函数"
  - "_i64tot_s 函数"
  - "_i64tow_s 函数"
  - "_itoa_s 函数"
  - "_itot_s 函数"
  - "_itow_s 函数"
  - "_ui64toa_s 函数"
  - "_ui64tot_s 函数"
  - "_ui64tow_s 函数"
  - "转换整数"
  - "转换数字, 为字符串"
  - "i64toa_s 函数"
  - "i64tow_s 函数"
  - "整数, 转换"
  - "itoa_s 函数"
  - "itow_s 函数"
  - "ui64toa_s 函数"
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _itoa_s、_i64toa_s、_ui64toa_s、_itow_s、_i64tow_s、_ui64tow_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将整数转换为字符串。  [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _itoa_s(  
   int value,  
   char *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
errno_t _i64toa_s(  
   __int64 value,  
   char *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
errno_t _ui64toa_s(  
   unsigned _int64 value,  
   char *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
errno_t _itow_s(  
   int value,  
   wchar_t *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
errno_t _i64tow_s(  
   __int64 value,  
   wchar_t *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
errno_t _ui64tow_s(  
   unsigned __int64 value,  
   wchar_t *buffer,  
   size_t sizeInCharacters,  
   int radix   
);  
template <size_t size>  
errno_t _itoa_s(  
   int value,  
   char (&buffer)[size],  
   int radix   
); // C++ only  
template <size_t size>  
errno_t _itow_s(  
   int value,  
   wchar_t (&buffer)[size],  
   int radix   
); // C++ only  
```  
  
#### 参数  
 \[in\] `value`  
 数字可被转换.  
  
 \[out\] `buffer`  
 填充转换的结果。  
  
 \[in\] `sizeInCharacters`  
 单字节字符或宽字符的缓冲区的大小。  
  
 \[in\] `radix`  
 基于`value`；必须在2\-36范围 之内。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  如果满足以下任一条件应用，函数调用参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
### 错误情况  
  
|值|buffer|sizeInCharacters|radix|返回|  
|-------|------------|----------------------|-----------|--------|  
|any|`NULL`|any|any|`EINVAL`|  
|any|any|\<\=0|any|`EINVAL`|  
|any|any|\<\= 需要的结果字符串的长度|any|`EINVAL`|  
|any|any|any|`radix` \< 2 或 `radix` \> 36|`EINVAL`|  
  
 **安全问题**  
  
 这些函数将生成访问冲突，如果 `buffer` 不指向有效的内存并且不为 `NULL`，或者，如果该缓冲区的长度不足够长以保存结果字符串。  
  
## 备注  
 除了参数和返回值，`_itoa_s` 函数具有和对应较不安全版本的相同行为。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_itot_s`|`_itoa_s`|`_itoa_s`|`_itow_s`|  
|`_i64tot_s`|`_i64toa_s`|`_i64toa_s`|`_i64tow_s`|  
|`_ui64tot_s`|`_ui64toa_s`|`_ui64toa_s`|`_ui64tow_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_itoa_s`|\<stdlib.h\>|  
|`_i64toa_s`|\<stdlib.h\>|  
|`_ui64toa_s`|\<stdlib.h\>|  
|`_itow_s`|\<stdlib.h\> 或 \<wchar.h\>|  
|`_i64tow_s`|\<stdlib.h\> 或 \<wchar.h\>|  
|`_ui64tow_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_itoa_s.c  
#include <stdlib.h>  
#include <string.h>  
  
int main( void )  
{  
    char buffer[65];  
    int r;  
    for( r=10; r>=2; --r )  
    {  
       _itoa_s( -1, buffer, 65, r );  
       printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
    }  
    printf( "\n" );  
    for( r=10; r>=2; --r )  
    {  
       _i64toa_s( -1L, buffer, 65, r );  
       printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
    }  
    printf( "\n" );  
    for( r=10; r>=2; --r )  
    {  
       _ui64toa_s( 0xffffffffffffffffL, buffer, 65, r );  
       printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
    }  
}  
```  
  
## Output  
  
```  
base 10: -1 (2 chars)  
base 9: 12068657453 (11 chars)  
base 8: 37777777777 (11 chars)  
base 7: 211301422353 (12 chars)  
base 6: 1550104015503 (13 chars)  
base 5: 32244002423140 (14 chars)  
base 4: 3333333333333333 (16 chars)  
base 3: 102002022201221111210 (21 chars)  
base 2: 11111111111111111111111111111111 (32 chars)  
  
base 10: -1 (2 chars)  
base 9: 145808576354216723756 (21 chars)  
base 8: 1777777777777777777777 (22 chars)  
base 7: 45012021522523134134601 (23 chars)  
base 6: 3520522010102100444244423 (25 chars)  
base 5: 2214220303114400424121122430 (28 chars)  
base 4: 33333333333333333333333333333333 (32 chars)  
base 3: 11112220022122120101211020120210210211220 (41 chars)  
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)  
  
base 10: 18446744073709551615 (20 chars)  
base 9: 145808576354216723756 (21 chars)  
base 8: 1777777777777777777777 (22 chars)  
base 7: 45012021522523134134601 (23 chars)  
base 6: 3520522010102100444244423 (25 chars)  
base 5: 2214220303114400424121122430 (28 chars)  
base 4: 33333333333333333333333333333333 (32 chars)  
base 3: 11112220022122120101211020120210210211220 (41 chars)  
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)  
```  
  
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)