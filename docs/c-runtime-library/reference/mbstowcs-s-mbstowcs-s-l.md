---
title: "mbstowcs_s, _mbstowcs_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
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
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbstowcs_s_l 函数"
  - "mbstowcs_s 函数"
  - "mbstowcs_s_l 函数"
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbstowcs_s, _mbstowcs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将多字节字符序列转换为对应的宽字符序列。  [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 要转换的字符数。  
  
 \[out\] `wcstr`  
 结果的缓冲区地址转换成宽字符字符串。  
  
 \[in\] `sizeInWords`  
 `wcstr` 缓冲区大小\(以字为单位\)。  
  
 \[in\]`mbstr`  
 多字节字符序列的空终止字符的地址。  
  
 \[in\] `count`  
 `wcstr` 缓冲区中存储的宽字符的最大页数，不包括 null 终止符或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
|错误条件|返回值和`errno`|  
|----------|-----------------|  
|`wcstr` 是 `NULL` 和 `sizeInWords` \> 0|`EINVAL`|  
|`mbstr` 为 `NULL`|`EINVAL`|  
|目标缓冲区因过小而无法包含转换的字符串。\(除非 `count` 是 `_TRUNCATE`；请参见下面"备注"\)|`ERANGE`|  
|`wcstr` 不是 `NULL` 和 `sizeInWords` \=\= 0|`EINVAL`|  
  
 如果任一错误状态发生，调用无效参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，函数返回错误代码然后按照下表设置 `errno`。  
  
## 备注  
 `mbstowcs_s` 函数将由`mbstr` 指向的缓冲区存储的多字节字符转换为 `wcstr`指向的缓冲区的宽字节字符。  字符的转换将继续进行，直到与这些情况之一匹配：  
  
-   遇到多字节字符null  
  
-   遇到无效的多字节字符  
  
-   在 `wcstr` 缓冲存储的宽字符数等于 `count`。  
  
 目标字符串始终为 null 终止 \(即使发生错误\)。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，则当仍有 null 结束符的空间时，`mbstowcs_s` 将许多字符串整合到目标缓冲区。  
  
 如果 `mbstowcs_s` 成功转换了源字符串，它将转换字符串的宽字符的大小（包括空终止符）放入`*``pReturnValue`。\(提供的 `pReturnValue` 不是 `NULL`\)。  即使 `wcstr` 参数为 `NULL`, 并提供方法来确定需要的缓冲区大小，也会发生这个事件。  请注意，如果 `wcstr` 为 `NULL`，将忽略 `count`，并且`sizeInWords` 必须为 0。  
  
 如果 `mbstowcs_s` 遇到无效的多字节字符，将0置于`*``pReturnValue`，将目标缓冲区设为空字符串，`errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果由 `mbstr` 与 `wcstr` 指向的序列重叠，`mbstowcs_s` 行为是未定义的。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 无重叠，并且`count` 恰好指出要转换的多字节字符的数量。  
  
 `mbstowcs_s`使用区域设置相关行为的当前区域设置；和`_mbstowcs_s_l` 相同，但它将使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`mbstowcs_s`|\<stdlib.h\>|  
|`_mbstowcs_s_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)