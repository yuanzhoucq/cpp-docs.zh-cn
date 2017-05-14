---
title: "_cabs | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
dev_langs:
- C++
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 13
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
ms.openlocfilehash: 930ef18229737fee03d03308c45f5ffb3615cdcd
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="cabs"></a>_cabs
计算复数的绝对值。  
  
## <a name="syntax"></a>语法  
  
```  
double _cabs(   
   struct _complex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 复数。  
  
## <a name="return-value"></a>返回值  
 如果成功，`_cabs` 将返回其参数的绝对值。 在溢出时，`_cabs` 将返回 `HUGE_VAL` 并将 `errno` 设置为 `ERANGE`。 可以使用 [_matherr](../../c-runtime-library/reference/matherr.md) 更改错误处理。  
  
## <a name="remarks"></a>备注  
 `_cabs` 函数计算复数的绝对值，该值必须是 [_complex](../../c-runtime-library/standard-types.md) 类型的结构。 结构 `z` 由实部 `x` 和虚部 `y` 构成。 调用`_cabs`生成等效的表达式值`sqrt( z.x * z.x + z.y * z.y )`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_cabs`|\<math.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_cabs.c  
/* Using _cabs, this program calculates  
 * the absolute value of a complex number.  
 */  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct _complex number = { 3.0, 4.0 };  
   double d;  
  
   d = _cabs( number );  
   printf( "The absolute value of %f + %fi is %f\n",  
           number.x, number.y, d );  
}  
```  
  
```Output  
The absolute value of 3.000000 + 4.000000i is 5.000000  
```  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [abs、labs、llabs、_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
