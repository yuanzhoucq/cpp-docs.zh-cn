---
title: "_mbsnbcat_s、_mbsnbcat_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
dev_langs: C++
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7288c00de4f09175d7fffd816267201011892953
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s、_mbsnbcat_s_l
至多将另一个多字节字符串的第一个 `n` 字节追加到一个多字节字符串。 这些版本的 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _mbsnbcat_s(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count   
);  
errno_t _mbsnbcat_s_l(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbcat_s(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbcat_s_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `dest`  
 以 null 终止的多字节字符目标字符串。  
  
 `sizeInBytes`  
 `dest` 缓冲区的大小（以字节为单位）。  
  
 `src`  
 以 null 终止的多字节字符源字符串。  
  
 `Count`  
 `src` 中要追加到 `dest` 的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；否则为错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`Dest`|`sizeInBytes`|`src`|返回值|  
|------------|-------------------|-----------|------------------|  
|`NULL`|任何|任何|`EINVAL`|  
|任意|<= 0|任何|`EINVAL`|  
|任意|任何|`NULL`|`EINVAL`|  
  
 如果出现任何一个错误状态，该函数生成无效参数错误，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果处理了错误，则该函数返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_mbsnbcat_s` 函数最多可以将 `dest` 的第一个 `count` 字节追加到 `src`。 如果 `dest` 中紧跟在 null 字符之前的字节是前导字节，则 `src` 的初始字节将覆盖此前导字节。 否则，`src` 的初始字节会覆盖 `dest` 的终止 null 字符。 如果在 `src` 字节追加之前，null 字节出现在 `count` 中，`_mbsnbcat_s` 将追加来自 `src` 的所有字节，直到 null 字符。 如果 `count` 大于 `src` 的长度，则会使用 `src` 的长度代替 `count`。 生成的字符串由 null 字符终止。 如果复制出现在重叠的字符串之间，则该行为不确定。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些函数的版本都相同，只是不带 `_l` 后缀的函数使用当前区域设置，而带有 `_l` 后缀的函数则使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小自变量，并且它们可以自动使用更新、更安全的函数替换较旧、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat_s`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_mbsnbcat_s`|\<mbstring.h>|  
|`_mbsnbcat_s_l`|\<mbstring.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcmp、_mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [_mbsnbcpy、_mbsnbcpy_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [_mbsnbcpy_s、_mbsnbcpy_s_l](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)   
 [_mbsnbset、_mbsnbset_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)