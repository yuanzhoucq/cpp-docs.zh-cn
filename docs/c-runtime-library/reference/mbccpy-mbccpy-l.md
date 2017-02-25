---
title: "_mbccpy、_mbccpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbccpy"
  - "_mbccpy_l"
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
  - "_mbccpy"
  - "tccpy"
  - "ftccpy"
  - "mbccpy"
  - "_tccpy"
  - "_ftccpy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbccpy 函数"
  - "_mbccpy_l 函数"
  - "_tccpy 函数"
  - "_tccpy_l 函数"
  - "mbccpy 函数"
  - "mbccpy_l 函数"
  - "tccpy 函数"
  - "tccpy_l 函数"
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _mbccpy、_mbccpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从一个字符串到另一个字符串复制多个字符。  有关这些函数的更多安全版本，请参见 [\_mbccpy\_s、\_mbccpy\_s\_l](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `dest`  
 复制目标。  
  
 `src`  
 要复制的多字节字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 备注  
 `_mbccpy` 函数复制多字符从`src`到 `dest`  
  
 此函数验证其参数。  如果`dest` or `src`给`_mbccpy`传递一个空指针，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，`errno` 设置为 `EINVAL`。  
  
 `_mbccpy` 对与区域设置相关的所有行为使用当前区域设置。  `_mbccpy_l` 与 `_mbccpy`相同，但`_mbccpy_l`使用区域设置传递任何的区域相关行为。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 **Security Note** 使用以 NULL 结尾的字符串。  该 null 终止的字符串不能超过目标缓冲区的大小。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tccpy`|映射到宏或内联函数|`_mbccpy`|映射到宏或内联函数|  
|`_tccpy_l`|无|`_mbccpy_l`|无|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbccpy`|\<mbctype.h\>|  
|`_mbccpy_l`|\<mbctype.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)