---
title: "_mbccpy_s、_mbccpy_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbccpy_s"
  - "_mbccpy_s_l"
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
  - "_mbccpy_s_l"
  - "mbccpy_s_l"
  - "mbccpy_s"
  - "_mbccpy_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbccpy_s 函数"
  - "_mbccpy_s_l 函数"
  - "_tccpy_s 函数"
  - "_tccpy_s_l 函数"
  - "mbccpy_s 函数"
  - "mbccpy_s_l 函数"
  - "tccpy_s 函数"
  - "tccpy_s_l 函数"
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbccpy_s、_mbccpy_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从一个字符串到另一个字符串复制多个字符。  [\_mbccpy、\_mbccpy\_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _mbccpy_s(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src   
);  
errno_t _mbccpy_s_l(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
);  
template <size_t size>  
errno_t _mbccpy_s(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src   
); // C++ only  
template <size_t size>  
errno_t _mbccpy_s_l(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
); // C++ only  
```  
  
#### 参数  
 \[out\] `dest`  
 复制目标。  
  
 \[in\] `buffSizeInBytes`  
 目标缓冲区的大小。  
  
 \[out\] `pCopied`  
 用复制的字节数填充 \(1 或 2，如果成功\)。  如果您对该数字不关心，请传递`NULL`。  
  
 \[in\] `src`  
 要复制的多字节字符。  
  
 \[in\] `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  如果 `src` 或 `dest` 是 `NULL`，或者，如果超过`buffSizeinBytes`字节都复制到 `dest`，则调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数将返回 `errno` 并将 `EINVAL`设置为`EINVAL`。  
  
## 备注  
 `_mbccpy_s` 函数从`src`复制多字符到 `dest` 如果 `src` 不指向多字节字符的前导字节,就如同隐式调用 [\_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md)，则复制指向`src` 的单字节。  如果 `src` 指向前导字节，但以下一个字节是 0 而无效，则将 0 复制到 `dest`，`errno` 设置为 `EILSEQ`，且函数返回 `EILSEQ`。  
  
 `_mbccpy_s` 不追加 null 结束符；但是，如果 `src` 指向空字符，则空字符被复制到 `dest` \(为普通单字节复制\)。  
  
 `pCopied` 的值用复制的字节数填充。  ;如果操作成功，可能的值为 1 和 2。  如果传递 `NULL`，此参数将被忽略。  
  
|`src`|复制到 `dest`|`pCopied`|返回值|  
|-----------|----------------|---------------|---------|  
|非前导字节|非前导字节|1|0|  
|0|0|1|0|  
|紧随非 0 的前导字节|紧随非 0 的前导字节|2|0|  
|紧随 0 的前导字节|0|1|`EILSEQ`|  
  
 注意第二行是第一行的一个特例。  另外请注意，表格假定`buffSizeInBytes` \> \= `pCopied`。  
  
 `_mbccpy_s` 对与区域设置相关的所有行为使用当前区域设置。  `_mbccpy_s_l` 与 `_mbccpy_s`相同，但`_mbccpy_s_l`使用区域设置传递任何的区域相关行为。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tccpy_s`|映射到宏或内联函数。|`_mbccpy_s`|映射到宏或内联函数。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbccpy_s`|\<mbstring.h\>|  
|`_mbccpy_s_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)