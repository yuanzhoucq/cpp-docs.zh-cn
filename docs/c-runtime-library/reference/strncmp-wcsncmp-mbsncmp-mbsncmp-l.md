---
title: "strncmp、wcsncmp、_mbsncmp、_mbsncmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
  - "_mbsncmp_l"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ftcsnccmp"
  - "_ftcsncmp"
  - "_tcsncmp"
  - "_tcsnccmp"
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsnccmp 函数"
  - "_ftcsncmp 函数"
  - "_mbsncmp 函数"
  - "_mbsncmp_l 函数"
  - "_tcsnccmp 函数"
  - "_tcsncmp 函数"
  - "字符 [C++], 比较"
  - "ftcsnccmp 函数"
  - "ftcsncmp 函数"
  - "mbsncmp 函数"
  - "mbsncmp_l 函数"
  - "字符串比较 [C++], strncmp 函数"
  - "字符串 [C++], 比较字符"
  - "strncmp 函数"
  - "tcsnccmp 函数"
  - "tcsncmp 函数"
  - "wcsncmp 函数"
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# strncmp、wcsncmp、_mbsncmp、_mbsncmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较高达两个字符串指定数量的字符。  
  
> [!IMPORTANT]
>  `_mbsncmp` 和 `_mbsncmp_l` 无法用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int strncmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int wcsncmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsncmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,   
   _locale_t locale  
);int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### 参数  
 `string1, string2`  
 要比较的字符串。  
  
 `count`  
 要比较的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回值指示 `string1` 和 `string2` 的子字符串之间关系，如下所示。  
  
|返回值|描述|  
|---------|--------|  
|\< 0|`string1` 的子字符串小于 `string2` 的子字符串|  
|0|`string1` 的子字符串等于 `string2` 的子字符串|  
|\> 0|`string1` 的子字符串大于 `string2` 的子字符串|  
  
 参数验证错误时，`_mbsncmp` 和 `_mbsncmp_l` 返回 `_NLSCMPERROR`，该返回值是在 \<string.h\> 和 \<mbstring.h\> 中定义的。  
  
## 备注  
 `strncmp` 函数对 `count` 和 `string1` 中最多前 `string2` 个字符执行序号比较，并返回一个指示子字符串之间关系的值。  `strncmp` 是 `_strnicmp` 的一个区分大小写的版本。  `wcsncmp` 和 `_mbsncmp` 是 `_wcsnicmp` 和 `_mbsnicmp` 的一个区分大小写的版本。  
  
 `wcsncmp` 和 `_mbsncmp` 是 `strncmp` 的宽字符和多字节字符版本。  `wcsncmp` 的参数是宽字符字符串；而 `_mbsncmp` 的则是多字节字符字符串。  `_mbsncmp` 根据多字节代码页识别多字节字符序列，并在发生错误时返回 `_NLSCMPERROR`。  
  
 此外，`_mbsncmp` 和 `_mbsncmp_l` 验证参数。  如果 `string1` 或 `string2` 是空指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则 `_mbsncmp` 和 `_mbsncmp_l` 返回 `_NLSCMPERROR`，并将 `errno` 设置为 `EINVAL`。  `strncmp` 和 `wcsncmp` 不会验证其参数。  否则这些函数具有相同行为。  
  
 `_mbsncmp` 和 `_mbsncmp_l` 的比较行为受到区域设置的 `LC_CTYPE` 类别设置的设置影响。  这会控制对多字节字符的前导和尾随字节的检测。  有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `_mbsncmp` 函数对与区域设置相关的行为使用当前区域设置。  `_mbsncmp_l` 函数完全相同，只不过它转而使用 `locale` 参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  如果区域设置是单字节的，则这些函数的行为等同于 `strncmp`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnccmp`|`strncmp`|`_mbsncmp`|`wcsncmp`|  
|`_tcsncmp`|`strncmp`|`_mbsnbcmp`|`wcsncmp`|  
|`_tccmp`|映射到宏或内联函数|`_mbsncmp`|映射到宏或内联函数|  
|**不适用**|**不适用**|`_mbsncmp_l`|**不适用**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strncmp`|\<string.h\>|  
|`wcsncmp`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncmp`, `_mbsncmp_l`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strncmp.c  
#include <string.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n      %s\n      %s\n\n",  
           string1, string2 );  
   printf( "Function:   strncmp (first 10 characters only)\n" );  
   result = strncmp( string1, string2 , 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n\n", tmp );  
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );  
   result = _strnicmp( string1, string2, 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n", tmp );  
}  
```  
  
  **比较字符串：**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown fox jumps over the lazy dog**  
**函数：strncmp（仅比较前 10 个字符）**  
**结果：字符串 1 大于字符串 2**  
**函数：strnicmp \_strnicmp（仅比较前 10 个字符）**  
**结果：字符串 1 等于字符串 2**   
## .NET Framework 等效项  
 [System::String::Compare](frlrfSystemStringClassCompareTopic)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)