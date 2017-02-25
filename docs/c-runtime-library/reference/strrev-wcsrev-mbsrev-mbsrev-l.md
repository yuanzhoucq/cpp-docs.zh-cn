---
title: "_strrev、_wcsrev、_mbsrev、_mbsrev_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsrev"
  - "_mbsrev"
  - "_strrev"
  - "_mbsrev_l"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strrev"
  - "_ftcsrev"
  - "_tcsrev"
  - "mbsrev"
  - "mbsrev_l"
  - "_wcsrev_fstrrev"
  - "_mbsrev"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsrev 函数"
  - "_mbsrev 函数"
  - "_mbsrev_l 函数"
  - "_strrev 函数"
  - "_tcsrev 函数"
  - "_wcsrev 函数"
  - "字符 [C++], 反转顺序"
  - "字符 [C++], 切换"
  - "ftcsrev 函数"
  - "mbsrev 函数"
  - "mbsrev_l 函数"
  - "反转字符串中的字符"
  - "字符串 [C++], 反向"
  - "strrev 函数"
  - "tcsrev 函数"
  - "wcsrev 函数"
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _strrev、_wcsrev、_mbsrev、_mbsrev_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

反转字符串的字符。  
  
> [!IMPORTANT]
>  `_mbsrev` 和 `_mbsrev_l` 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strrev(  
   char *str   
);  
wchar_t *_wcsrev(  
   wchar_t *str   
);  
unsigned char *_mbsrev(  
   unsigned char *str   
);  
unsigned char *_mbsrev_l(  
   unsigned char *str,  
   _locale_t locale   
);  
```  
  
#### 参数  
 `str`  
 反转的 null 终止的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向修改后的字符串的指针。  没有保留任何返回值以指示错误。  
  
## 备注  
 `_strrev` 函数反转在 `string` 中的字符排序。  终止空字符保持不变。  `_wcsrev` 和 `_mbsrev` 是宽字符，属于 `_strrev` 的多节字字符版本。  参数和 `_wcsrev` 的返回值是宽字符字符串；`_mbsrev` 的参数和返回值为多字节字符字符串。  对于 `_mbsrev`，在 `string` 中每个多字节字符的字节顺序不变。  否则这三个函数否则具有相同行为。  
  
 `_mbsrev`验证其参数。  如果`string1` 或 `string2`是空指针，则会调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行， `_mbsrev` 返回 `NULL`并设置`errno` 为 `EINVAL`。  `_strrev` 和 `_wcsrev` 不验证其参数。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  除了不具有使用当前区域的 `_l` 后缀以及具有 `_l` 后缀而不是使用传入的区域参数，这些函数的版本相同。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。  缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsrev`|`_strrev`|`_mbsrev`|`_wcsrev`|  
|**无**|**无**|`_mbsrev_l`|**无**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strrev`|\<string.h\>|  
|`_wcsrev`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsrev`, `_mbsrev_l`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strrev.c  
// This program checks a string to see  
// whether it is a palindrome: that is, whether  
// it reads the same forward and backward.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* string = "Able was I ere I saw Elba";  
   int result;  
  
   // Reverse string and compare (ignore case):  
   result = _stricmp( string, _strrev( _strdup( string ) ) );  
   if( result == 0 )  
      printf( "The string \"%s\" is a palindrome\n", string );  
   else  
      printf( "The string \"%s\" is not a palindrome\n", string );  
}  
```  
  
  **字符串“Able was I ere I saw Elba”是一个回文。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)