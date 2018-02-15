---
title: "_strdate_s、_wstrdate_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strdate_s
- _wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs:
- C++
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e71476fbb1810505f0b50a04d20f6235ff727c92
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="strdates-wstrdates"></a>_strdate_s、_wstrdate_s
将当前系统日期复制到缓冲区。 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [_strdate、_wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md) 具有安全性增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 指向缓冲区的指针将使用格式化的日期字符串填充。  
  
 [in] `numberOfElements`  
 缓冲区的大小。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno](../../c-runtime-library/errno-constants.md)。  
  
## <a name="error-conditions"></a>错误条件  
  
|`buffer`|`numberOfElements`|返回|`buffer` 的内容|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|（任意数值）|`EINVAL`|未修改|  
|非 `NULL`（指向有效的缓冲区）|0|`EINVAL`|未修改|  
|非 `NULL`（指向有效的缓冲区）|0 < `numberOfElements` < 9|`EINVAL`|空字符串|  
|非 `NULL`（指向有效的缓冲区）|`numberOfElements` >= 9|0|注解中指定的当前日期格式|  
  
## <a name="security-issues"></a>安全问题  
 如果 `numberOfElements` 参数大于 9，则为缓冲区传入无效非 `NULL` 值将导致访问冲突。  
  
 传递大于 `buffer` 实际大小的值将导致缓冲区溢出。  
  
## <a name="remarks"></a>备注  
 这些函数提供 `_strdate` 和 `_wstrdate` 的更安全的版本。 `_strdate_s` 函数将当前系统日期复制到 `buffer` 所指向的缓冲区，格式为 `mm`/`dd`/`yy`，其中 `mm` 表示两位数字的月份，`dd` 表示两位数字的日期，`yy` 表示年份的最后两位数字。 例如，字符串 `12/05/99` 表示 1999 年 12 月 5 日。 缓冲区长度必须至少为 9 个字符。  
  
 `_wstrdate_s` 是 `_strdate_s` 的宽字符版本；`_wstrdate_s` 的参数和返回值都是宽字符字符串。 否则这些函数具有相同行为。  
  
 如果 `buffer` 是 `NULL` 指针，或如果 `numberOfElements` 小于 9 个字符，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 -1，且如果缓冲区为 `NULL` 或 `numberOfElements` 小于或等于 0，则将 `errno` 设置为 `EINVAL`，或者如果 `numberOfElements` 小于 9，则将 `errno` 设置为 `ERANGE`。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mapping"></a>一般文本例程映射：  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_strdate`|\<time.h>|  
|`_wstrdate`|\<time.h> 或 \<wchar.h>|  
|`_strdate_s`|\<time.h>|  
  
## <a name="example"></a>示例  
 请参阅 [time](../../c-runtime-library/reference/time-time32-time64.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)