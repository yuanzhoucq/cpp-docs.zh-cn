---
title: "_mbccpy、_mbccpy_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy
- _mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs: C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 11f5a9a0629aa7012418cdb74d849d838e8cc5b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy、_mbccpy_l
将多字节字符从一个字符串复制到另一个字符串。 提供这些函数的更多安全版本；请参阅 [_mbccpy_s、_mbccpy_s_l](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `dest`  
 复制目标。  
  
 `src`  
 要复制的多字节字符。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="remarks"></a>备注  
 `_mbccpy` 函数将一个多字节字符从 `src` 复制到 `dest`。  
  
 此函数验证其参数。 如果 `_mbccpy` 为 `dest` 或 `src` 传递了空指针，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则 `errno` 将设置为 `EINVAL`。  
  
 `_mbccpy` 对依赖于区域设置的任何行为使用当前区域设置。 `_mbccpy_l` 等同于 `_mbccpy`，只不过 `_mbccpy_l` 使用为所有与区域设置相关的行为传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 **安全说明** 使用以 null 结尾的字符串。 以 null 结尾的字符串不得超过目标缓冲区的大小。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy`|映射到宏或内联函数|`_mbccpy`|映射到宏或内联函数|  
|`_tccpy_l`|无|`_mbccpy_l`|无|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbccpy`|\<mbctype.h>|  
|`_mbccpy_l`|\<mbctype.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)