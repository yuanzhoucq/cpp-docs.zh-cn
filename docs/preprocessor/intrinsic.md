---
title: 内部函数 |Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 496971736e1f303d61b83e15b2ba1c03083f8d53
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422787"
---
# <a name="intrinsic"></a>intrinsic

指定对杂注自变量列表中指定的函数的调用是内部的。

## <a name="syntax"></a>语法

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>备注

**内部函数**杂注告知编译器某个函数已了解行为。  编译器可以调用函数，并且不将函数调用替换为内联说明（如果将实现更好的性能）。

下面列出了带内部形式的库函数。 一次**内部函数**杂注，它将包含指定的内部函数的第一个函数定义处生效。 该效果持续到源文件的末尾或外观的`function`杂注指定相同内部函数。 **内部函数**杂注可以使用仅在函数定义之外，在全局级别。

以下函数具有内部形式和指定时，会使用内部函数的窗体[/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

使用内部函数的程序的运行速度比较快，因为它们没有函数调用的开销，但是，由于生成了附加代码，它们可能比较大。

**x86 特定**

`_disable`和`_enable`内部函数生成内核模式说明以禁用/启用中断，可以是内核模式驱动程序中很有用。

### <a name="example"></a>示例

从命令行中使用以下代码编译`cl -c -FAs sample.c`并查看 sample.asm 以了解它们是否为 x86 说明 CLI 和 STI:

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

下面列出的浮点函数不具有真正的内部形式。 相反，它们具有直接将自变量传递到浮点芯片而不是将其推送到程序堆栈上的版本：

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

 下面列出的浮点函数没有真正的内部形式指定时[/Oi](../build/reference/oi-generate-intrinsic-functions.md)， [/Og](../build/reference/og-global-optimizations.md)，并[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md) (或任何包含 /Og 的选项： [/Ox](../build/reference/ox-full-optimization.md)， [/o1](../build/reference/o1-o2-minimize-size-maximize-speed.md)，和/o2):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

可以使用[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)或[/Za](../build/reference/za-ze-disable-language-extensions.md)重写的则返回 true 的内部浮点选项的生成。 在此情况下，函数将生成为库例程，后者将自变量直接传递到浮点芯片，而不是将自变量推送到程序堆栈。

请参阅[#pragma 函数](../preprocessor/function-c-cpp.md)有关信息和有关如何启用/禁用的源文本块的内部函数的示例。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)  