---
title: "_ltoa、_ltow | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ltoa
- _ltow
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
apitype: DLLExport
f1_keywords:
- ltow
- _ltot
- _ltoa
- _ltow
dev_langs:
- C++
helpviewer_keywords:
- converting integers
- _ltoa function
- _ltow function
- ltow function
- ltoa function
- long integer conversion to string
- converting numbers, to strings
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 5e67ca683ac8946f88389e9ca2323f1255da6695
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="ltoa-ltow"></a>_ltoa、_ltow
将长整数转换为字符串。 提供这些函数的更多安全版本；请参阅 [_ltoa_s、_ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `value`  
 要转换的数字。  
  
 `str`  
 字符串结果。  
  
 `radix`  
 `value` 的基数。  
  
## <a name="return-value"></a>返回值  
 这些函数均返回指向 `str` 的指针。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `_ltoa` 函数将 `value` 的数字转换为以 null 结尾的字符串，并将结果（最多 33 个字节）存储在 `str` 中。 `radix`参数指定的基数`value`，其范围必须介于 2-36 之间。 如果`radix`等于 10 和`value`为负，则存储字符串的第一个字符为减号 （-）。 `_ltow` 是 `_ltoa` 的宽字符版本；`_ltow` 的第二个参数和返回值是宽字符字符串。 所有这些函数都是 Microsoft 特定的。  
  
> [!IMPORTANT]
>  若要防止缓冲区溢出，请确保 `str` 缓冲区的大小足以承载转换的位数及尾随的空字符和符号字符。  
  
 在 C++ 中，这些函数具有模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_ltoa`|\<stdlib.h>|  
|`_ltow`|\<stdlib.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa、_ultow](../../c-runtime-library/reference/ultoa-ultow.md)
