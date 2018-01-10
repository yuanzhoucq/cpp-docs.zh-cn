---
title: "_control87、_controlfp、__control87_2 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
dev_langs: C++
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c4c6188917737e46807979d5f4a7fec350cb3e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2
获取并设置浮点控制字。 `_controlfp` 有一个更安全的版本；请参阅 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `new`  
 新的控制字位值。  
  
 `mask`  
 要设置的新控制字位掩码。  
  
 `x86_cw`  
 使用 x87 浮点单元的控制字进行填充。 传入 0 (`NULL`) 来仅设置 SSE2 控制字。  
  
 `sse2_cw`  
 SSE 浮点单元的控制字。 传入 0 (`NULL`) 来仅设置 x87 控制字。  
  
## <a name="return-value"></a>返回值  
 对于 `_control87` 和 `_controlfp` 而言，返回值中的位表示浮点控制状态。 有关由 `_control87` 返回的位的完整定义，请参阅 Float.H。  
  
 对于 `__control87_2`，返回值为 1，表示成功。  
  
## <a name="remarks"></a>备注  
 `_control87` 函数获取并设置浮点控制字。 浮点控制字允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 还可使用 `_control87` 屏蔽或取消屏蔽浮点异常。 如果 `mask` 的值等于 0，则 `_control87` 获取浮点控制字。 如果 `mask` 为非零的值，则为控制字设置新值：对于 `mask` 中已设置的任何位（即等于 1），`new` 中的对应位被用于更新控制字。 即，`fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`)) 其中 `fpcntrl` 是浮点控制字。  
  
> [!NOTE]
>  默认情况下，运行时库屏蔽所有浮点异常。  
  
 `_controlfp` 是 `_control87` 的一个与平台无关的、可移植的版本。 它几乎等同于 Intel (x86) 上的 `_control87` 函数、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 以及 ARM 平台。 如果你正面向 x86、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 平台，则使用 `_control87` 或 `_controlfp`。  
  
 `_control87` 和 `_controlfp` 之间的差异在于它们看待 DENORMAL 值的方式。 对于 Intel (x86)、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台，`_control87` 可以设置并清除 DENORMAL OPERAND 异常掩码。 `_controlfp` 不会修改 DENORMAL OPERAND 异常掩码。 此示例演示了差别：  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 下列十六进制值表中显示了掩码常量的可能值 (`mask`) 和新的控制值 (`new`)。 请使用下面列出的可移植常量 （`_MCW_EM`、`_EM_INVALID`，依此类推）作为这些函数的参数，而不是显式提供十六进制值。  
  
 Intel (x86) 派生的平台支持硬盘中的 DENORMAL 输入和输出值。 x86 行为是为了保留 DENORMAL 值。 具有 SSE2 支持的 ARM 平台和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台允许刷新DENORMAL 操作数和结果，或强制为零。 `_controlfp` 和 `_control87` 函数提供更改此行为的掩码。 下面的示例演示此掩码的使用。  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 在 ARM 平台上，将 `_control87` 和 `_controlfp` 函数应用于 FPSCR 寄存器。 在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，仅存储在 MXCSR 寄存器中的 SSE2 控制字受到影响。 在 Intel (x86) 平台上，`_control87` 和 `_controlfp` 会对 x87 和 SSE2 的控制字（如果存在）产生影响。 函数 `__control87_2` 一起或单独控制 x87 和 SSE2 浮点单位。 如果想要影响这两个单元，将这两个整数的地址传入 `x86_cw` 和 `sse2_cw`。 如果仅想影响一个单元，则传入该参数的地址，但为另一个单元传入 0 (NULL)。 如果为其中一个参数传递了 0，则函数对该浮点单元没有影响。 对于一部分代码使用 x87 浮点单元而另一部分代码使用 SSE2 浮点单元的情况而言，此功能很有用。 如果将 `__control87_2` 用于某个程序的一部分，并为浮点控制字设置不同值，然后使用 `_control87` 或 `_controlfp` 进一步操作控制字，则 `_control87` 和 `_controlfp` 可能无法返回表示这两个浮点单元状态的单个控制字。 在这种情况下，这些函数在返回的整数值中设置 `EM_AMBIGUOUS` 标志，以表示在两个控制字之间存在不一致性。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。  
  
 在 ARM 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中，不支持更改无穷模式或浮点精度。 如果在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台上使用精度控制掩码，则函数引发断言并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
> [!NOTE]
>  `__control87_2` 在 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构中不受支持。 如果使用 `__control87_2` 并为 ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 体系结构编译程序，编译器将生成错误。  
  
 当你使用这些函数将忽略[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)来编译，因为公共语言运行时 (CLR) 仅支持默认的浮点精度。  
  
 **十六进制值**  
  
 对于 `_MCW_EM` 掩码，清除掩码将设置异常，这会允许硬盘异常；设置掩码可隐藏异常。 如果出现 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW`，则在执行下一步浮点指令之前，不会引发任何硬盘异常。 若要在 `_EM_UNDERFLOW` 或 `_EM_OVERFLOW` 后立即生成硬件异常，请调用 `FWAIT` MASM 指令。  
  
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
|`_control87`, `_controlfp`, `_control87_2`|\<float.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```C  
// crt_cntrl87.c  
// processor: x86  
// This program uses __control87_2 to output the x87 control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
  
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
  
```Output  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)