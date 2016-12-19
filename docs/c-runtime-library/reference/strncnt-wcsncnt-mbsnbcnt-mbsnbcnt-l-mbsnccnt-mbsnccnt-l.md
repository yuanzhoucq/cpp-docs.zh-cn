---
title: "_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l | Microsoft Docs"
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
  - "_mbsnbcnt_l"
  - "_mbsnccnt"
  - "_wcsncnt"
  - "_strncnt"
  - "_mbsnccnt_l"
  - "_mbsnbcnt"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbsnbcnt"
  - "wcsncnt"
  - "_tcsnbcnt"
  - "_mbsnccnt"
  - "_ftcsnbcnt"
  - "mbsnbcnt"
  - "strncnt"
  - "mbsnbcnt_l"
  - "mbsnccnt_l"
  - "mbsnccnt"
  - "_strncnt"
  - "_wcsncnt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcnt 函数"
  - "_mbsnbcnt_l 函数"
  - "_mbsnccnt 函数"
  - "_mbsnccnt_l 函数"
  - "_strncnt 函数"
  - "_tcsnbcnt 函数"
  - "_wcsncnt 函数"
  - "mbsnbcnt 函数"
  - "mbsnbcnt_l 函数"
  - "mbsnccnt 函数"
  - "mbsnccnt_l 函数"
  - "strncnt 函数"
  - "tcsnbcnt 函数"
  - "wcsncnt 函数"
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的计数中返回字符书或字节数。  
  
> [!IMPORTANT]
>  `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt`, `_mbsnccnt_l`不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### 参数  
 `str`  
 要修改的字符串。  
  
 `count`  
 在 `str`中检查字符数和字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 返回在 `str`多字节字符中第一个 `count` 找到字节数。  `_mbsnccnt` 和 `_mbsnccnt_l` 返回在 `str`多字节字符中第一个 `count` 找到字节数。  如果NULL在 `str` 检查完成之前，他们会在NULL字符之前返回找到的字节或者字符的数量。  如果 `str` 小于 `count`的 字符或字节数，它们返回该字符串的字符或字节数  如果 `count` 小于零，则返回 0。  在早期版本中，这些函数具有类型 `int` 的返回值而不是 `size_t`。  
  
 `_strncnt` 在单字节字符字符串 `str`的第一个 `count` 字节返回字符数。  `_wcsncnt` 在宽字符串 `str`的第一个宽字符`count`返回字符的数量。  
  
## 备注  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 返回在 `str`多字节字符中第一个 `count` 找到字节数。  `_mbsnbcnt` 和 `_mbsnbcnt_l` 替换 `mtob`，因此应在 `mtob`位置。  
  
 `_mbsnccnt` 和 `_mbsnccnt_l` 返回在 `str`多字节字符中第一个 `count` 找到字节数。  如果 `_mbsnccnt` 和 `_mbsnccnt_l` 在双字节字符的第二个字节会遇到 null，第一个字节也视为空且不包含在返回的计数值。  `_mbsnccnt` 和 `_mbsnccnt_l` 替换 `btom`，因此应在 `btom`位置。  
  
 如果 `str` 是空指针或是 `count` 为 0，这些函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述，`errno` 设置为 `EINVAL`，函数返回 0。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|--------|----------------------------|----------------|-------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbcnt`|\<mbstring.h\>|  
|`_mbsnbcnt_l`|\<mbstring.h\>|  
|`_mbsnccnt`|\<mbstring.h\>|  
|`_mbsnccnt_l`|\<mbstring.h\>|  
|`_strncnt`|\<tchar.h\>|  
|`_wcsncnt`|\<tchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## Output  
  
```  
The first 10 characters are single-byte.  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)