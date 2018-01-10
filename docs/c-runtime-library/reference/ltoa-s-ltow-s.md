---
title: "_ltoa_s、_ltow_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ltoa_s
- _ltow_s
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
- _ltow_s
- _ltoa_s
- ltoa_s
- ltow_s
dev_langs: C++
helpviewer_keywords:
- converting integers
- _ltoa_s function
- ltow_s function
- long integer conversion to string
- converting numbers, to strings
- ltoa_s function
- _ltow_s function
ms.assetid: d7dc61ea-1ccd-412d-b262-555a58647386
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de078e5ad6d2488b852e14247d2d72ca751a9635
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltoas-ltows"></a>_ltoa_s、_ltow_s
将长整数转换为字符串。 这些版本的 [_ltoa、_ltow](../../c-runtime-library/reference/ltoa-ltow.md) 具有安全性增强功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _ltoa_s(  
    long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ltow_s(  
    long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ltoa_s(  
    long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ltow_s(  
    long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `value`  
 要转换的数字。  
  
 `str`  
 生成的字符串的缓冲区。  
  
 `sizeOfstr`  
 `_ltoa_s` 的 `str` 大小（以字节为单位）或 `_ltow_s` 的字数。  
  
 `radix`  
 `value` 的基数。  
  
## <a name="return-value"></a>返回值  
 如果此函数成功，则为零，否则出现错误代码。  
  
## <a name="remarks"></a>备注  
 `_ltoa_s` 函数将 `value` 的数字转换为以 null 结尾的字符串，并将结果（最多 33 个字节）存储在 `str` 中。 `radix`参数指定的基数`value`，其范围必须介于 2-36 之间。 如果`radix`等于 10 和`value`为负，则存储字符串的第一个字符为减号 （-）。 `_ltow_s` 是 `_ltoa_s` 的宽字符版本；`_ltow_s` 的第二个参数是宽字符字符串。  
  
 如果 `str` 是一个 `NULL` 指针，或 `sizeOfstr` 小于或等于 0，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，这些函数将返回 -1 并将 `errno` 设置为 `EINVAL`，或者如果 `value` 或 `str` 超出长整数的范围，则这些函数返回 -1 并将 `errno` 设置为 `ERANGE`。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_ltoa_s`|\<stdlib.h>|  
|`_ltow_s`|\<stdlib.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa、_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ultoa_s、_ultow_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)