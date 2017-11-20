---
title: "ldiv、lldiv | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ldiv
- lldiv
dev_langs: C++
helpviewer_keywords:
- ldiv function
- lldiv function
- quotients, computing
- computing remainders
- remainder computing
- computing quotients
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c1da38d40c45ecd6dc36eed594304894a25dcc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ldiv-lldiv"></a>ldiv、lldiv
通过一个操作计算两个整数的商和余数。  
  
## <a name="syntax"></a>语法  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### <a name="parameters"></a>参数  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>返回值  
 `ldiv` 返回一个包括商和余数的 [ldiv_t](../../c-runtime-library/standard-types.md) 类型的结构。 `lldiv` 返回一个包括商和余数的 [lldiv_t](../../c-runtime-library/standard-types.md) 类型的结构。  
  
## <a name="remarks"></a>备注  
 `ldiv` 和 `lldiv` 函数将 `numer` 除以 `denom`，从而计算商和余数。 商的符号与数学商的符号相同。 商的绝对值是小于数学商的绝对值的最大整数。 如果分母为 0，程序将终止并显示错误消息。 `ldiv` 和 `lldiv` 与 `div` 相同，只是 `ldiv` 的参数和返回的结构的成员都是 `long` 类型，而 `lldiv` 的参数和返回的结构的成员是 `long long` 类型。  
  
 `ldiv_t` 和 `lldiv_t` 结构在 \<stdlib.h> 中定义。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`ldiv`, `lldiv`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)