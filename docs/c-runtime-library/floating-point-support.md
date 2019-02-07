---
title: 数学和浮点支持
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: 1d03333dee12989af5897c34ba96484930a39673
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703124"
---
# <a name="math-and-floating-point-support"></a>数学和浮点支持

通用 C 运行时库 (UCRT) 提供了许多整型和浮点数学库函数，包括 ISO C99 所需的所有函数。 这些浮点函数的实现是为了平衡性能与正确性。 因为产生正确舍入的结果可能成本过高，这些函数旨在有效地生成接近正确舍入结果的近似结果。 在大多数情况下，虽然可能存在误差较大的情况，但生成的结果在正确舍入结果的 + /-1 ulp 范围内。

许多浮点数学库函数具有不同 CPU 体系结构的不同实现。 例如，相比 64 位 x64 CRT，32 位 x86 CRT 可能具有不同的实现。 此外，某些函数可能有适用于给定 CPU 体系结构的多个实现。 在运行时动态地选择最有效的实现，具体取决于受 CPU 支持的指令集。 例如，在 32 位 x86 CRT 中，一些函数同时具有 x87 实现和 SSE2 实现。 在支持 SSE2 的 CPU 上运行时，使用速度更快的 SSE2 实现。 在不支持 SSE2 的 CPU 上运行时，使用速度较慢的 x87 实现。 数学库函数的不同实现可能会使用不同的 CPU 指令和不同的算法来生成其结果，因此，这些函数可能会在各 CPU 中产生不同的结果。 在大多数情况下，结果在正确舍入结果的 +/-1 ulp 范围内，但实际结果在各 CPU 中可能会有所不同。

以前的 16 位版本 Microsoft C/C ++ 和 Microsoft Visual C++ 支持长双精度类型作为 80 位精度浮点数据类型。 在更高版本的 Visual C++ 中，长双精度数据类型是与双精度类型相同的 64 位精度浮点数据类型。 编译器将长双精度数据类型和双精度数据类型视为不同类型，但长双精度函数与双精度函数相同。 CRT 为 ISO C99 源代码兼容性提供了数学函数的长双精度版本，但请注意，二进制表示形式可能不同于其他编译器。

## <a name="supported-math-and-floating-point-routines"></a>受支持的数学和浮点例程

|例程所返回的值|使用|
|-|-|
[abs、labs、llabs、_abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|计算整数类型的绝对值
[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|计算反余弦值
[acosh、acoshf、acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|计算双曲反余弦值
[asin、asinf、asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|计算反正弦值
[asinh、asinhf、asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|计算双曲反正弦值
[atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|计算反正切值
[atanh、atanhf、atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|计算双曲反正切值
[_atodbl、_atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|将特定于区域设置的字符串转换为双精度型
[atof、_atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符串转换为双精度型
[_atoflt、_atoflt_l、_atoldbl、_atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|将特定于区域设置的字符串转换为浮点型或长双精度型
[cbrt、cbrtf、cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|计算立方根
[ceil、ceilf、ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|计算上限
[_chgsign、_chgsignf、_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|计算相反数
[_clear87、_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|获取并清除浮点状态注册
[_control87、\__control87_2、_controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|获取并设置浮点控制字
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|_controlfp 的安全版本
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|返回一个值，该值具有一个自变量的数值和另一个自变量的符号
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|计算正弦值
[cosh、coshf、coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|计算双曲正弦值
[div、ldiv、lldiv](../c-runtime-library/reference/div.md)|计算两个整数值的商和余数
[_ecvt](../c-runtime-library/reference/ecvt.md)、[ecvt](../c-runtime-library/reference/posix-ecvt.md)|将双精度型转换为字符串
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|_ecvt 的安全版本
[erf、erff、erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|计算错误函数
[erfc、erfcf、erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|计算互补错误函数
[exp、expf、expl](../c-runtime-library/reference/exp-expf.md)|计算指数 e<sup>x</sup>
[exp2、exp2f、exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|计算指数 2<sup>x</sup>
[expm1、expm1f、expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|计算 e<sup>x</sup>-1
[fabs、fabsf、fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|计算浮点类型的绝对值
[_fcvt](../c-runtime-library/reference/fcvt.md)、[fcvt](../c-runtime-library/reference/posix-fcvt.md)|将浮点数转换为字符串
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|_fcvt 的安全版本
[fdim、fdimf、fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|确定两个值之间的正数差
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|清除指定的浮点异常
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|存储当前的浮点环境
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|获取指定的浮点异常状态
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|获取浮点舍入模式
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|设置不间断的浮点异常模式
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|引发指定的浮点异常
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|设置当前的浮点环境
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|获取指定的浮点异常状态标志
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|设置指定的浮点舍入标志
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|确定要设置的浮点异常状态标志
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|还原浮点环境，然后引发以前的异常
[floor、floorf、floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|计算下限
[fma、fmaf、fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|计算浮点混合乘加运算
[fmax、fmaxf、fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|计算参数的最大值
[fmin、fminf、fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|计算参数的最小值
[fmod、fmodf、fmodl](../c-runtime-library/reference/fmod-fmodf.md)|计算浮点余数
[_fpclass、_fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|返回浮点值的分类
[fpclassify](../c-runtime-library/reference/fpclassify.md)|返回浮点值的分类
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|设置浮点异常的处理程序
[_fpreset](../c-runtime-library/reference/fpreset.md)|重置浮点环境
[frexp、frexpf、frexpl](../c-runtime-library/reference/frexp.md)|获取浮点数的尾数和指数
[_gcvt](../c-runtime-library/reference/gcvt.md)、[gcvt](../c-runtime-library/reference/posix-gcvt.md)|将浮点数转换为字符串
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|_gcvt 的安全版本
[_get_FMA3_enable、_set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|获取或设置用于 x64 上 FMA3 指令的标志
[hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|计算斜边
[ilogb、ilogbf、ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|计算以整数 2 为底的指数
[imaxabs](../c-runtime-library/reference/imaxabs.md)|计算整数类型的绝对值
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|计算两个整数值的商和余数
[isfinite、_finite、_finitef](../c-runtime-library/reference/finite-finitef.md)|确定某值是否有限
[isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered](../c-runtime-library/reference/floating-point-ordering.md)|比较两个浮点值的顺序
[isinf](../c-runtime-library/reference/isinf.md)|确定浮点值是否为无穷大
[isnan、_isnan、_isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|测试 NaN 的浮点值
[isnormal](../c-runtime-library/reference/isnormal.md)|测试浮点值是否既有限又不低于正常值
[_j0、_j1、_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|计算贝塞尔函数
[ldexp、ldexpf、ldexpl](../c-runtime-library/reference/ldexp.md)|计算 x*2<sup>n</sup>
[lgamma、lgammaf、lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|计算 gamma 函数的绝对值的自然对数
[llrint、llrintf、llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|将浮点值舍入为最接近的超长值
[llround、llroundf、llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|将浮点值舍入为最接近的超长值
[log、logf、logl、log10、log10f、log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|计算自然对数或以 10 为底的对数
[log1p、log1pf、log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|计算 1+x 的自然对数
[log2、log2f、log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|计算以 2 为底的对数
[logb、logbf、logbl、_logb、_logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|返回浮点值的指数
[lrint、lrintf、lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|将浮点值舍入为最接近的长值
[_lrotl、_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|向左或向右旋转整数值
[lround、lroundf、lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|将浮点值舍入为最接近的长值
[_matherr](../c-runtime-library/reference/matherr.md)|默认数学错误处理程序
[__max](../c-runtime-library/reference/max.md)|返回两个值中的较大者的宏
[__min](../c-runtime-library/reference/min.md)|返回两个值中的较小者的宏
[modf、modff、modfl](../c-runtime-library/reference/modf-modff-modfl.md)|将浮点值拆分为小数部分和整数部分
[nan、nanf、nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|返回 quiet NaN 值
[nearbyint、nearbyintf、nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|返回舍入后的值
[nextafter、nextafterf、nextafterl、_nextafter、_nextafterf](../c-runtime-library/reference/nextafter-functions.md)|返回下一个可表示的浮点值
[nexttoward、nexttowardf、nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|返回下一个可表示的浮点值
[pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)|返回 x<sup>y</sup> 的值
[remainder、remainderf、remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|计算两个浮点值的商的余数
[remquo、remquof、remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|计算两个整数值的余数
[rint、rintf、rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|舍入浮点值
[_rotl、_rotl64、_rotr、_rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|旋转整数类型中的位
[round、roundf、roundl](../c-runtime-library/reference/round-roundf-roundl.md)|舍入浮点值
[_scalb、_scalbf](../c-runtime-library/reference/scalb.md)|按 2 的幂缩放参数
[scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|将浮点数乘以 FLT_RADIX 的整数幂
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|设置浮点控制字
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|启用或禁用 SSE2 指令
[signbit](../c-runtime-library/reference/signbit.md)|测试浮点值的符号位
[sin、sinf、sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|计算正弦值
[sinh、sinhf、sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|计算双曲正弦值
[sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|计算平方根
[_status87、_statusfp、_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|获取浮点状态字
[strtof、_strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|将字符串转换为浮点型
[strtold、_strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|将字符串转换为长双精度型
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|计算正切值
[tanh、tanhf、tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|计算双曲正切值
[tgamma、tgammaf、tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|计算 gamma 函数
[trunc、truncf、truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|截断小数部分
[_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将宽字符串转换为双精度型
[_y0、_y1、_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|计算贝塞尔函数

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[浮点基元](../c-runtime-library/reference/floating-point-primitives.md)<br/>
