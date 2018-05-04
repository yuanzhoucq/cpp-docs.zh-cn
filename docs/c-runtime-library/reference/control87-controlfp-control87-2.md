---
title: _control87、_controlfp、__control87_2 | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 098e5760718e4e2d2a9063700b09d0381e76df1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2

获取并设置浮点控制字。 更安全的版本 **_controlfp**是可用; 请参阅[_controlfp_s](controlfp-s.md)。

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

*掩码*<br/>
要设置的新控制字位掩码。

*x86_cw*<br/>
使用 x87 浮点单元的控制字进行填充。 请传入 0 (**NULL**) 以设置 SSE2 控制字。

*sse2_cw*<br/>
SSE 浮点单元的控制字。 请传入 0 (**NULL**) 设置仅 x87 控制 word。

## <a name="return-value"></a>返回值

有关 **_control87**和 **_controlfp**中值, 的位返回表示浮点控制状态。 有关通过返回的位的完整定义 **_control87**，请参阅浮点数。H。

有关 **__control87_2**，返回值为 1，这表示成功。

## <a name="remarks"></a>备注

**_Control87**函数获取和设置浮点控制字。 浮点控制字允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 你还可以使用 **_control87**屏蔽或取消屏蔽浮点异常。 如果值*掩码*等于 0， **_control87**获取浮点控制字。 如果*掩码*是新的控制字值设置为零，： 位于任何位 （即，等于 1） 在*掩码*中的对应位*新*用于更新控件word。 换而言之， **fpcntrl** = ((**fpcntrl** & ~*掩码*) &#124; (*新* & *掩码*))其中**fpcntrl**是浮点控制字。

> [!NOTE]
> 默认情况下，运行时库屏蔽所有浮点异常。

**_controlfp**是独立于平台的版本，并且可移植的 **_control87**。 它几乎等同于 **_control87** x86、 x64 和 ARM 平台上的函数。 如果你正面向 x86、 x64 或 ARM 平台上，使用 **_control87**或 **_controlfp**。

之间的差异 **_control87**和 **_controlfp**处于它们如何处理 DENORMAL 值。 X86、 x64 和 ARM 平台上，为 **_control87**可以设置和清除非常规操作数异常掩码。 **_controlfp**不会修改非常规操作数异常掩码。 此示例演示了差别：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

掩码常量的可能值 (*掩码*) 和控件的新值 (*新*) 下的十六进制值表中显示。 使用下面列出的可移植常量 (**_MCW_EM**， **_EM_INVALID**，依此类推) 作为对这些函数的自变量，而不是提供十六进制值显式。

Intel x86 派生平台支持 DENORMAL 输入和输出硬件中的值。 x86 行为是为了保留 DENORMAL 值。 ARM 平台和 x64 平台具有 SSE2 支持启用 DENORMAL 操作数和结果，以刷新，或强制为零。 **_Controlfp**和 **_control87**函数提供的掩码要更改此行为。 下面的示例演示此掩码的使用。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台上， **_control87**和 **_controlfp**函数应用于 FPSCR 寄存器。 在 x64 体系结构中，仅存储 SSE2 控制字 MXCSR 注册受到影响。 在 x86 平台， **_control87**和 **_controlfp**影响 x87 和 SSE2 的控制字，如果存在。 该函数 **__control87_2**使 x87 和 SSE2 浮点单位单独或一起进行控制。 如果你想要影响这两个单元，则传入到两个整数的地址**x86_cw**和**sse2_cw**。 如果仅想影响一个单元，则传入该参数的地址，但为另一个单元传入 0 (NULL)。 如果为其中一个参数传递了 0，则函数对该浮点单元没有影响。 对于一部分代码使用 x87 浮点单元而另一部分代码使用 SSE2 浮点单元的情况而言，此功能很有用。 如果你使用 **__control87_2**程序的一部分中和设置浮点控制字，不同的值，然后使用 **_control87**或 **_controlfp**进一步然后操作控制字， **_control87**和 **_controlfp**可能导致无法返回单个控件单词以表示这两个浮点单元状态。 在这种情况下，这些函数将设置**EM_AMBIGUOUS**中返回的整数值，指示两个控件单词之间不一致的标志。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。

在 ARM 和 x64 体系结构，更改无穷大模式或的浮点精度不支持。 如果在 x64 上使用的精度控制掩码平台，该函数引发了断言并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

> [!NOTE]
> **__control87_2**不支持 ARM 或 x64 体系结构。 如果你使用 **__control87_2**和编译你的程序对于 ARM 或 x64 体系结构，编译器将生成错误。

当你使用这些函数将忽略[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)来编译，因为公共语言运行时 (CLR) 仅支持默认的浮点精度。

**十六进制值**

有关 **_MCW_EM**掩码，清除掩码设置允许的硬件异常的异常; 设置掩码隐藏异常。 如果 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**发生，直到执行下一步的浮点指令不引发任何硬件异常。 生成硬件异常后立即 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**，调用**FWAIT** MASM 指令。

|掩码|十六进制值|返回的常量|十六进制值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （不正常控制）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （中断异常掩码）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （无穷大控件）<br /><br /> (不在 ARM 或 x64 上受支持] 平台。)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （舍入控件）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精度控制）<br /><br /> （不支持在 ARM 或 x64 平台。）|0x00030000|**_PC_24** （24 位）<br /><br /> **_PC_53** （53 位）<br /><br /> **_PC_64** （64 位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>要求

|例程|必需的标头|
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
