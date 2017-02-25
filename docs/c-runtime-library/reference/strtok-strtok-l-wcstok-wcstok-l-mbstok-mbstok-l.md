---
title: "strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstok_l"
  - "_mbstok"
  - "wcstok"
  - "_mbstok"
  - "strtok"
  - "_wcstok_l"
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
  - "_mbstok"
  - "strtok"
  - "_tcstok"
  - "wcstok"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstok 函数"
  - "_mbstok_l 函数"
  - "_strtok_l 函数"
  - "_tcstok 函数"
  - "_tcstok_l 函数"
  - "_wcstok_l 函数"
  - "mbstok 函数"
  - "mbstok_l 函数"
  - "字符串 [C++], 搜索"
  - "strtok 函数"
  - "strtok_l 函数"
  - "tcstok 函数"
  - "tcstok_l 函数"
  - "标记, 在字符串中查找"
  - "wcstok 函数"
  - "wcstok_l 函数"
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用当前区域设置或通过的区域设置，查找在字符串中的下一个标记。  有关这些函数的更多安全版本，请参见 [strtok\_s、\_strtok\_s\_l、wcstok\_s、\_wcstok\_s\_l、\_mbstok\_s、\_mbstok\_s\_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbstok` 和 `_mbstok_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strtok(  
   char *strToken,  
   const char *strDelimit   
);  
wchar_t *wcstok(  
   wchar_t *strToken,  
   const wchar_t *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `strToken`  
 字符串包含一个标记或一个以上的标记。  
  
 `strDelimit`  
 分隔符的设置。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回在 `strToken`中指向下一个标记的指针。  当未找到其他标记时，它们返回 `NULL` 。  通过为返回标记后出现的第一个分隔符替换 `NULL` 字符，每个调用修改 `strToken` 。  
  
## 备注  
 `strtok` 函数来查找在 `strToken`的下一个标记。  `strDelimit`中字符的设置指定标记分隔符，该标记分隔符可能在当前调用的 `strToken` 中找到。  `wcstok` 和 `_mbstok` 是宽字符，属于 `strtok` 的多节字字符版本。  参数和 `wcstok` 的返回值是宽字符字符串；`_mbstok` 的参数和返回值为多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
> [!IMPORTANT]
>  这些函数会引起由缓冲区溢出问题带来的潜在威胁。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 在第一次调用 `strtok` 时，函数跳过前导分隔符并返回指向在 `strToken`的第一个标记的指针，以空字符终止标记。  通过一系列 `strtok` 的调用，多个标记将被从 `strToken` 的其余部分拆开。  每个 `strtok`调用通过插入 null 字符在该调用返回 `token` 之后修改`strToken`。  若要读取 `strToken`的下一个标记，请调用带有一个 `NULL` 值的 `strtok` `strToken` 参数。  `NULL` `strToken` 参数引起 `strtok` 搜索修改的 `strToken`中的下一个标记。  `strDelimit` 参数可以接收从一个调用到下一个的任何值，以便分隔符的设置可以更改。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
> [!NOTE]
>  每个函数为了解析字符串为记号使用一个线程局部静态变量。  因此，多个线程能够同时调用这些函数，而不会有意外的效果。  但是，在单线程中，交错调用这些函数很可能导致数据损坏和不正确的结果。  当分析不同的字符串，在开始分析下一个之前完成一个字符串的分析。  同时，请注意潜在的危险，当调用来自循环的这些函数中的某一个时，该循环中另一个函数被调用。  如果另外的函数停止使用这些函数中的某一个，一个交错的顺序调用将发生，触发数据损坏。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstok`|`strtok`|`_mbstok`|`wcstok`|  
|`_tcstok`|`_strtok_l`|`_mbstok_l`|`_wcstok_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strtok`|\<string.h\>|  
|`wcstok`|\<string.h\> 或 \<wchar.h\>|  
|`_mbstok`, `_mbstok_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strtok.c  
// compile with: /W3  
// In this program, a loop uses strtok  
// to print all the tokens (separated by commas  
// or blanks) in the string named "string".  
//  
#include <string.h>  
#include <stdio.h>  
  
char string[] = "A string\tof ,,tokens\nand some  more tokens";  
char seps[]   = " ,\t\n";  
char *token;  
  
int main( void )  
{  
   printf( "Tokens:\n" );  
  
   // Establish string and get the first token:  
   token = strtok( string, seps ); // C4996  
   // Note: strtok is deprecated; consider using strtok_s instead  
   while( token != NULL )  
   {  
      // While there are tokens in "string"  
      printf( " %s\n", token );  
  
      // Get next token:   
      token = strtok( NULL, seps ); // C4996  
   }  
}  
```  
  
  **标记：**  
 **A**  
 **string**  
 **的**  
 **标记**  
 **和**   
 **一些**  
 **more**  
 **标记**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)