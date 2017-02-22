---
title: "_control87、_controlfp、__control87_2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_control87"
  - "_controlfp"
  - "__control87_2"
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
  - "_control87"
  - "__control87_2"
  - "control87"
  - "_controlfp"
  - "controlfp"
  - "control87_2"
  - "_control87_2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__control87_2 函数"
  - "_control87 函数"
  - "_controlfp 函数"
  - "control87 函数"
  - "control87_2 函数"
  - "controlfp 函数"
  - "EM_AMBIGUOUS"
  - "浮点函数"
  - "浮点函数, 设置控制字"
  - "浮点数字, 控制字"
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# _control87、_controlfp、__control87_2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取和设置浮点控制字。  一种较为安全的版本`_controlfp` 是有效的；请参见[\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)。  
  
## 语法  
  
```  
unsigned int _control87(   
   unsigned int new,  
   unsigned int mask   
);  
unsigned int _controlfp(   
   unsigned int new,  
   unsigned int mask   
);  
int __control87_2(  
   unsigned int new,  
   unsigned int mask,  
   unsigned int* x86_cw,  
   unsigned int* sse2_cw  
);  
```  
  
#### 参数  
 `new`  
 新的控制字位值。  
  
 `mask`  
 设置新的控制字位的掩码。  
  
 `x86_cw`  
 使用 x87 浮点单元填充控制字。  通过在 0 \(`NULL`\) 设置SSE2控制字。  
  
 `sse2_cw`  
 SSE 浮点单元的控制字。  通过在 0 \(`NULL`\) 设置x87控制字。  
  
## 返回值  
 `_control87` 和 `_controlfp`，按位返回的值指示浮点控制态。  有关由 `_control87`返回位的完整定义，请参见 FLOAT.H。  
  
 对于 `__control87_2`，返回值是 1，指示成功。  
  
## 备注  
 `_control87` 函数获取和设置浮点控制字。  浮点控制字使程序能够根据不同的平台改变精度，舍入，并在浮点数学包无限模式。  还可以使用 `_control87` 掩码或非掩码浮点异常。  如果 `mask` 的值为等于 0，则`_control87` 获取浮点控制字。  如果 `mask` 不为零，控制字的新值被设置：对于在 `mask` 中打开的位\(即等于 1\)，在 `new` 中，对应的位用于更新控制字。  换而言之，`fpcntrl` `=` \(`fpcntrl` `& ~mask`\)&#124;\(`new & mask`\) 其中 `fpcntrl` 是浮点控制字。  
  
> [!NOTE]
>  默认情况下，运行库掩码所有浮点异常。  
  
 `_controlfp` 是的一个独立于平台的，`_control87`的可移植版本。  它几乎相当于在 Intel \(x86\)上 `_control87` 和 ARM 平台的 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 的功能。  如果面向 x86，[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]或 ARM 平台、使用 `_control87` 或 `_controlfp`。  
  
 在 `_control87` 和 `_controlfp` 之间的区别是它们如何处理 DENORMAL 值。  为 Intel \(x86\)，[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]和 ARM 平台，`_control87` 可以设置和清除 DENORMAL 操作的异常掩码。  `_controlfp` 不修改 DENORMAL OPERAND 的异常掩码。  此示例演示不同。  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 常数的掩码的可能值 \(`mask`\) 和新值的控件 \(`new`\) 位于以下十六进制值表所示。  用可移植的常量列出下列 \(`_MCW_EM`，`_EM_INVALID`，等等\) 这些函数的参数，而不是显式提供十六进制值。  
  
 Intel \(x86\) 派生的平台在硬件上支持 DENORMAL 的输入和输出值。  x86 行为是保持 DENORMAL 的值。  具有 SSE2 支持的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台启用 DENORMAL 刷新操作和结果或强制为零。  `_controlfp` 和 `_control87` 函数提供掩码更改此行为。  下面的示例说明掩码的用法。  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，`_control87` 和 `_controlfp` 函数适用于 FPSCR 注册。  在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架构中，只有存储在 MXCSR 注册中的SSE2控制字受到影响。  在 Intel \(x86\) 平台上，`_control87` 和 `_controlfp` 影响 x87 和 SSE2 的控制字。  函数 `__control87_2` 可以同时或分别启用 x87 和 SSE2 浮点单元。  如果你想影响两个单元，传递两个整数的地址到 `x86_cw` 和 `sse2_cw`。  如果希望仅影响一个单元，请传递该参数的地址，但是传递在 0 \(空\) 到其他。  如果 0 为这些被传递的参数之一，函数对该浮点单元没有效果。  此函数可以被用在部分代码使用x87浮点单元并另一部分使用SSE2用浮点单元的情形下。  如果在程序中的一部分使用 `__control87_2` 并将浮点控制字不同的值，然后使用 `_control87` 或 `_controlfp` 进一步操作控制字，则 `_control87` 和 `_controlfp` 可能无法返回一个控件来表示两个浮点单元状态。  在这种情况下，这些函数通过返回的整数值设置 `EM_AMBIGUOUS` 标志来指示有两个控制字之间的不一致。  这是警告说明返回的控制字可能无法准确地表示两个浮点控制字状态。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，更改无限模式或浮点精度是不受支持。  如果精度控件掩码在[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台使用，则该函数来增强声明，并调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
> [!NOTE]
>  `__control87_2` 在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构不受支持。  如果你通过 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构，使用 `__control87_2` 来编译你的程序，编译器会产生错误。  
  
 这些函数被忽略，当您使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 来编译时，这是因为公共语言运行时 \(CLR\) 仅支持默认值浮点精度。  
  
 **十六进制数值**  
  
 `_MCW_EM` 掩码，清除掩码设置异常，允许硬件异常；设置掩码隐藏异常。  如果一个 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 发生，硬件不会抛出异常，直到下浮点命令执行。  若要生成在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`后直接产生的一个硬件异常，请调用 `FWAIT` MASM 指令。  
  
|掩码|十六进制值|常量|十六进制值|  
|--------|-----------|--------|-----------|  
|`_MCW_DN` \(不正常的控件\)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` \(中断异常掩码\)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` \(无限制控件\)<br /><br /> \(不支持 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台。\)|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` \(舍入控件\)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` \(精度控件\)<br /><br /> \(不支持 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台。\)|0x00030000|`_PC_24` （24 位）<br /><br /> `_PC_53` （53 位）<br /><br /> `_PC_64` （64 位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_control87`, `_controlfp`, `_control87_2`|\<float.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_cntrl87.c  
// processor: x86  
// This program uses __control87_2 to output the x87 control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access (on)  
  
int main( void )  
{  
    double a = 0.1;  
    unsigned int control_word_x87;  
  
    // Show original x87 control word and do calculation.  
    control_word_x87 = __control87_2(0, 0,  
                                     &control_word_x87, 0);  
    printf( "Original: 0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Set precision to 24 bits and recalculate.  
    control_word_x87 = __control87_2(_PC_24, MCW_PC,  
                                     &control_word_x87, 0);  
    printf( "24-bit:   0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Restore default precision-control bits and recalculate.  
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,   
                                     &control_word_x87, 0 );  
    printf( "Default:  0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
}  
```  
  
## Output  
  
```  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)