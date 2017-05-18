---
title: "_fcvt_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
dev_langs:
- C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: 27
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 9c282757ae79367cdc2ee72b3f3ce8d0e50983fa
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="fcvts"></a>_fcvt_s
将浮点数转换为字符串。 这是 [_fcvt](../../c-runtime-library/reference/fcvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 所提供的缓冲区将保留转换的结果。  
  
 [in] `sizeInBytes`  
 缓冲区的大小（以字节为单位）。  
  
 [in] `value`  
 要转换的数字。  
  
 [in] `count`  
 小数点后面的数字位数。  
  
 [out] `dec`  
 指向存储的小数点位置的指针。  
  
 [out] `sign`  
 指向存储的符号指示符的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 ERRNO.h 中定义的。 有关这些错误的列表，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
### <a name="error-conditions"></a>错误条件  
  
|`buffer`|`sizeInBytes`|值|count|dec|Sign|返回|`buffer` 中的值|  
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|  
|`NULL`|任何|任何|任何|任何|任何|`EINVAL`|未修改。|  
|非 `NULL`（指向有效内存）|<=0|any|任何|任何|任何|`EINVAL`|未修改。|  
|any|任何|任何|任何|`NULL`|任何|`EINVAL`|未修改。|  
|any|任何|任何|任何|任何|`NULL`|`EINVAL`|未修改。|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效内存且不为 `NULL`，则 `_fcvt_s` 可能生成访问冲突。  
  
## <a name="remarks"></a>备注  
 `_fcvt_s` 函数将浮点数转换为以 null 结尾的字符串。 `value` 参数是要转换的浮点数。 `_fcvt_s` 将 `value` 的位数存储为字符串，并追加一个空字符 ('\0')。 `count` 参数指定此小数点后要存储的数字位数。 多余的位数被舍入到 `count` 位置。 如果小于精确到 `count` 的位数，则字符串使用零填充。  
  
 字符串中仅存储位数。 小数点位置和 `value` 的符号可以在调用后从 `dec` 和 `sign` 中获取。 `dec` 参数指向整数值；此整数值指定相对于字符串开头的小数点的位置。 零或负整数值表示小数点位于第一个数字的左侧。 参数 `sign` 指向一个整数值，表示 `value` 的符号。 如果 `value` 为正数，则整数设置为 0，如果 `value` 为负数，则整数设置为非零数。  
  
 `_CVTBUFSIZE` 的缓冲区长度足以满足任何浮点值。  
  
 `_ecvt_s` 和 `_fcvt_s` 之间的差异在于对 `count` 参数的解释。 `_ecvt_s`解释`count`作为的输出字符串中的位数总数和`_fcvt_s`解释`count`作为小数点后的数字个数。  
  
 在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|可选标头|  
|--------------|---------------------|---------------------|  
|`_fcvt_s`|\<stdlib.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：** [CRT 库功能](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 120000  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)
