---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958096"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

获取浮点状态字。

## <a name="syntax"></a>语法

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>参数

*px86*<br/>
此地址用 x87 浮点单元的状态字填充。

*pSSE2*<br/>
此地址用 SSE2 浮点单元的状态字填充。

## <a name="return-value"></a>返回值

对于 **_status87**和 **_statusfp**，返回值中的位表示浮点状态。 请参阅 FLOAT。H 包含 **_statusfp**返回的位的定义的文件。 许多数学库函数修改了浮点状态字，结果不可预知。 优化可以对 **_status87**、 **_statusfp**和相关函数的调用进行排序、合并和消除浮点运算。 使用 [/Od（禁用（调试））](../../build/reference/od-disable-debug.md)编译器选项或 [fenv_access](../../preprocessor/fenv-access.md) pragma 指令，可防止对浮点操作重新排序的优化。 如果在浮点状态字的已知状态之间执行的浮点运算更少，则从 **_clearfp**和 **_statusfp**返回值以及 **_statusfp2**的返回参数将更可靠。

## <a name="remarks"></a>备注

**_Statusfp**函数获取浮点状态字。 状态字是浮点异常处理程序检测出的浮点处理程序状态和其他条件的组合（例如，浮点堆栈溢出和下溢）。 在返回状态字的内容之前检查未屏蔽的异常。 这表示通知调用方挂起异常。 在 x86 平台上， **_statusfp**返回 X87 和 SSE2 浮点状态的组合。 在 x64 平台上，返回的状态基于 SSE 的 MXCSR 状态。 在 ARM 平台上， **_statusfp**从 FPSCR 寄存器返回状态。

**_statusfp**是独立于平台的、可移植版本的 **_status87**。 它与 Intel （x86）平台上的 **_status87**完全相同，并且也受 X64 和 ARM 平台的支持。 若要确保你的浮点代码可移植到所有体系结构，请使用 **_statusfp**。 如果仅面向 x86 平台，可以使用 **_status87**或 **_statusfp**。

建议将 **_statusfp2**用于具有 X87 和 SSE2 浮点处理器的芯片（如 Pentium IV）。 对于 **_statusfp2**，将使用 X87 或 SSE2 浮点处理器的浮点状态字来填充地址。 对于支持 x87 和 SSE2 浮点处理器的芯片，如果使用 **_statusfp**或 **_CONTROLFP** ，则 EM_AMBIGUOUS 设置为1，并且操作是不明确的，因为它可以引用 x87 或 SSE2 浮点状态字。 **_Statusfp2**函数仅在 x86 平台上受支持。

这些函数对于[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)不起作用，因为公共语言运行时（clr）仅支持默认的浮点精度。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_status87**、 **_statusfp**、 **_statusfp2**|\<float.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
