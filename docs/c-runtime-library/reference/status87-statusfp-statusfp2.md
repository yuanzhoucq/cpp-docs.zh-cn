---
title: "_status87, _statusfp, _statusfp2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_statusfp2"
  - "_statusfp"
  - "_status87"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_statusfp2"
  - "_statusfp"
  - "statusfp2"
  - "_status87"
  - "status87"
  - "statusfp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浮点函数, 获取状态字"
  - "浮点数字, 状态字"
  - "status87 函数"
  - "状态字, 获取浮点"
  - "statusfp 函数"
  - "_statusfp 函数"
  - "_statusfp2 函数"
  - "statusfp2 函数"
  - "_status87 函数"
  - "浮点函数"
  - "状态字"
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _status87, _statusfp, _statusfp2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取浮点状态字。  
  
## 语法  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### 参数  
 `px86`  
 此地址填充 x87 浮点单元的状态字。  
  
 `pSSE2`  
 此地址填充 SSE2 浮点单元的状态字。  
  
## 返回值  
 为了 `_status87` 和 `_statusfp`，按位返回的值指示浮点状态。  对由 `_statusfp`返回位的定义参见 FLOAT.H 包含文件。  许多数学库函数修改浮点状态字，伴随着不可预知的结果。  在调用`_status87`, `_statusfp`和相关函数时，优化可以重新排序，结合并消除浮点运算。  使用[\/Od（禁用（调试））](../../build/reference/od-disable-debug.md) 编译器选项或 [fenv\_access](../../preprocessor/fenv-access.md) 编译指令防止重新排列浮点操作的优化。  如果在浮点状态字已知状态内执行较少的浮点操作，从`_clearfp` 和`_statusfp`返回的值以及`_statusfp2`参数的返回更加可信。  
  
## 备注  
 `_statusfp` 函数获取浮点状态字。  状态字是浮点处理器状态和其他情况的组合，它由浮点异常处理程序检测 。例如，浮点堆栈溢出和下溢。  在状态字的内容返回之前，检测发现的异常。  这意味着调用方是合理的挂起异常。  在 x86 平台上，`_statusfp` 返回该 x87 和 SSE2 浮点状态的组合。  在 x64 平台上，返回的状态基于 SSE 的 MXCSR 状态。  在 ARM 平台上，`_statusfp` 返回从 FPSCR 注册的状态。  
  
 `_statusfp` 是一个独立平台，`_status87`的可移植版本。  它与 Intel \(x86\) 平台的 `_status87` 相同， x64 和 ARM 平台也支持。  若要确保您的浮点代码移植到任何体系结构，请使用 `_statusfp`。  如果仅 x86 平台，可以使用 `_status87` 或 `_statusfp`。  
  
 建议使用有 x87 和一个 SSE2 浮点处理器的芯片 `_statusfp2` \(例如 Pentium IV\)。  关于`_statusfp2`，针对 x87 或 SSE2 浮点处理器使用浮点状态字填充地址。  对于支持 x87 和 SSE2 浮点处理器的芯片，如果使用 `_statusfp` 或 `_controlfp`，EM\_AMBIGUOUS 设置为 1，操作不明确，因为它可以指的是 x87 或 SSE2 浮点状态字。  `_statusfp2` 函数只有 x86 平台支持。  
  
 这些函数被忽略，当您使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 来编译时，这是因为公共语言运行时 \(CLR\) 仅支持默认值浮点精度。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **状态 \=0x00000000 \-清除**  
**状态 \= 0x00000003\-不精确，下溢**  
**状态 \= 0x00080003 \-不精确，下溢，不正常**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)