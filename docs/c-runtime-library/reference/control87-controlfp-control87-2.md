---
title: _control87、_controlfp、__control87_2
ms.date: 08/29/2019
api_name:
- _control87
- _controlfp
- __control87_2
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 15700a5dabfbc3f8915e251bd8b9270f8f9c1a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942907"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87、_controlfp、__control87_2

获取并设置浮点控制字。 **_Controlfp**的更安全版本可用;请参阅[_controlfp_s](controlfp-s.md)。

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

*new*\
新的控制字位值。

*掩盖*\
要设置的新控制字位掩码。

*x86_cw*\
使用 x87 浮点单元的控制字进行填充。 传入0（**NULL**），只设置 SSE2 控制字。

*sse2_cw*\
SSE 浮点单元的控制字。 传入0（**NULL**）以仅设置 x87 控件字。

## <a name="return-value"></a>返回值

对于 **_control87**和 **_controlfp**，返回值中的位表示浮点控制状态。 有关 **_control87**返回的位的完整定义，请参阅 FLOAT。高.

对于 **__control87_2**，返回值为1，表示成功。

## <a name="remarks"></a>备注

**_Control87**函数获取并设置浮点控制字。 浮点控制字使程序可以更改精度、舍入和无穷模式，具体取决于平台。 还可以使用 **_control87**来屏蔽或取消屏蔽浮点异常。 如果*mask*的值等于0，则 **_control87**将获取浮点控制字。 如果*掩码*为非零值，则将设置一个新的控制字值：对于*掩码*中的任何位（即等于1）， *new*中的相应位用于更新控制字。 换句话说， **fpcntrl** = （（**fpcntrl** & ~*mask*） &#124; （*新* & *掩码*）），其中**fpcntrl**是浮点控制字。

> [!NOTE]
> 默认情况下，运行时库屏蔽所有浮点异常。

**_controlfp**是一种独立于平台、可移植的 **_control87**版本，几乎与 **_control87**函数相同。 如果你的代码针对多个平台，请使用 **_controlfp**或 **_controlfp_s**。 **_Control87**和 **_controlfp**之间的区别在于它们如何处理 DENORMAL 值。 对于 x86、x64、ARM 和 ARM64 平台， **_control87**可以设置和清除 DENORMAL 操作数异常掩码。 **_controlfp**不会修改 DENORMAL 操作数异常掩码。 此示例演示了差别：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

掩码常量（*掩码*）和新控件值（*新*）的可能值显示在 "控制文字掩码" 和 "值" 表中。 使用下面列出的可移植常量（ **_MCW_EM**、 **_EM_INVALID**等）作为这些函数的参数，而不是显式提供十六进制值。

Intel x86 派生平台支持硬件中的 DENORMAL 输入和输出值。 x86 行为是为了保留 DENORMAL 值。 ARM 和 ARM64 平台以及具有 SSE2 支持的 x64 平台启用 DENORMAL 操作数和结果，或将其强制为零。 **_Controlfp**和 **_control87**函数提供了一个用于更改此行为的掩码。 下面的示例演示此掩码的使用。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 和 ARM64 平台上， **_control87**和 **_controlfp**函数适用于 FPSCR 寄存器。 在 x64 平台上，只会影响存储在 MXCSR 寄存器中的 SSE2 控制字。 在 x86 平台上， **_control87**和 **_controlfp**会影响 x87 和 SSE2 的控制字（如果存在）。

函数 **__control87_2**可同时或单独控制 X87 和 SSE2 浮点单元。 若要同时影响两个单位，请将两个整数的地址传递给**x86_cw**和**sse2_cw**。 如果只想要影响一个单位，请传入该参数的地址，但为其传入0（**NULL**）。 如果为其中一个参数传递了 0，则函数对该浮点单元没有影响。 当部分代码使用 x87 浮点单元时，此方法非常有用，而另一部分则使用 SSE2 浮点单元。

如果使用 **__control87_2**为浮点控制字设置不同的值，则 **_control87**或 **_controlfp**可能无法返回单个控制字来表示两个浮点单元的状态。 在这种情况下，这些函数将在返回的整数值中设置**EM_AMBIGUOUS**标志，以指示这两个控制字之间存在不一致。 **EM_AMBIGUOUS**标志是一条警告，指出返回的控制字可能并不准确表示这两个浮点控制字的状态。

在 ARM、ARM64 和 x64 平台上，不支持更改无穷大模式或浮点精度。 如果在 x64 平台上使用精度控制掩码，则函数将引发断言，并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

> [!NOTE]
> ARM、ARM64 或 x64 平台上不支持 **__control87_2** 。 如果使用 **__control87_2**并为 ARM、ARM64 或 x64 平台编译程序，编译器将生成错误。

使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)编译时，这些函数将被忽略。 公共语言运行时（CLR）仅支持默认的浮点精度。

### <a name="control-word-masks-and-values"></a>控制单词掩码和值

对于 **_MCW_EM**掩码，清除掩码将设置允许硬件例外的异常;设置掩码将隐藏异常。 如果发生 **_EM_UNDERFLOW**或 **_EM_OVERFLOW** ，则在执行下一个浮点指令之前，不会引发任何硬件异常。 若要在 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**之后立即生成硬件异常，请调用**FWAIT** MASM 指令。

|掩码|十六进制值|返回的常量|十六进制值|
|----------|---------------|--------------|---------------|
|**_MCW_DN**（Denormal 控件）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM**（中断异常掩码）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC**（无限大控制）<br /><br /> （在 ARM 或 x64 平台上不受支持。）|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC**（舍入控制）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC**（精度控制）<br /><br /> （在 ARM 或 x64 平台上不受支持。）|0x00030000|**_PC_24**（24位）<br /><br /> **_PC_53**（53位）<br /><br /> **_PC_64**（64位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_control87**、 **_controlfp**、 **_control87_2**|\<float.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)\
[_clear87、_clearfp](clear87-clearfp.md)\
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
