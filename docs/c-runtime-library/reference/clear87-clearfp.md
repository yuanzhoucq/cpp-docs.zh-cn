---
title: "_clear87、_clearfp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 7c7659bb52594678538ea2701174c070ace41d70
ms.lasthandoff: 02/24/2017

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
  
 使用编译时，这些函数被弃用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时仅支持默认浮点精度。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_clear87`|\<float.h>|  
|`_clearfp`|\<float.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)
