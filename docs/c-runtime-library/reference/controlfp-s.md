---
title: _controlfp_s | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _controlfp_s
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
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 443b9ee53606bc3075e62e98012edfca79747cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="controlfps"></a>_controlfp_s

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

如果成功，或者将为零**errno**值错误代码。

## <a name="remarks"></a>备注

**_Controlfp_s**函数是独立于平台的更安全版本， **_control87**，后者将获取存储在地址到浮点控制字*currentControl*并将其设置通过使用*newControl*。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式，具体取决于平台。 你还可以使用 **_controlfp_s**屏蔽或取消屏蔽浮点异常。

如果值*掩码*等于 0， **_controlfp_s**获取浮点控制字并将存储中检索到的值*currentControl*。

如果*掩码*是新的控制字值设置为零，： 设置任何位 （即，等于 1） 在*掩码*中的对应位*新*用于更新控件word。 换而言之， *fpcntrl* = ((*fpcntrl* & ~*掩码*) &#124; (*newControl* & *掩码*)) 其中*fpcntrl*是浮点控制字。 在此方案中， *currentControl*设置为值后更改完成; 它不是旧的控制字位值。

> [!NOTE]
> 默认情况下，运行时库屏蔽所有浮点异常。

**_controlfp_s**几乎等同于 **_control87** (x86)、 x64 和 ARM 平台上 Intel 函数。 如果你正面向 x86、 x64 或 ARM 平台上，则可以使用 **_control87**或 **_controlfp_s**。

之间的差异 **_control87**和 **_controlfp_s**是在它们如何处理非常规值。 X64 和 ARM 平台上，intel (x86)， **_control87**可以设置和清除非常规操作数异常掩码。 **_controlfp_s**不会修改非常规操作数异常掩码。 此示例演示了差别：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

掩码常量的可能值 (*掩码*) 和控件的新值 (*newControl*) 下的十六进制值表中显示。 使用下面列出的可移植常量 (**_MCW_EM**， **_EM_INVALID**，依次类推) 作为对这些函数的自变量，而不是提供十六进制值显式。

Intel (x86) 派生的平台支持硬盘中的 DENORMAL 输入和输出值。 x86 行为是为了保留 DENORMAL 值。 ARM 平台和 x64 平台具有 SSE2 支持启用 DENORMAL 操作数和结果，以刷新，或强制为零。 **_Controlfp_s**， **_controlfp**，和 **_control87**函数提供的掩码要更改此行为。 下面的示例演示此掩码的使用：

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台上， **_controlfp_s**函数将应用于 FPSCR 寄存器。 在 x64 体系结构中，仅存储 SSE2 控制字 MXCSR 注册受到影响。 在 Intel (x86) 平台 **_controlfp_s**影响 x87 和 SSE2 的控制字，如果存在。 可能的两个控件单词不相互一致 (因以前调用而[__control87_2](control87-controlfp-control87-2.md)，例如); 如果存在两个控件单词，之间不一致 **_controlfp_s**设置**EM_AMBIGUOUS**中标记出来*currentControl*。 这是一条警告，指示所返回的控制字可能没有准确地表示两个浮点控制字的状态。

在 ARM 和 x64 体系结构，更改无穷大模式或的浮点精度不支持。 如果在 x64 上使用的精度控制掩码平台，该函数引发了断言并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

如果未正确设置掩码，则此函数生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回**EINVAL**和设置**errno**到**EINVAL**。

当你使用此函数将忽略[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)来编译，因为公共语言运行时 (CLR) 仅支持默认的浮点精度。

### <a name="mask-constants-and-values"></a>掩码常量和值

有关 **_MCW_EM**掩码，清除此复选框设置允许的硬件异常的异常; 将其设置隐藏异常。 如果 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**发生，直到执行下一步的浮点指令不引发任何硬件异常。 生成硬件异常后立即 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**，调用 FWAIT MASM 指令。

|掩码|十六进制值|返回的常量|十六进制值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （不正常控制）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （中断异常掩码）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （无穷大控件）<br /><br /> （不支持在 ARM 或 x64 平台。）|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （舍入控件）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精度控制）<br /><br /> （不支持在 ARM 或 x64 平台。）|0x00030000|**_PC_24** （24 位）<br /><br /> **_PC_53** （53 位）<br /><br /> **_PC_64** （64 位）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
