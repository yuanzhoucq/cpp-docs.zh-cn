---
title: "_mbsnbcpy、_mbsnbcpy_l | Microsoft Docs"
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
  - "_mbsnbcpy"
  - "_mbsnbcpy_l"
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
  - "mbsnbcpy"
  - "_ftcsncpy"
  - "_mbsnbcpy"
  - "mbsnbcpy_l"
  - "_mbsnbcpy_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcpy 函数"
  - "_mbsnbcpy_l 函数"
  - "_tcsncpy 函数"
  - "_tcsncpy_l 函数"
  - "mbsnbcpy 函数"
  - "mbsnbcpy_l 函数"
  - "tcsncpy 函数"
  - "tcsncpy_l 函数"
ms.assetid: 83d17b50-3cbf-4df9-bce8-3b6d52f85d04
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcpy、_mbsnbcpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串的 `n` 个字节复制到目标字符串。  有关这些函数的更多安全版本，请参阅 [\_mbsnbcpy\_s、\_mbsnbcpy\_s\_l](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关更多信息，请参见 [CRT 函数不支持使用 \/ZW](http://msdn.microsoft.com/en-us/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
unsigned char * _mbsnbcpy(  
   unsigned char * strDest,  
   const unsigned char * strSource,  
   size_t count  
);  
unsigned char * _mbsnbcpy_l(  
   unsigned char * strDest,  
   const unsigned char * strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
unsigned char * _mbsnbcpy(  
   unsigned char (&strDest)[size],  
   const unsigned char * strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
unsigned char * _mbsnbcpy_l(  
   unsigned char (&strDest)[size],  
   const unsigned char * strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `strDest`  
 要复制的字符串的目标。  
  
 `strSource`  
 要复制的字符串。  
  
 `count`  
 要复制的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsnbcpy` 返回一个指向目标字符串的指针。  没有保留任何返回值以指示错误。  
  
## 备注  
 `_mbsnbcpy` 函数将 `count` 个字节从 `strSource` 复制到 `strDest`。  如果 `count` 超过 `strDest` 的大小，或者源字符串和目标字符串重叠，则 `_mbsnbcpy` 的行为是不确定的。  
  
 如果 `strSource` 或 `strDest` 为空指针，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则函数将返回 `NULL`，并且将 `errno` 设置为 `EINVAL`。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些函数的版本都相同，只是那些不带 `_l` 后缀的函数使用当前区域设置，而那些带有 `_l` 后缀的函数则使用传入的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。  缓冲区溢出可用于执行任意代码者攻击，这些代码可能会导致不必要地提升特权并危害系统。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 在 C\+\+ 中，这些函数具有可调用这些函数的更新、更安全的版本的模板重载。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncpy`|[strncpy](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|`_mbsnbcpy`|[wcsncpy](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|  
|`_tcsncpy_l`|`_strncpy_l`|`_mbsnbcp_l`|`_wcsncpy_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbcpy`|\<mbstring.h\>|  
|`_mbsnbcpy_l`|\<mbstring.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt、\_wcsncnt、\_mbsnbcnt、\_mbsnbcnt\_l、\_mbsnccnt、\_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)