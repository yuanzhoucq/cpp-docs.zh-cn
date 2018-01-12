---
title: "_ultoa、_ultow | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultoa
- _ultow
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ultot
- ultow
- _ultoa
- _ultow
- _ultot
dev_langs: C++
helpviewer_keywords:
- ultot function
- converting integers
- _ultot function
- ultow function
- integers, converting
- _ultow function
- _ultoa function
- converting numbers, to strings
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e555275f4516d92318ec5cfffbca3472c2a5cf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ultoa-ultow"></a>_ultoa、_ultow
将无符号长整数转换为字符串。 提供这些函数的更多安全版本；请参阅 [_ultoa_s、_ultow_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
   unsigned long value,  
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
 `_ultoa` 函数将 `value` 转换为以 null 结尾的字符串，并将结果（最多 33 个字节）存储在 `str` 中。 不执行溢出检查。 `radix`指定的基数`value`;`radix`必须介于 2-36 之间。 `_ultow` 是 `_ultoa` 的宽字符版本。  
  
> [!IMPORTANT]
>  若要防止缓冲区溢出，请确保 `str` 缓冲区的大小足以承载转换的位数及尾随的 Null 字符。  
  
 在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_ultoa`|\<stdlib.h>|  
|`_ultow`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)