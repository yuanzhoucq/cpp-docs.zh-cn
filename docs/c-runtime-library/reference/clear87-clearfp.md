---
title: "_clear87、_clearfp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
dev_langs: C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fb487a2db1938c173a8b926319adcfb57fc7e80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clear87-clearfp"></a>_clear87、_clearfp
获取并清除浮点状态字。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _clear87( void );  
unsigned int _clearfp( void );  
```  
  
## <a name="return-value"></a>返回值  
 返回值中的位表示调用 `_clear87` 或 `_clearfp` 之前的浮点状态。 有关由 `_clear87` 返回的位的完整定义，请参阅 Float.h。 许多数学库函数修改了 8087/80287 状态字，结果不可预知。 在浮点状态字的已知状态之间执行的浮点运算越少，`_clear87` 和 `_status87` 的返回值就会越可靠。  
  
## <a name="remarks"></a>备注  
 `_clear87` 函数将清除浮点状态字中的异常标记，将繁忙位设置为 0，并返回状态字。 浮点状态字是 8087/80287 状态字和通过 8087/80287 异常处理程序检测到的其他条件（如浮点堆栈上溢和下溢）组合而成。  
  
 `_clearfp` 是 `_clear87` 例程的一个与平台无关的、可移植的版本。 它与 Intel (x86) 平台上的 `_clear87` 相同，并且也受 x64 和 ARM 平台的支持。 若要确保你的浮点代码可移植到 x64 和 ARM，请使用 `_clearfp`。 如果你只面向 x86 平台，可以使用 `_clear87` 或 `_clearfp`。  
  
 这些函数在编译时被弃用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时仅支持默认的浮点精度。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_clear87`|\<float.h>|  
|`_clearfp`|\<float.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_clear87.c  
// compile with: /Od  
  
// This program creates various floating-point   
// problems, then uses _clear87 to report on these problems.  
// Compile this program with Optimizations disabled (/Od).   
// Otherwise the optimizer will remove the code associated with   
// the unused floating-point values.  
//  
  
#include <stdio.h>  
#include <float.h>  
  
int main( void )  
{  
   double a = 1e-40, b;  
   float x, y;  
  
   printf( "Status: %.4x - clear\n", _clear87()  );  
  
   // Store into y is inexact and underflows:  
   y = a;  
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );  
  
   // y is denormal:   
   b = y;  
   printf( "Status: %.4x - denormal\n", _clear87() );  
}  
```  
  
```Output  
Status: 0000 - clear  
Status: 0003 - inexact, underflow  
Status: 80000 - denormal  
```  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)