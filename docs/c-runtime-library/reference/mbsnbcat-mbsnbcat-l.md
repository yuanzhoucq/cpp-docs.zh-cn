---
title: "_mbsnbcat、_mbsnbcat_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcat_l"
  - "_mbsnbcat"
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
  - "mbsnbcat"
  - "mbsnbcat_l"
  - "_mbsnbcat"
  - "_mbsnbcat_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcat 函数"
  - "_mbsnbcat_l 函数"
  - "_tcsncat 函数"
  - "_tcsncat_l 函数"
  - "mbsnbcat 函数"
  - "mbsnbcat_l 函数"
  - "tcsncat 函数"
  - "tcsncat_l 函数"
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _mbsnbcat、_mbsnbcat_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

至多，追加一个多字节字符字符串的第一个 `n` 字节到另一个字符串。  有关这些函数的更多安全版本，请参见 [\_mbsnbcat\_s、\_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned char *_mbsnbcat(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count   
);  
unsigned char *_mbsnbcat_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
unsigned char *_mbsnbcat(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsnbcat_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `dest`  
 以null 终止的多字节字符的目标字符串。  
  
 `src`  
 以null 终止的多字节字符的源字符串。  
  
 `count`  
 字节数从`src` 追加到 `dest`。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsnbcat`返回指向目标字符串的指针。  没有保留任何返回值以指示错误。  
  
## 备注  
 `_mbsnbcat` 函数至多追加第一个 `count` 字节 `src` 到 `dest`。  如果在 null 字符之前的字节在 `dest` 是前导字节，则`src` 的初始字节复盖此前导字节。  否则，`src`的初始字节复盖 `dest`的终止 null 字符。  如果在 `count` 字节追加之前， null 字节出现在 `src`中，\_`mbsnbcat` 追加来自 `src`的所有字节，直到 null 字符。  如果 `count` 比 `src`的长度更长时，使用`src`的长度代替 `count`。  该字符串以null字符终止。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些函数的 `_mbsnbcat` 版本使用与区域设置相关的行为的当前区域设置；与`_mbsnbcat_l`版本相同， 只不过它们使用传递区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 **Security Note** 使用以 NULL 结尾的字符串。  该 null 终止的字符串不能超过目标缓冲区的大小。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 如果 `dest` 或 `src` 是 `NULL`，函数将生成一个无效参数错误，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果错误被处理，函数将返回 `EINVAL` ，并将`errno`设置为`EINVAL` 。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbcat`|\<mbstring.h\>|  
|`_mbsnbcat_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt、\_wcsncnt、\_mbsnbcnt、\_mbsnbcnt\_l、\_mbsnccnt、\_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [\_mbsnbcat\_s、\_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)