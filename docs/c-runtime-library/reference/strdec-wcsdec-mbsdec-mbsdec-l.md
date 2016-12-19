---
title: "_strdec、_wcsdec、_mbsdec、_mbsdec_l | Microsoft Docs"
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
  - "_wcsdec"
  - "_strdec"
  - "_mbsdec"
  - "_mbsdec_l"
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
  - "_strdec"
  - "mbsdec_l"
  - "strdec"
  - "_mbsdec"
  - "_mbsdec_l"
  - "mbsdec"
  - "wcsdec"
  - "_wcsdec"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsdec 函数"
  - "_mbsdec_l 函数"
  - "_strdec 函数"
  - "_tcsdec 函数"
  - "_wcsdec 函数"
  - "mbsdec 函数"
  - "mbsdec_l 函数"
  - "strdec 函数"
  - "tcsdec 函数"
  - "wcsdec 函数"
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdec、_wcsdec、_mbsdec、_mbsdec_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个字符串指针后移一个字符  
  
> [!IMPORTANT]
>  `mbsdec` 和 `mbsdec_l` 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned char *_strdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned wchar_t *_wcsdec(  
   const unsigned wchar_t *start,  
   const unsigned wchar_t *current   
);  
unsigned char *_mbsdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned char *_mbsdec_l(  
   const unsigned char *start,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `start`  
 指向在源字符串中任意字符的指针 \(或对于 `_mbsdec` 和 \_`mbsdec_l`，任何多字节字符的第一个字节\) ；`start` 必须在源字符串的 `current` 之前。  
  
 `current`  
 指向在源字符串中任意字符的指针 \(或对于 `_mbsdec` 和 \_`mbsdec_l`，任何多字节字符的第一个字节\) ；`current` 必须在源字符串的 `start` 之后。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsdec`、\_`mbsdec_l`、`_strdec`和 `_wcsdec` 每返回一个指向先于 `current`的字符；如果 `start` 的值大于或等于该 `current`，`_mbsdec` 返回 `NULL`。  `_tcsdec` 映射到这些函数其中之一，其返回值取决于映射。  
  
## 备注  
 `_mbsdec` 和 `_mbsdec_l` 函数返回指向在包含`start` 字符串中的先于 `current` 的多字节字符的第一个字节的指针。  
  
 输出值受区域中的 `LC_CTYPE` 分类设置 的设置影响；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。`_mbsdec` 根据当前正在使用的区域设置识别多字节字符序列，而除了使用传入的区域设置参数不同外， `_mbsdec_l` 都是相同的。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `start` 或 `current` 为 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则这函数返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。  缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsdec`|`_strdec`|`_mbsdec`|`_wcsdec`|  
  
 `_strdec` 和 `_wcsdec` 分别是`_mbsdec` 和 `_mbsdec_l` 的单字节字符和宽字符版本。  `_strdec` 和 `_wcsdec` 仅为此映射提供，不应以其他方式使用。  
  
 有关更多信息，请参见[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_mbsdec`|\<mbstring.h\>|\<mbctype.h\>|  
|`_mbsdec_l`|\<mbstring.h\>|\<mbctype.h\>|  
|`_strdec`|\<tchar.h\>||  
|`_wcsdec`|\<tchar.h\>||  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 下面的示例演示了 `_tcsdec` 的一种用法。  
  
```  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main()  
{  
   const TCHAR *str = _T("12345");  
   cout << "str: " << str << endl;  
  
   const TCHAR *str2;  
   str2 = str + 2;  
   cout << "str2: " << str2 << endl;  
  
   TCHAR *answer;  
   answer = _tcsdec( str, str2 );  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
 下面的示例演示了 `_mbsdec` 的一种用法。  
  
```  
#include <iostream>  
#include <mbstring.h>  
using namespace std;  
  
int main()   
{   
   char *str = "12345";  
   cout << "str: " << str << endl;  
  
   char *str2;  
   str2 = str + 2;   
   cout << "str2: " << str2 << endl;  
  
   unsigned char *answer;  
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));  
  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strinc、\_wcsinc、\_mbsinc、\_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strnextc、\_wcsnextc、\_mbsnextc、\_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [\_strninc、\_wcsninc、\_mbsninc、\_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)