---
title: "_gcvt_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
dev_langs:
- C++
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 567738b488ae648dbd67ea1d2b5cdf34b649170c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="gcvts"></a>_gcvt_s
将浮点值转换为字符串。 这是 [_gcvt](../../c-runtime-library/reference/gcvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 存储转换结果的缓冲区。  
  
 [in] `sizeInBytes`  
 缓冲区的大小。  
  
 [in] `value`  
 要转换的值。  
  
 [in] `digits`  
 存储的有效位数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果由于无效参数导致失败（请参阅下表中的无效值），则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回错误代码。 错误代码是在 Errno.h 中定义的。 有关这些错误的列表，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>错误条件  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|返回|`buffer` 中的值|  
|--------------|-------------------|-------------|--------------|------------|-----------------------|  
|`NULL`|任何|任何|任何|`EINVAL`|未修改。|  
|非 `NULL`（指向有效内存）|零|任何|任何|`EINVAL`|未修改。|  
|非 `NULL`（指向有效内存）|任何|任何|>= `sizeInBytes`|`EINVAL`|未修改。|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效内存且不为 `NULL`，则 `_gcvt_s` 可以生成访问冲突。  
  
## <a name="remarks"></a>备注  
 `_gcvt_s` 函数将浮点 `value` 转换为字符串（它包括小数点和可能的登录字节），并将字符串存储在 `buffer` 中。 `buffer` 应足够大以容纳转换后的值加上一个会自动追加的端接空字符。 `_CVTBUFSIZE` 的缓冲区长度足以满足任何浮点值。 如果已使用 `digits` + 1 的缓冲区大小，该函数将不会覆盖缓冲区的末尾，因此请确保为此操作提供足够的缓冲区。 `_gcvt_s` 尝试生成十进制格式的 `digits` 数字。 如果不能，则将生成指数格式的 `digits` 数字。 在转换过程中，可以取消零结尾。  
  
 在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_gcvt_s`|\<stdlib.h>|\<error.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 1.2  
```  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)   
 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)