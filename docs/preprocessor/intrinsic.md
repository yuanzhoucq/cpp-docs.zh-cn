---
title: intrinsic 杂注
ms.date: 08/29/2019
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: bb4403abf5e278ed3727af660579e22ab69592c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220939"
---
# <a name="intrinsic-pragma"></a>intrinsic 杂注

指定对杂注参数列表中指定的函数的调用是内部的。

## <a name="syntax"></a>语法

> **#pragma 内部 (** *function1* [ **,** _function2_ ...] **)**

## <a name="remarks"></a>备注

**内部**杂注告知编译器函数具有已知行为。 编译器可以调用函数，并且不将函数调用替换为内联说明（如果将实现更好的性能）。

下面列出了带内部形式的库函数。 出现**内部**杂注后, 它将在包含指定的内部函数的第一个函数定义处生效。 该效果将继续到源文件末尾或指定相同内部函数的`function`杂注的外观。 **内部**杂注只能在全局级别的函数定义之外使用。

以下函数具有内部形式, 当你指定[/Oi](../build/reference/oi-generate-intrinsic-functions.md)时, 将使用内部窗体:

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

使用内部函数的程序速度更快, 因为它们没有函数调用的开销, 但由于生成了附加代码, 可能会更大。

**x86 特定**

`_disable` 和`_enable`内部函数生成内核模式指令以禁用或启用中断, 在内核模式驱动程序中可能非常有用。

### <a name="example"></a>示例

从命令行`cl -c -FAs sample.c`编译以下代码, 并查看示例 .asm, 以查看它们是否转换为 x86 说明 CLI 和 STI:

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

**结束 x86 专用**

下面列出的浮点函数没有真正的内部形式。 相反，它们具有直接将自变量传递到浮点芯片而不是将其推送到程序堆栈上的版本：

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

当你指定[/Oi](../build/reference/oi-generate-intrinsic-functions.md)、 [/og](../build/reference/og-global-optimizations.md)和[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md) (或包含/Og: [/ox](../build/reference/ox-full-optimization.md)、 [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)和[/O2](../build/reference/o1-o2-minimize-size-maximize-speed.md)的任何选项) 时, 下面列出的浮点函数具有真正的内部形式:

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

可以使用[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)或[/za](../build/reference/za-ze-disable-language-extensions.md)来重写真正的内部浮点选项的生成。 在此情况下，函数将生成为库例程，后者将参数直接传递到浮点芯片，而不是将参数推送到程序堆栈。

有关详细信息, 请参阅[#pragma 函数](../preprocessor/function-c-cpp.md), 以及如何为源文本块启用/禁用内部函数的示例。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
