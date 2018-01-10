---
title: "_status87、_statusfp、_statusfp2 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
dev_langs: C++
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f7124b8236550f9e86e04ac56460426a080f137b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2
获取浮点状态字。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### <a name="parameters"></a>参数  
 `px86`  
 此地址用 x87 浮点单元的状态字填充。  
  
 `pSSE2`  
 此地址用 SSE2 浮点单元的状态字填充。  
  
## <a name="return-value"></a>返回值  
 对于 `_status87` 和 `_statusfp` 而言，返回值中的位指示浮点状态。 有关由 `_statusfp` 返回位的定义，请参阅 Float.H 包含文件。 许多数学库函数修改了浮点状态字，结果不可预知。 优化可以围绕对 `_status87`、`_statusfp` 和相关函数的调用进行重新排序、组合和消除浮点运算。 使用 [/Od（禁用（调试））](../../build/reference/od-disable-debug.md)编译器选项或 [fenv_access](../../preprocessor/fenv-access.md) pragma 指令，可防止对浮点操作重新排序的优化。 在浮点状态字的已知状态之间执行的浮点运算越少，`_clearfp` 和 `_statusfp` 的返回值及 `_statusfp2` 返回参数就会越可靠。  
  
## <a name="remarks"></a>备注  
 `_statusfp` 函数获取浮点状态字。 状态字是浮点异常处理程序检测出的浮点处理程序状态和其他条件的组合（例如，浮点堆栈溢出和下溢）。 在返回状态字的内容之前检查未屏蔽的异常。 这表示通知调用方挂起异常。 在 x86 平台上，`_statusfp` 返回 x87 和 SSE2 浮点状态的组合。 在 x64 平台上，返回的状态基于 SSE 的 MXCSR 状态。 在 ARM 平台上，`_statusfp` 从 FPSCR 寄存器返回状态。  
  
 `_statusfp` 是 `_status87` 的一个与平台无关的、可移植的版本。 它与 Intel (x86) 平台上的 `_status87` 相同，并且也受 x64 和 ARM 平台的支持。 若要确保你的浮点代码可移植到所有体系结构，请使用 `_statusfp`。 如果你只面向 x86 平台，可以使用 `_status87` 或 `_statusfp`。  
  
 对于同时具有 x87 和 SSE2 浮点处理器的芯片（如 Pentium IV），我们建议使用 `_statusfp2`。 对于 `_statusfp2`，使用 x87 或 SSE2 浮点处理器的浮点状态字填充地址。 对于支持 x87 和 SSE2 浮点处理器的芯片，如果使用 `_statusfp` 或 `_controlfp`，并且该操作不明确，则将 EM_AMBIGUOUS 设置为 1，因为它可以引用 x87 或 SSE2 浮点状态字。 `_statusfp2` 函数仅在 x86 平台上受支持。  
  
 这些函数不是用于[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时 (CLR) 仅支持默认的浮点精度。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_statusfp.c  
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c  
// This program creates various floating-point errors and  
// then uses _statusfp to display messages that indicate these problems.  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access(on)  
  
double test( void )  
{  
   double a = 1e-40;  
   float b;  
   double c;  
  
   printf("Status = 0x%.8x - clear\n", _statusfp());  
  
   // Assignment into b is inexact & underflows:   
   b = (float)(a + 1e-40);  
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());  
  
   // c is denormal:   
   c = b / 2.0;   
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",   
            _statusfp());  
  
   // Clear floating point status:   
   _clearfp();  
   return c;  
}  
  
int main(void)  
{  
   return (int)test();  
}  
```  
  
```Output  
Status = 0x00000000 - clear  
Status = 0x00000003 - inexact, underflow  
Status = 0x00080003 - inexact, underflow, denormal  
```  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)