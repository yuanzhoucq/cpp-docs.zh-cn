---
title: intrinsic 杂注
description: MSVC 内部杂注用于指定要用作内部函数的支持的内部函数。
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 31f4ebc2fdd4c5c984160d441b4e0a723c686a46
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180950"
---
# <a name="intrinsic-pragma"></a>`intrinsic` 杂注

指定对杂注参数列表中指定的函数的调用是内部的。

## <a name="syntax"></a>语法

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>备注

**`intrinsic`** 杂注告诉编译器函数具有已知行为。 编译器可以调用函数，并且不将函数调用替换为内联说明（如果将实现更好的性能）。

下面列出了带内部形式的库函数。 **`intrinsic`** 检测到杂注后，它会在包含指定内部函数的第一个函数定义处生效。 该效果将继续到源文件末尾或 `function` 指定相同内部函数的杂注的外观。 **`intrinsic`** 杂注只能在全局级别的函数定义之外使用。

以下函数具有内部形式，当你指定时，将使用内部形式的窗体 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) ：

|  |  |  |  |
|--|--|--|--|
| [`_disable`](../intrinsics/disable.md) | [`_outp`](../c-runtime-library/outp-outpw-outpd.md) | [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md) | [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) |
| [`_enable`](../intrinsics/enable.md) | [`_outpw`](../c-runtime-library/outp-outpw-outpd.md) | [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) |
| [`_inp`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md) | [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) |
| [`_inpw`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) |  |
| [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md) | [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) | [`memset`](../c-runtime-library/reference/memset-wmemset.md) |  |
| [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md) | [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md) |  |

使用内部函数的程序速度更快，因为它们没有函数调用的开销。 不过，由于生成了附加代码，这些代码可能会更大。

### <a name="x86-specific-example"></a>x86 特定示例

`_disable`和 `_enable` 内部函数生成内核模式指令以禁用或启用中断，在内核模式驱动程序中可能非常有用。

在命令行中编译以下代码 `cl -c -FAs sample.c` ，并查看 *`sample.asm`* 它们是否转换为 X86 说明 CLI 和 STI：

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

### <a name="intrinsic-floating-point-functions"></a>内部浮点函数

这些浮点函数没有真正的内部形式。 相反，它们具有直接将参数传递到浮点芯片的版本，而不是将其推送到堆栈上：

|  |  |  |  |
|--|--|--|--|
| [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md) | [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md) | [`pow`](../c-runtime-library/reference/pow-powf-powl.md) | [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md) |
| [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md) | [`fmod`](../c-runtime-library/reference/fmod-fmodf.md) | [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md) |  |

当你指定 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) 和 [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (或任何包含 **`/Oi`** ： [`/Ox`](../build/reference/ox-full-optimization.md) 、 [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) 和) 的选项时，这些浮点函数都具有真正的内部形式 [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ：

|  |  |  |  |
|--|--|--|--|
| [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`exp`](../c-runtime-library/reference/exp-expf.md) | [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md) |
| [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md) | [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md) |
| [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md) |  |  |  |

您可以使用 [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) 或 [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 重写真正的内部浮点选项的生成。 在此情况下，函数将生成为库例程，后者将参数直接传递到浮点芯片，而不是将参数推送到程序堆栈。

有关 [`#pragma function`](../preprocessor/function-c-cpp.md) 如何启用和禁用源文本块的内部函数的详细信息和示例，请参阅。

## <a name="see-also"></a>另请参阅

[Pragma 指令和 `__pragma` 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
