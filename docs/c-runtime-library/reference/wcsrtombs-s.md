---
title: "wcsrtombs_s | Microsoft Docs"
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
  - "wcsrtombs_s"
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
  - "wcsrtombs_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符串转换, 宽字符"
  - "wcsrtombs_s 函数"
  - "宽字符, 字符串"
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcsrtombs_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将宽字符字符串转换为多字节字符串表示形式。  [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) 的一个版本提供安全增强功能，正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 要转换的字符数。  
  
 \[out\] `mbstr`  
 缓冲区为生成的转换多字节字符串的地址。  
  
 \[out\] `sizeInBytes`  
 `mbstr` 缓冲区的大小。  
  
 \[in\] `wcstr`  
 指向要转换的宽字符串。  
  
 \[in\] `count`  
 `mbstr` 缓冲区存储的最大字节数或者 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `mbstate`  
 指向`mbstate_t`转换状态对象的指针。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
|错误条件|返回值和`errno`|  
|----------|-----------------|  
|`mbstr` 是 `NULL` 和 `sizeInBytes` \> 0|`EINVAL`|  
|`wcstr` 为 `NULL`|`EINVAL`|  
|目标缓冲区因过小而无法包含转换的字符串。\(除非 `count` 是 `_TRUNCATE`；请参见下面"备注"\)|`ERANGE`|  
  
 如果任一错误状态发生，调用无效参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，函数返回错误代码然后按照下表设置 `errno`。  
  
## 备注  
 `wcsrtombs_s` 函数转换由 `wcstr` 指向的宽字节字符串到由 `mbstr`指向的缓冲区存储的多字符，该过程使用 `mbstate`包含的状态转换。  字符的转换将继续进行，直到与这些情况之一匹配：  
  
-   遇到空宽字符  
  
-   遇到不能转换宽字符  
  
-   `mbstr` 缓冲存储字节数等于 `count`。  
  
 目标字符串始终为 null 终止 \(即使发生错误\)。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，则当仍有 null 结束符的空间时，`wcsrtombs_s` 将许多字符串整合到目标缓冲区。  
  
 如果 `wcsrtombs_s` 成功转换了源字符串，它将转换字符串的字节的大小（包括空终止符）放入`*``pReturnValue`。\(提供的 `pReturnValue` 不是 `NULL`\)。  即使 `mbstr` 参数为 `NULL`, 并提供方法来确定需要的缓冲区大小，也会发生这个事件。  请注意，如果 `mbstr` 为 `NULL`，则 `count` 会被忽略。  
  
 如果遇到无法转换为多字节字符的 `wcsrtombs_s` 宽字符，将 `*``pReturnValue` 设置为\-1，将目标缓冲区为空字符串，请将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果由 `wcstr` 与 `mbstr` 指向的序列重叠，`wcsrtombs_s` 行为是未定义的。  `wcsrtombs_s` 受当前区域设置的 LC\_TYPE 类别的影响。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 无重叠，并且`count` 恰好指出要转换的宽字节字符的数量。  
  
 `wcsrtombs_s` 函数重启不同于 [wcstombs\_s、\_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) 。  转换状态存储在 `mbstate` 随后调用相同或其他可重新启动的函数。  当混淆重启和非重启函数的使用时，则结果未定义。  例如，如果随后调用 `wcsrtombs_s` 而不是 `wcstombs_s.`，则应用程序应使用 `wcsrlen` 而不是 `wcslen`。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 异常  
 只要当函数正在执行和 `mbstate` 为空时，在当前线程中无函数调用 `setlocale`时，`wcsrtombs_s` 函数是多线程安全的。  
  
## 示例  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
  **字符串转换成功。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcsrtombs_s`|\<wchar.h\>|  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)