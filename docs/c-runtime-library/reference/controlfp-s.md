---
title: "_controlfp_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_controlfp_s"
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
  - "controlfp_s"
  - "_controlfp_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_controlfp_s 函数"
  - "controlfp_s 函数"
  - "EM_AMBIGUOUS"
  - "浮点函数, 设置控制字"
  - "浮点数字, 控制字"
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _controlfp_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取和设置浮点控制字。  [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 的这些版本的安全得到了增强，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 语法  
  
```  
errno_t _controlfp_s(  
    unsigned int *currentControl,  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### 参数  
 `currentControl`  
 当前控制字位的值。  
  
 `newControl`  
 新的控制字位值。  
  
 `mask`  
 设置新的控制字位的掩码。  
  
## 返回值  
 如果成功，则为零；如果失败，则为`errno` 值的错误代码。  
  
## 备注  
 `_controlfp_s` 函数是 `_control87`的一个独立于平台的和更安全版本，它得到存储在`currentControl`的浮点控制字输入地址，并通过使用 `newControl`设置它。  按位值指示浮点控制态。  浮点控制状态使程序能够根据不同的平台改变精度，舍入，并在浮点数学包无限模式。  还可以使用 `_controlfp_s` 掩码或非掩码浮点异常。  
  
 如果 `mask` 的值为等于 0，`_controlfp_s` 获取浮点控制字并存储在`currentControl`的检索值。  
  
 如果 `mask` 不为零，控制字的新值被设置：对于设置在 `mask` 中的位\(即等于 1\)，在 `new` 中对应的位用于更新控制字。  换而言之，`fpcntrl` `=` \(`fpcntrl` `& ~mask`\)&#124;\(`new & mask`\) 其中 `fpcntrl` 是浮点控制字。  在此方案中，在更改完成后，`currentControl` 设置为值；它不是旧控制字的位值。  
  
> [!NOTE]
>  默认情况下，运行库掩码所有浮点异常。  
  
 `_controlfp_s`它几乎相当于在 Intel \(x86\)上 的`_control87`函数，[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]和ARM平台。  如果面向 x86、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]或 ARM 平台，可以使用 `_control87` 或 `_controlfp_s`。  
  
 `_control87` 和 `_controlfp_s` 之间的区别在于它们如何处理`DENORMAL`值。  为 Intel \(x86\)，[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]和 ARM 平台，`_control87` 可以设置和清除 DENORMAL OPERAND的异常掩码。  `_controlfp_s` 不修改 DENORMAL OPERAND 的异常掩码。  此示例演示不同。  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call.  
unsigned int current_word = 0;  
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged.  
```  
  
 常数的掩码的可能值 \(`mask`\) 和新值的控件 \(`newControl`\) 位于以下十六进制值表所示。  用下面列出的可移植常量 \(`_MCW_EM`，`_EM_INVALID`，等等\) 作为参数给这些函数，而不是显式提供十六进制值。  
  
 Intel \(x86\) 派生的平台在硬件上支持 DENORMAL 的输入和输出值。  x86 行为是保持 DENORMAL 的值。  具有 SSE2 支持的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台启用 DENORMAL 刷新操作和结果或强制为零。  `_controlfp_s`，`_controlfp`和`_control87` 函数提供掩码更改此行为。  下面的示例说明掩码的用法:  
  
```  
unsigned int current_word = 0;  
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，`_controlfp_s` 函数用于 FPSCR 注册。  在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架构中，只有存储在 MXCSR 注册中的SSE2控制字受到影响。  在 Intel \(x86\) 平台上，`_controlfp_s`影响 x87 和 SSE2 的控制字\(如果存在\)。  两个控制字可能是互相不一致\(例如由于以前调用 [\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)\);如果存在两个控制字之间的不一致，`_controlfp_s` 在 `currentControl`中设置 `EM_AMBIGUOUS` 标志。  这是警告说明返回的控制字可能无法准确地表示两个浮点控制字状态。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，更改无限模式或浮点精度是不受支持。  如果精度控件掩码在[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台使用，则该函数来增强声明，并调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
 如果掩码未正确设置，此函数生成无效的参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这函数返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
 当您使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 来编译时，这些函数被忽略，这是因为公共语言运行时 \(CLR\) 仅支持默认值浮点精度。  
  
 **十六进制数值**  
  
 关于`_MCW_EM` 掩码，清除它引发异常，它允许硬件异常；设置为隐藏异常。  如果一个 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 发生，硬件不会抛出异常，直到下浮点命令执行。  若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`后直接产生的一个硬件异常，请调用FWAIT MASM 指令。  
  
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
|`_controlfp_s`|\<float.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_contrlfp_s.c  
// processor: x86  
// This program uses _controlfp_s to output the FP control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access (on)  
  
int main( void )  
{  
    double a = 0.1;  
    unsigned int control_word;  
    int err;  
  
    // Show original FP control word and do calculation.  
    err = _controlfp_s(&control_word, 0, 0);  
    if ( err ) /* handle error here */;  
  
    printf( "Original: 0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Set precision to 24 bits and recalculate.  
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);  
    if ( err ) /* handle error here */;  
  
    printf( "24-bit:   0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Restore default precision-control bits and recalculate.  
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);  
    if ( err ) /* handle error here */;  
  
    printf( "Default:  0x%.4x\n", control_word );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
}  
```  
  
## Output  
  
```  
Original: 0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0xa001f  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)