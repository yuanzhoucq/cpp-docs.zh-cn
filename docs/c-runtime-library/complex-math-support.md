---
title: C 复数数学支持
ms.date: 05/14/2019
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: dac032940ed9d96764b64809c5f8901ac273898b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215174"
---
# <a name="c-complex-math-support"></a>C 复数数学支持

Microsoft C 运行时库 (CRT) 提供了复数数学库函数，包括 ISO C99 所需的所有函数。 编译器不直接支持 **`complex`** 或 **`_Complex`** 关键字，因此 Microsoft 实现使用结构类型来表示复数。

这些函数的实现是为了平衡性能与正确性。 因为产生正确舍入的结果可能成本过高，这些函数旨在有效地生成接近正确舍入结果的近似结果。 在大多数情况下，虽然可能存在误差较大的情况，但生成的结果在正确舍入结果的 + /-1 ulp 范围内。

复数数学例程依赖于浮点数学库函数进行实现。 这些函数具有不同 CPU 体系结构的不同实现。 例如，相比 64 位 x64 CRT，32 位 x86 CRT 可能具有不同的实现。 此外，某些函数可能有适用于给定 CPU 体系结构的多个实现。 在运行时动态地选择最有效的实现，具体取决于受 CPU 支持的指令集。 例如，在 32 位 x86 CRT 中，一些函数同时具有 x87 实现和 SSE2 实现。 在支持 SSE2 的 CPU 上运行时，使用速度更快的 SSE2 实现。 在不支持 SSE2 的 CPU 上运行时，使用速度较慢的 x87 实现。 数学库函数的不同实现可能会使用不同的 CPU 指令和不同的算法来生成其结果，因此，这些函数可能会在各 CPU 中产生不同的结果。 在大多数情况下，结果在正确舍入结果的 +/-1 ulp 范围内，但实际结果在各 CPU 中可能会有所不同。

## <a name="types-used-in-complex-math"></a>复数数学中使用的类型

complex.h 标头的 Microsoft 实现将这些类型定义为 C99 标准本机复数类型的等效项：

|标准类型|Microsoft 类型|
|-|-|
|**`float complex`** 或 **`float _Complex`**|**_Fcomplex**|
|**`double complex`** 或 **`double _Complex`**|**_Dcomplex**|
|**`long double complex`** 或 **`long double _Complex`**|**_Lcomplex**|

math.h 标头定义了单独类型 struct _complex****，用于 [_cabs](../c-runtime-library/reference/cabs.md) 函数。 struct _complex**** 类型没有用于等效复数数学函数 [cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)。

## <a name="complex-constants-and-macros"></a>复数常数和宏

**I**定义为 **_Fcomplex**初始化的复杂类型 `{ 0.0f, 1.0f }` 。

## <a name="trigonometric-functions"></a>三角函数

|函数|描述|
|-|-|
|[cacos、cacosf、cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|计算复数的复数反余弦值|
|[casin、casinf、casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|计算复数的复数反正弦值|
|[catan、catanf、catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|计算复数的复数反正切值|
|[ccos、ccosf、ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|计算复数的复数余弦值|
|[csin、csinf、csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|计算复数的复数正弦值|
|[ctan、ctanf、ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|计算复数的复数正切值|

## <a name="hyperbolic-functions"></a>双曲函数

|函数|描述|
|-|-|
|[cacosh、cacoshf、cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|计算复数的复数反双曲余弦值|
|[casinh、casinhf、casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|计算复数的复数反双曲正弦值|
|[catanh、catanhf、catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|计算复数的复数反双曲正切值|
|[ccosh、ccoshf、ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|计算复数的复数双曲余弦值|
|[csinh、csinhf、csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|计算复数的复数双曲正弦值|
|[ctanh、ctanhf、ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|计算复数的复数双曲正切值|

## <a name="exponential-and-logarithmic-functions"></a>指数和对数函数

|函数|描述|
|-|-|
|[cexp、cexpf、cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|计算复数的以 e 为底的复数指数**|
|[clog、clogf、clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|计算复数的（以 e 为底的）复数自然对数**|
|[clog10、clog10f、clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|计算复数的以 10 为底的复数对数|

## <a name="power-and-absolute-value-functions"></a>幂和绝对值函数

|函数|描述|
|-|-|
|[cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|计算复数的复数绝对值（也称为范数、模数或量值）|
|[cpow、cpowf、cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|计算复数幂函数 x<sup>y</sup>|
|[csqrt、csqrtf、csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|计算复数的复数平方根|

## <a name="manipulation-functions"></a>操作函数

|函数|描述|
|-|-|
|[_Cbuild、_FCbuild、_LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|从实部和虚部构造复数|
|[carg、cargf、cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|计算复数的自变量（也称为相角）|
|[cimag、cimagf、cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|检索复数的虚部|
|[conj、conjf、conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|计算复数的复数共轭|
|[cproj、cprojf、cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|计算 Riemann 球体上某个复数的投影|
|[creal、crealf、creall](../c-runtime-library/reference/creal-crealf-creall.md)|计算复数的实部|
|[norm、normf、norml1](../c-runtime-library/reference/norm-normf-norml1.md)|计算复数的平方量值|

## <a name="operation-functions"></a>运算函数

由于复数不是 Microsoft 编译器中的本机类型，复数类型上未定义标准的算术运算符。 为方便起见，这些复数数学库函数用于实现用户代码中的复数的有限处理：

|函数|描述|
|-|-|
|[_Cmulcc、_FCmulcc、_LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|将两个复数相乘|
|[_Cmulcr、_FCmulcr、_LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|将复数和浮点数相乘|

## <a name="see-also"></a>另请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
