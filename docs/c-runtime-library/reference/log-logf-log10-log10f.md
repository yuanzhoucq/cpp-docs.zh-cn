---
title: "log、logf、log10、log10f | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- log10f
- logf
- log10
- log
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
- logf
- _log10l
- log
- _logl
- log10f
- log10
dev_langs: C++
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8146d4ebe041fa3419aff3614edcd8fe9fa8b8d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="log-logf-log10-log10f"></a>log、logf、log10、log10f
计算对数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      double log(  
   double x   
);  
float log(  
   float x  
);  // C++ only  
long double log(  
   long double x  
);  // C++ only  
float logf(  
   float x   
);  
double log10(  
   double x  
);  
float log10(  
   float x  
);  // C++ only  
long double log10(  
   long double x  
);  // C++ only  
float log10f (  
   float x  
);  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 要查找的值的对数。  
  
## <a name="return-value"></a>返回值  
 如果操作成功，则 **log** 函数返回 *x* 的自然对数（以 e 为底数）。 log10 函数返回以 10 为底数的对数。 如果 *x* 是负数，那么默认情况下，这些函数将返回无穷大。 如果 *x* 为 0，则它们将返回 INF（无限）。  
  
|输入|SEH 异常|Matherr 异常|  
|-----------|-------------------|-----------------------|  
|± QNAN,IND|无|_DOMAIN|  
|± 0|ZERODIVIDE|_SING|  
|x < 0|无效|_DOMAIN|  
  
 **log** 和 `log10` 具有使用流式处理 SIMD 扩展 2 (SSE2) 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## <a name="remarks"></a>备注  
 C++ 允许重载，因此你可以调用 **log** 和 `log10` 的重载。 在 C 程序中，**log** 和 `log10` 始终采用并返回一个双精度值。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|**log**、`logf`、`log10`、`log10f`|\<math.h>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_log.c  
/* This program uses log and log10  
 * to calculate the natural logarithm and  
 * the base-10 logarithm of 9,000.  
 */  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 9000.0;  
   double y;  
  
   y = log( x );  
   printf( "log( %.2f ) = %f\n", x, y );  
   y = log10( x );  
   printf( "log10( %.2f ) = %f\n", x, y );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 若要生成其他底数的对数，请使用数学关系：a 的 log 底数 b == 自然 log (a) / 自然 log （b）。  
  
```  
// logbase.cpp  
#include <math.h>  
#include <stdio.h>  
  
double logbase(double a, double base)  
{  
   return log(a) / log(base);  
}  
  
int main()  
{  
   double x = 65536;  
   double result;  
  
   result = logbase(x, 2);  
   printf("Log base 2 of %lf is %lf\n", x, result);  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、 expf，资源管理器](../../c-runtime-library/reference/exp-expf.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [_CIlog](../../c-runtime-library/cilog.md)   
 [_CIlog10](../../c-runtime-library/cilog10.md)