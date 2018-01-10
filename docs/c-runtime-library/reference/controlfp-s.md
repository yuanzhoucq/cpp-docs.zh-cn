---
title: "_controlfp_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _controlfp_s
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
- controlfp_s
- _controlfp_s
dev_langs: C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8c8f651e04a1d68cd27f8321d6a30250c0e6ce1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="controlfps"></a>_controlfp_s
获取并设置浮点控制字。 此版本的 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _controlfp_s(  
    unsigned int *currentControl,  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>参数  
 `currentControl`  
 当前控制字位值。  
  
 `newControl`  
 新的控制字位值。  
  
 `mask`  
 要设置的新控制字位掩码。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；否则为 `errno` 值错误代码。  
  
## <a name="remarks"></a>备注  
 `_controlfp_s` 函数是 `_control87` 的一个与平台无关的、更安全的版本，它将浮点控制字置入存储于 `currentControl` 中的地址，并使用 `newControl` 对其进行设置。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 还可使用 `_controlfp_s` 屏蔽或取消屏蔽浮点异常。  
  
 如果 `mask` 的值等于 0，则 `_controlfp_s` 获取浮点控制字，并存储 `currentControl` 中检索到的值。  
  
 如果 `mask` 为非零的值，则为控制字设置新值：对于 `mask` 中设置的任何位（即等于 1），`new` 中的对应位被用于更新控制字。 即，`fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`)) 其中 `fpcntrl` 是浮点控制字。 在此方案中，`currentControl` 在更改完成后被设置为该值；它并非旧的控制字位值。  
  
> [!NOTE]
>  默认情况下，运行时库屏蔽所有浮点异常。  
  
 `_controlfp_s` 几乎等同于 Intel (x86) 上的 `_control87` 函数、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 以及 ARM 平台。 如果你正面向 x86、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 平台，则可以使用 `_control87` 或 `_controlfp_s`。  
  
 `_control87` 和 `_controlfp_s` 之间的差异在于它们看待 `DENORMAL` 值的方式。 对于 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台，`_control87` 可以设置并清除 DENORMAL OPERAND 异常掩码。 `_controlfp_s` 不会修改 DENORMAL OPERAND 异常掩码。 此示例演示了差别：  
  
```C  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call.  
unsigned int current_word = 0;  
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged.  
```  
  
 下列十六进制值表中显示了掩码常量的可能值 (`mask`) 和新的控制值 (`newControl`)。 请使用下面列出的可移植常量 （`_MCW_EM``_EM_INVALID`，等等）作为这些函数的参数，而不是显式提供十六进制值。  
  
 Intel (x86) 派生的平台支持硬盘中的 DENORMAL 输入和输出值。 x86 行为是为了保留 DENORMAL 值。 具有 SSE2 支持的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台允许刷新DENORMAL 操作数和结果，或强制为零。 `_controlfp_s`、`_controlfp` 和 `_control87` 函数提供更改此行为的掩码。 下面的示例演示此掩码的使用：  
  
```C  
unsigned int current_word = 0;  
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，将 `_controlfp_s` 函数应用于 FPSCR 寄存器。 在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，仅存储在 MXCSR 寄存器中的 SSE2 控制字受到影响。 在 Intel (x86) 平台上，`_controlfp_s` 会对 x87 和 SSE2 的控制字（如果存在）产生影响。 两个控制字有可能彼此不一致（例如，因为之前调用了 [__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)）；如果在两个控制字之间存在不一致性，则 `_controlfp_s` 将在 `currentControl` 中设置 `EM_AMBIGUOUS` 标志。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，不支持更改无穷模式或浮点精度。 如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上使用精度控制掩码，则函数引发断言并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如果未正确设置掩码，则此函数生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
 当你使用此函数将忽略[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)来编译，因为公共语言运行时 (CLR) 仅支持默认的浮点精度。  
  
### <a name="mask-constants-and-values"></a>掩码常量和值  
  
 对于 `_MCW_EM` 掩码，清除掩码将设置异常，这会允许硬件异常；设置它可隐藏异常。 如果出现 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`，则在执行下一步浮点指令之前，不会引发任何硬盘异常。 若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 后立即生成硬件异常，请调用 FWAIT MASM 指令。  
  
|掩码|十六进制值|返回的常量|十六进制值|  
|----------|---------------|--------------|---------------|  
|`_MCW_DN` （非常规控制）|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM`（中断异常掩码）|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC`（无穷控制）<br /><br /> （在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上不受支持。）|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC`舍入控制）|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC`（精度控制）<br /><br /> （在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上不受支持。）|0x00030000|`_PC_24`（24 位）<br /><br /> `_PC_53`（53 位）<br /><br /> `_PC_64`（64 位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_controlfp_s`|\<float.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```C  
// crt_contrlfp_s.c  
// processor: x86  
// This program uses _controlfp_s to output the FP control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
  
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
  
```Output  
Original: 0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0xa001f  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x9001f  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)