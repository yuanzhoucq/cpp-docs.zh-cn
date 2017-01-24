---
title: "mbsrtowcs_s | Microsoft Docs"
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
  - "mbsrtowcs_s"
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
  - "mbsrtowcs_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mbsrtowcs_s 函数"
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbsrtowcs_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将当前区域设置中的多字节字符字符串转换为宽字符字符串表示形式。  具有安全增强功能的 [mbsrtowcs](../../c-runtime-library/reference/mbsrtowcs.md) 版本（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t * wcstr,  
   size_t sizeInWords,  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
);  
template <size_t size>  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
); // C++ only  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 要转换的字符数。  
  
 \[out\] `wcstr`  
 用于存储转换所生成的宽字符字符串的缓冲区地址。  
  
 \[out\] `sizeInWords`  
 `wcstr` 的大小（宽字符）（以单词为单位）。  
  
 \[in, out\] `mbstr`  
 指向要转换的多字节字符字符串位置的间接指针。  
  
 \[in\] `count`  
 要存储在 `wcstr` 缓冲区中的宽字符的最大数量，不包括终止 null 或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in, out\] `mbstate`  
 指向 `mbstate_t` 转换状态对象的指针。  如果此值为 null 指针，则使用静态内部转换状态对象。  由于内部 `mbstate_t` 对象不是线程安全的，建议始终传递你自己的 `mbstate` 参数。  
  
## 返回值  
 如果转换成功则返回零；如果失败则返回错误代码。  
  
|错误条件|返回值和 `errno`|  
|----------|------------------|  
|`wcstr` 为 null 指针且 `sizeInWords` \> 0|`EINVAL`|  
|`mbstr` 为 null 指针|`EINVAL`|  
|`mbstr` 间接指向的字符串包含一个对当前区域设置无效的多字节序列。|`EILSEQ`|  
|目标缓冲区过小，无法包含转换后的字符串（除非 `count` 是 `_TRUNCATE`；有关详细信息，请参阅备注）|`ERANGE`|  
  
 如果发生这些情况中的任何一个，都会调用无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，函数将返回错误代码并按表中所示设置 `errno`。  
  
## 备注  
 `mbsrtowcs_s` 函数通过使用 `mbstr` 中包含的转换状态，将 `wcstr` 间接指向的多字节字符的字符串转换为存储在 `mbstate` 指向的缓冲区中的宽字符。  在满足以下条件之一前，该转换将一直对每个字符执行：  
  
-   遇到一个多字节空字符  
  
-   遇到一个无效的多字节字符  
  
-   存储在 `wcstr` 缓冲区中的宽字符数等于 `count`。  
  
 目标字符串 `wcstr` 始终以 null 值结束，即使在发生错误的情况下也是如此，除非 `wcstr` 为 null 指针。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，则 `mbsrtowcs_s` 会根据目标缓冲区的容量尽量多地转换字符串，同时仍然为 null 结束符留下空间。  
  
 如果 `mbsrtowcs_s` 成功转换了源字符串，则它会将大小放入转换的字符串的宽字符并将 null 结束符放入 `*``pReturnValue`（前提是 `pReturnValue` 不是 null 指针）。  即使 `wcstr` 参数为 null 指针并且由你确定所需的缓冲区大小，也会发生这种情况。  请注意，如果 `wcstr` 为 null 指针，则忽略 `count`。  
  
 如果 `wcstr` 不是 null 指针，则在转换因到达终止 null 字符而停止时，`mbstr` 指向的指针对象将分配到一个 null 指针。  否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。  这将允许调用后续函数以在此调用停止的位置重新调用转换。  
  
 如果 `mbstate` 为 null 指针，则将使用库内部 `mbstate_t` 转换状态静态对象。  由于此内部静态对象不是线程安全的，建议传递你自己的 `mbstate` 值。  
  
 如果 `mbsrtowcs_s` 遇到在当前区域设置中无效的多字节字符，它将把 \-1 放到 `*``pReturnValue` 中，将目标缓冲区 `wcstr` 设置为空字符串，将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果 `mbstr` 和 `wcstr` 指向的序列重叠，则 `mbsrtowcs_s` 的行为没有定义。  `mbsrtowcs_s` 会受到当前区域设置中 LC\_TYPE 类别 的影响。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 未重叠，并且 `count` 正确反映了要转换的多字节字符的数量。  
  
 `mbsrtowcs_s` 函数的可重启性不同于 [mbstowcs\_s, \_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)。  转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。  混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用 `mbsrlen`（而非 `mbslen` ）的后续调用，则应用程序应使用 `mbsrtowcs_s`，而不是 `mbstowcs_s.`。  
  
 在 C\+\+ 中，模板重载简化了这些函数的使用；重载可以自动推导出缓冲区长度\(不再需要指定大小参数\)，并且它们可以通过使用更新、更安全的对应函数来自动替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 异常  
 只要 `mbsrtowcs_s` 函数正在执行且 `mbstate` 参数不是 null 指针，当前线程中的函数都不调用 `setlocale` 时，此函数就是多线程安全的。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`mbsrtowcs_s`|\<wchar.h\>|  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs\_s, \_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)