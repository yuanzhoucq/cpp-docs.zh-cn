---
title: _clear87、_clearfp
ms.date: 04/05/2018
apiname:
- _clearfp
- _clear87
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
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4148f85d82a4210033686455c73046081832e3c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340541"
---
# <a name="clear87-clearfp"></a>_clear87、_clearfp

获取并清除浮点状态字。

## <a name="syntax"></a>语法

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>返回值

返回的值中的位表示调用之前的浮点状态 **_clear87**或 **_clearfp**。 有关通过返回的位的完整定义 **_clear87**，请参阅 Float.h。 许多数学库函数修改了 8087/80287 状态字，结果不可预知。 返回值从 **_clear87**并 **_status87**就会越浮点状态字的已知状态之间执行较少浮点运算越可靠。

## <a name="remarks"></a>备注

**_Clear87**函数清除浮点状态字中的异常标记，将繁忙位设置为 0，并返回状态字。 浮点状态字是 8087/80287 状态字和通过 8087/80287 异常处理程序检测到的其他条件（如浮点堆栈上溢和下溢）组合而成。

**_clearfp**是一个独立于平台的、 可移植的版本 **_clear87**例程。 它等同于 **_clear87** Intel (x86) 平台上和也受 x64 和 ARM 平台。 若要确保你的浮点代码可移植到 x64 和 ARM，使用 **_clearfp**。 如果你只面向 x86 平台，你可以使用 **_clear87**或 **_clearfp**。

使用编译时，这些函数已弃用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时仅支持默认浮点精度。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
