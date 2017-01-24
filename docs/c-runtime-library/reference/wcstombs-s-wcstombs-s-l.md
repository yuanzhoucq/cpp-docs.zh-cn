---
title: "wcstombs_s、_wcstombs_s_l | Microsoft Docs"
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
  - "_wcstombs_s_l"
  - "wcstombs_s"
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
  - "wcstombs_s"
  - "_wcstombs_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcstombs_s 函数"
  - "字符串转换, 宽字符"
  - "将转换的宽字符"
  - "_wcstombs_s_l 函数"
  - "wcstombs_s_l 函数"
  - "将转换的字符"
  - "字符串转换，多字节字符字符串"
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcstombs_s、_wcstombs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将宽字符序列转换为对应的多字节字符序列。 版本 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 要转换的字符数。  
  
 \[out\] `mbstr`  
 生成的已转换多字节字符字符串的缓冲区的地址。  
  
 \[\] in`sizeInBytes`  
 缓冲区 `mbstr` 的大小（以字节为单位）。  
  
 \[in\] `wcstr`  
 指向要转换的宽字符字符串的指针。  
  
 \[in\] `count`  
 个字节的存储中的最大数 `mbstr` 缓冲区，不包括终止 null 字符，或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功则为零，失败则返回错误代码。  
  
|错误条件|返回值和 `errno`|  
|----------|------------------|  
|`mbstr` 是 `NULL` 和 `sizeInBytes` \> 0|`EINVAL`|  
|`wcstr` 为 `NULL`|`EINVAL`|  
|目标缓冲区过小，无法包含转换的字符串（除非 `count` 是 `_TRUNCATE`；请参阅下面的备注）|`ERANGE`|  
  
 如果发生其中任一条件，如中所述调用无效参数异常 [参数验证](../../c-runtime-library/parameter-validation.md) 。 如果允许执行继续，函数将返回错误代码并按表中所示设置 `errno`。  
  
## 备注  
 `wcstombs_s` 函数将`wcstr` 指向的宽字节字符字符串转换为存储在 `mbstr` 指向的缓冲区中的多字节字符。 在满足以下条件之一前，该转换将一直对每个字符执行：  
  
-   遇到 null 宽字符  
  
-   遇到无法转换的宽字符  
  
-   存储在 `mbstr` 缓冲中的字节数等于 `count`。  
  
 目标字符串始终以 null 结尾（即使在出错时）。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md), ，然后 `wcstombs_s` 尽可能将字符串作为将根据目标缓冲区转换，同时仍保持 null 终止符的空间。  
  
 如果 `wcstombs_s` 成功转换了源字符串，它会将转换的字符串（包括 null 结束符）的大小（以字节为单位）放入 `*``pReturnValue`（假定 `pReturnValue` 不是 `NULL`）。 即使 `mbstr` 参数为 `NULL` 并提供了确定所需的缓冲区大小的方法，也会发生这种情况。 请注意，如果 `mbstr` 为 `NULL`，则 `count` 会被忽略。  
  
 如果 `wcstombs_s` 遇到无法转换为多字节字符的宽字符，它将执行以下操作：将 0 放入 `*``pReturnValue`，将目标缓冲区设置为空字符串，将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果 `wcstr` 和 `mbstr` 指向的序列重叠，则 `wcstombs_s` 的行为没有定义。  
  
> [!IMPORTANT]
>  请确保 `wcstr` 和 `mbstr` 未重叠，并且 `count` 正确地反映了要转换的宽字节的数量。  
  
 `wcstombs_s` 对所有区域设置相关行为使用当前区域设置；`_wcstombs_s_l` 与 `wcstombs` 相同，只不过前者使用的是传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小自变量\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcstombs_s`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 本程序演示 `wcstombs_s` 函数的行为。  
  
```  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
将宽字符字符串转换︰ 字符都转换字符︰ 14 的多字节字符︰ Hello，world。  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)