---
title: "_ecvt_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs:
- C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 25
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 81bcb9fe1306f5affa49672269890d6f5888a3ac
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="ecvts"></a>_ecvt_s
将 `double` 编号转换为字符串。 这是 [_ecvt](../../c-runtime-library/reference/ecvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `_Buffer`  
 使用转换的结果填充指向位字符串的指针。  
  
 [in] `_SizeInBytes`  
 缓冲区的大小（以字节为单位）。  
  
 [in] `_Value`  
 要转换的数字。  
  
 [in] `_Count`  
 存储的数字位数。  
  
 [out] `_Dec`  
 存储的十进制点位置。  
  
 [out] `_Sign`  
 转换后的数字的符号。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 ERRNO.h 中定义的。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
### <a name="error-conditions"></a>错误条件  
  
|`_Buffer`|`_SizeInBytes`|_Value|_Count|_Dec|_Sign|返回值|`buffer` 中的值|  
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|  
|`NULL`|任何|任何|任何|任何|任何|`EINVAL`|未修改。|  
|非 `NULL`（指向有效内存）|<=0|any|任何|任何|任何|`EINVAL`|未修改。|  
|any|任何|任何|任何|`NULL`|任何|`EINVAL`|未修改。|  
|any|任何|任何|任何|任何|`NULL`|`EINVAL`|未修改。|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效内存且不为 `NULL`，则 `_ecvt_s` 可能生成访问冲突。  
  
## <a name="remarks"></a>备注  
 `_ecvt_s` 函数将浮点数转换为字符串。 `_Value` 参数是要转换的浮点数。 此函数最多存储 `count` 位 `_Value` 作为字符串，并追加空字符 ('\0')。 如果 `_Value` 中的数字位数超过 `_Count`，则低位数字被舍入。 如果数字位数少于 `count`，则字符串使用零来填充。  
  
 字符串中仅存储位数。 小数点位置和 `_Value` 的符号可以在调用后从 `_Dec` 和 `_Sign` 中获取。 `_Dec` 参数指向整数值；此整数值给定相对于字符串开头的小数点的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 `_Sign` 参数指向一个整数，表示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。  
  
 `_CVTBUFSIZE` 的缓冲区长度足以满足任何浮点值。  
  
 `_ecvt_s` 和 `_fcvt_s` 之间的差异在于对 `_Count` 参数的解释。 `_ecvt_s` 将 `_Count` 解释为输出字符串中的数字总位数，而 `_fcvt_s` 将 `_Count` 解释为小数点后面的数字位数。  
  
 在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|可选标头|  
|--------------|---------------------|---------------------|  
|`_ecvt_s`|\<stdlib.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 12000  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)
