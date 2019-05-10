---
title: _control87、_controlfp、__control87_2
ms.date: 04/05/2018
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
ms.openlocfilehash: e2ebfdc80a451ebf02563f78a62dd08618f92bcd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340412"
---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2

获取并设置浮点控制字。 更安全的版本 **_controlfp**有; 请参阅[_controlfp_s](controlfp-s.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*new*<br/>
新的控制字位值。

*mask*<br/>
要设置的新控制字位掩码。

*x86_cw*<br/>
使用 x87 浮点单元的控制字进行填充。 传入 0 (**NULL**) 设置 SSE2 控制字。

*sse2_cw*<br/>
SSE 浮点单元的控制字。 传入 0 (**NULL**) 来仅设置 x87 控制字。

## <a name="return-value"></a>返回值

有关 **_control87**并 **_controlfp**，值中的位返回表示浮点控制状态。 对于返回的位的完整定义 **_control87**，请参阅 FLOAT。H.

有关 **__control87_2**，返回值为 1，表示成功。

## <a name="remarks"></a>备注

**_Control87**函数获取并设置浮点控制字。 浮点控制字允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 此外可以使用 **_control87**屏蔽或取消屏蔽浮点异常。 如果为值*掩码*等于 0， **_control87**获取浮点控制字。 如果*掩码*为非零值，将设置为控制字为新值：对于任何位，位于 （即等于 1） 中*掩码*中的对应位*新*用于更新控制字。 换而言之， **fpcntrl** = ((**fpcntrl** & ~*掩码*) &#124; (*新* & *掩码*))其中**fpcntrl**是浮点控制字。

> [!NOTE]
> 默认情况下，运行时库屏蔽所有浮点异常。

**_controlfp**是一个独立于平台的、 可移植的版本 **_control87**。 它几乎等同于 **_control87** x86、 x64 和 ARM 平台上的函数。 如果你正面向 x86、 x64 或 ARM 平台，使用 **_control87**或 **_controlfp**。

之间的差异 **_control87**并 **_controlfp**在于它们看待 DENORMAL 值的方式。 X86、 x64 和 ARM 平台 **_control87**可以设置并清除 DENORMAL OPERAND 异常掩码。 **_controlfp**不会修改 DENORMAL OPERAND 异常掩码。 此示例演示了差别：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

掩码常量的可能值 (*掩码*) 和新的控制值 (*新*) 下的十六进制值表中所示。 使用下面列出的可移植常量 (**_MCW_EM**， **_EM_INVALID**，依此类推) 作为这些函数的参数，而不是提供十六进制值显式。

Intel x86 派生的平台支持的 DENORMAL 输入和输出在硬件中的值。 x86 行为是为了保留 DENORMAL 值。 ARM 平台和 x64 平台具有 SSE2 支持启用 DENORMAL 操作数和结果，以刷新，或强制为零。 **_Controlfp**并 **_control87**函数提供更改此行为的掩码。 下面的示例演示此掩码的使用。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台上 **_control87**并 **_controlfp**函数应用于 FPSCR 寄存器。 在 x64 体系结构中，仅存储的 SSE2 控制字 MXCSR 寄存器受到影响。 在 x86 平台， **_control87**并 **_controlfp**如果存在会影响对 x87 和 SSE2 的控制字。 该函数 **__control87_2**允许对 x87 和 SSE2 浮点单位一起或单独控制。 如果你想要影响这两个单元，则传入到两个整数的地址**x86_cw**并**sse2_cw**。 如果只想要影响一个单元，地址传递给该参数，但传入 0 (**NULL**) 其他。 如果为其中一个参数传递了 0，则函数对该浮点单元没有影响。 对于一部分代码使用 x87 浮点单元而另一部分代码使用 SSE2 浮点单元的情况而言，此功能很有用。 如果您使用 **__control87_2**中某个部件的程序并设置浮点控制字，不同的值以及如何将 **_control87**或 **_controlfp**进一步操作控制字，然后 **_control87**并 **_controlfp**可能无法返回单个控制字来表示这两个浮点单元的状态。 在这种情况下，这些函数将设置**EM_AMBIGUOUS**中返回的整数值，以指示两个控制字之间不存在不一致的标志。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。

在 ARM 和 x64 上不支持更改无穷模式或浮点精度的体系结构。 如果在 x64 上使用精度控制掩码平台，该函数引发断言并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

> [!NOTE]
> **__control87_2**不支持 ARM 或 x64 体系结构。 如果您使用 **__control87_2**并将程序编译为 ARM 或 x64 体系结构中，编译器将生成错误。

当你使用时，将忽略这些函数[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)来进行编译，因为公共语言运行时 (CLR) 仅支持默认浮点精度。

**十六进制值**

有关 **_MCW_EM**掩码，清除掩码将设置异常，这会允许硬件异常; 设置掩码可隐藏异常。 如果 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**发生，直到执行下一步浮点指令会引发任何硬件异常。 若要生成硬件异常后立即 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**，调用**FWAIT** MASM 指令。

|掩码|十六进制值|返回的常量|十六进制值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （非常规控制）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （中断异常掩码）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （无穷控制）<br /><br /> (不支持 ARM 或 x64] 的平台。)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （舍入控制）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精度控制）<br /><br /> （不支持 ARM 或 x64 平台。）|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** （53 位）<br /><br /> **_PC_64** （64 位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_control87**， **_controlfp**， **_control87_2**|\<float.h>|

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

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
