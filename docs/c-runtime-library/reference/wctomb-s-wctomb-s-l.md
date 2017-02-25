---
title: "wctomb_s、_wctomb_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wctomb_s_l"
  - "wctomb_s"
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
  - "wctomb_s"
  - "_wctomb_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wctomb_s_l 函数"
  - "字符, 转换"
  - "字符串转换, 多字节字符串"
  - "字符串转换, 宽字符"
  - "wctomb_s 函数"
  - "wctomb_s_l 函数"
  - "宽字符, 转换"
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# wctomb_s、_wctomb_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个宽字符转换为相应的多字节字符。  [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 的一个版本提供安全增强功能，正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### 参数  
 \[out\] `pRetValue`  
 字节数或者指示结果的代码。  
  
 \[out\] `mbchar`  
 一个多字节字符的地址。  
  
 \[in\] `sizeInBytes`  
 `mbchar` 缓冲区的大小。  
  
 \[in\] `wchar`  
 一个宽字符。  
  
 \[in\] `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
 错误情况  
  
|`mbchar`|`sizeInBytes`|返回值|`pRetValue`|  
|--------------|-------------------|---------|-----------------|  
|`NULL`|\>0|`EINVAL`|未修改|  
|any|\>`INT_MAX`|`EINVAL`|未修改|  
|any|太小|`EINVAL`|未修改|  
  
 如果任一以上错误状态发生，调用无效参数句柄，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行， `wctomb` 返回 `EINVAL`并设置`errno` 为 `EINVAL`。  
  
## 备注  
 `wctomb_s` 函数将其 `wchar` 参数转换为对应的多字节字符并将结果存储在 `mbchar`。  在所有程序可以调用从任意点的函数。  
  
 如果 `wctomb_s` 将宽字符转换为多字节字符，将在宽字符中的字节数 \(不大于`MB_CUR_MAX`\) 转换为通过 `pRetValue` 指向的整数。  如果 `wchar` 是宽字符空字符 \(L' \\ 0 '\) ，`wctomb_s` 用 1 来填充 `pRetValue`。  如果目标指针 `mbchar` 为空，则`wctomb_s` 将 0 放入 `pRetValue`。  如果在当前语言环境中不能转换，在`wctomb_s` 在 `pRetValue` 放置 \- 1。  
  
 `wctomb_s` 为语言环境相关信息使用当前语言环境；`_wctomb_s_l` 相同，除了它将传递的语言环境。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wctomb_s`|\<stdlib.h\>|  
|`_wctomb_s_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此程序阐述 `wctomb` 函数的行为。  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
  **转换宽字符：**  
 **已转换的字符：1**  
 **多字节字符：a**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)