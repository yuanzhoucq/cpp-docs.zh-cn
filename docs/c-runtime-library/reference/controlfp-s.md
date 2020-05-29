---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 0e734a0286ac21ed0883cc10b0cd4ee5857ba448
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917268"
---
# <a name="_controlfp_s"></a>_controlfp_s

获取并设置浮点控制字。 此版本的 [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>参数

*currentControl*<br/>
当前控制字位值。

*newControl*<br/>
新的控制字位值。

*掩码*<br/>
要设置的新控制字位掩码。

## <a name="return-value"></a>返回值

如果成功，则为零; 否则为**errno**值错误代码。

## <a name="remarks"></a>备注

**_Controlfp_s**函数是一种独立于平台的、更安全的 **_control87**版本，它将浮点控制字转换为存储在*currentControl*中的地址，并使用*newControl*对其进行设置。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 你还可以使用 **_controlfp_s**来屏蔽或取消屏蔽浮点异常。

如果*mask*的值等于0，则 **_controlfp_s**获取浮点控制字，并将检索到的值存储在*currentControl*中。

如果*掩码*为非零值，则将设置一个新的控制字值：对于*掩码*中设置的任何位（即等于1）， *new*中的相应位用于更新控制字。 换句话说， *fpcntrl* = （（*fpcntrl* & ~*mask*） &#124; （*newControl* & *mask*）），其中*fpcntrl*是浮点控制字。 在这种情况下，在更改完成后， *currentControl*设置为值;它不是旧的控制字位值。

> [!NOTE]
> 默认情况下，运行时库屏蔽所有浮点异常。

**_controlfp_s**与 Intel （x86）、X64 和 ARM 平台上的 **_control87**函数几乎相同。 如果面向 x86、x64 或 ARM 平台，则可以使用 **_control87**或 **_controlfp_s**。

**_Control87**和 **_controlfp_s**之间的区别在于它们如何处理 denormal 值。 对于 Intel （x86）、x64 和 ARM 平台， **_control87**可以设置和清除 DENORMAL 操作数异常掩码。 **_controlfp_s**不会修改 DENORMAL 操作数异常掩码。 此示例演示了差别：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

以下十六进制值表中显示了掩码常量（*掩码*）和新控件值（*newControl*）的可能值。 使用下面列出的可移植常量（**_MCW_EM**、 **_EM_INVALID**等）作为这些函数的参数，而不是显式提供十六进制值。

Intel (x86) 派生的平台支持硬盘中的 DENORMAL 输入和输出值。 x86 行为是为了保留 DENORMAL 值。 支持 SSE2 的 ARM 平台和 x64 平台允许刷新 DENORMAL 操作数和结果，或将其强制为零。 **_Controlfp_s**、 **_controlfp**和 **_control87**函数提供了一个用于更改此行为的掩码。 下面的示例演示此掩码的使用：

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台上， **_controlfp_s**函数适用于 FPSCR 寄存器。 在 x64 体系结构上，只会影响存储在 MXCSR 寄存器中的 SSE2 控制字。 在 Intel （x86）平台上， **_controlfp_s**会影响 X87 和 SSE2 的控制字（如果存在）。 两个控制词可能相互不一致（例如，由于对[__control87_2](control87-controlfp-control87-2.md)的上一个调用）;如果两个控制字之间存在不一致， **_controlfp_s**将在*currentControl*中设置**EM_AMBIGUOUS**标志。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。

在 ARM 和 x64 体系结构上，不支持更改无穷大模式或浮点精度。 如果在 x64 平台上使用精度控制掩码，则函数将引发断言，并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

如果未正确设置掩码，则此函数生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回**EINVAL** ，并将**Errno**设置为**EINVAL**。

使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)编译时，将忽略此函数，因为公共语言运行时（clr）仅支持默认的浮点精度。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="mask-constants-and-values"></a>掩码常量和值

对于 **_MCW_EM**掩码，清除它将设置允许硬件例外的异常;设置将隐藏异常。 如果发生 **_EM_UNDERFLOW**或 **_EM_OVERFLOW** ，则在执行下一个浮点指令之前，不会引发硬件异常。 若要在 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**后立即生成硬件异常，请调用 FWAIT MASM 指令。

|Mask|十六进制值|返回的常量|十六进制值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （Denormal 控件）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （中断异常掩码）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （无限大控件）<br /><br /> （在 ARM 或 x64 平台上不受支持。）|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （舍入控制）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精度控制）<br /><br /> （在 ARM 或 x64 平台上不受支持。）|0x00030000|**_PC_24** （24位）<br /><br /> **_PC_53** （53位）<br /><br /> **_PC_64** （64位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
