---
title: "_mbccpy_s、_mbccpy_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
dev_langs: C++
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 942267c2632e6ffafec3d2fa9308bfb3db69aa87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s、_mbccpy_s_l
将一个多字节字符从一个字符串复制到另一个字符串。 这些版本的 [_mbccpy、_mbccpy_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 [out] `dest`  
 复制目标。  
  
 [in] `buffSizeInBytes`  
 目标缓冲区的大小。  
  
 [out] `pCopied`  
 填充复制的字节数（如果成功则为 1 或 2）。 如果不在乎数量，则传递 `NULL`。  
  
 [in] `src`  
 要复制的多字节字符。  
  
 [in] `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果失败，则为错误代码。 如果 `src` 或 `dest` 是 `NULL`，或如果要将超过 `buffSizeinBytes` 个字节复制到 `dest`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则这些函数返回 `EINVAL`，并且 `errno` 设置为 `EINVAL`.  
  
## <a name="remarks"></a>备注  
 `_mbccpy_s` 函数将一个多字节字符从 `src` 复制到 `dest`。 如果 `src` 未按照对 [_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 的隐式调用确定的方式指向多字节字符的前导字节，则会复制 `src` 指向的单字节。 如果 `src` 指向前导字节但是后续字节为 0 并因此而无效，则将 0 复制到 `dest`，将 `errno` 设置为 `EILSEQ`，函数返回 `EILSEQ`。  
  
 `_mbccpy_s` 未追加 Null 终止符；但是，如果 `src` 指向空字符，则会将该 null 复制到 `dest`（只是常规的单字节复制）。  
  
 `pCopied` 中的值使用复制的字节数填充。 如果操作成功，则可能的值为 1 和 2。 如果传入了 `NULL`，则会忽略此参数。  
  
|`src`|复制到 `dest`|`pCopied`|返回值|  
|-----------|----------------------|---------------|------------------|  
|非前导字节|非前导字节|1|0|  
|0|0|1|0|  
|前导字节，后跟非零值|前导字节，后跟非零值|2|0|  
|前导字节，后跟 0|0|1|`EILSEQ`|  
  
 请注意，第二行只是第一行的特殊情况。 另请注意，此表假设 `buffSizeInBytes` >= `pCopied`。  
  
 `_mbccpy_s` 对依赖于区域设置的任何行为使用当前区域设置。 `_mbccpy_s_l` 等同于 `_mbccpy_s`，只不过 `_mbccpy_s_l` 使用为所有与区域设置相关的行为传入的区域设置。  
  
 在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy_s`|映射到宏或内联函数。|`_mbccpy_s`|映射到宏或内联函数。|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_mbccpy_s`|\<mbstring.h>|  
|`_mbccpy_s_l`|\<mbstring.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)