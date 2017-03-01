---
title: "Concurrency:: precise_math Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::precise_math
dev_langs:
- C++
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b64bd3e3702701ae2685d6688d88988dd91dc5d0
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace"></a>Concurrency::precise_math 命名空间
中的函数`precise_math`命名空间是符合 C99。 包括单精度和双精度版本的每个函数。 例如，`acos`是双精度版本和`acosf`是单精度版本。 这些函数，其中包括单精度函数中，需要在快捷键上的长的双精度支持。 您可以使用[accelerator:: supports_double_precision 数据成员](accelerator-class.md#supports_double_precision)，确定是否可以在特定快捷键上运行这些函数。 

  
## <a name="syntax"></a>语法  
  
```cpp  
namespace precise_math;  
```  
  
#### <a name="parameters"></a>参数  
  
## <a name="members"></a>成员  
  
### <a name="functions"></a>函数  
  
|名称|说明|  
|----------|-----------------|  
|[acos 函数](concurrency-precise-math-namespace-functions.md#acos)|已重载。 计算参数的反余弦值|  
|[acosf 函数](concurrency-precise-math-namespace-functions.md#acosf)|计算参数的反余弦值|  
|[acosh 函数](concurrency-precise-math-namespace-functions.md#acosh)|已重载。 计算自变量的反双曲余弦值|  
|[acoshf 函数](concurrency-precise-math-namespace-functions.md#acoshf)|计算自变量的反双曲余弦值|  
|[asin 函数](concurrency-precise-math-namespace-functions.md#asin)|已重载。 计算参数的反正弦值|  
|[asinf 函数](concurrency-precise-math-namespace-functions.md#asinf)|计算参数的反正弦值|  
|[asinh 函数](concurrency-precise-math-namespace-functions.md#asinh)|已重载。 计算自变量的反双曲正弦值|  
|[asinhf 函数](concurrency-precise-math-namespace-functions.md#asinhf)|计算自变量的反双曲正弦值|  
|[atan 函数](concurrency-precise-math-namespace-functions.md#atan)|已重载。 计算参数的反正切值|  
|[atan2 函数](concurrency-precise-math-namespace-functions.md#atan2)|已重载。 计算 _Y/_X 的反正切值|  
|[atan2f 函数](concurrency-precise-math-namespace-functions.md#atan2f)|计算 _Y/_X 的反正切值|  
|[atanf 函数](concurrency-precise-math-namespace-functions.md#atanf)|计算参数的反正切值|  
|[atanh 函数](concurrency-precise-math-namespace-functions.md#atanh)|已重载。 计算自变量的反双曲正切值|  
|[atanhf 函数](concurrency-precise-math-namespace-functions.md#atanhf)|计算自变量的反双曲正切值|  
|[cbrt 函数](concurrency-precise-math-namespace-functions.md#cbrt)|已重载。 计算自变量的实立方根|  
|[cbrtf 函数](concurrency-precise-math-namespace-functions.md#cbrtf)|计算自变量的实立方根|  
|[ceil 函数](concurrency-precise-math-namespace-functions.md#ceil)|已重载。 计算参数的上限|  
|[ceilf 函数](concurrency-precise-math-namespace-functions.md#ceilf)|计算参数的上限|  
|[copysign 函数](concurrency-precise-math-namespace-functions.md#copysign)|已重载。 用 _X 的大小和 _Y 的符号生成一个值|  
|[copysignf 函数](concurrency-precise-math-namespace-functions.md#copysignf)|用 _X 的大小和 _Y 的符号生成一个值|  
|[cos 函数](concurrency-precise-math-namespace-functions.md#cos)|已重载。 计算参数的余弦值|  
|[cosf 函数](concurrency-precise-math-namespace-functions.md#cosf)|计算参数的余弦值|  
|[cosh 函数](concurrency-precise-math-namespace-functions.md#cosh)|已重载。 计算参数的双曲余弦值|  
|[coshf 函数](concurrency-precise-math-namespace-functions.md#coshf)|计算参数的双曲余弦值|  
|[cospi 函数](concurrency-precise-math-namespace-functions.md#cospi)|已重载。 计算 pi * _X 的余弦值|  
|[cospif 函数](concurrency-precise-math-namespace-functions.md#cospif)|计算 pi * _X 的余弦值|  
|[erf 函数](concurrency-precise-math-namespace-functions.md#erf)|已重载。 计算 _X 的错误函数|  
|[erfc 函数](concurrency-precise-math-namespace-functions.md#erfc)|已重载。 计算 _X 的互补错误函数|  
|[erfcf 函数](concurrency-precise-math-namespace-functions.md#erfcf)|计算 _X 的互补错误函数|  
|[erfcinv 函数](concurrency-precise-math-namespace-functions.md#erfcinv)|已重载。 计算 _X 的反互补错误函数|  
|[erfcinvf 函数](concurrency-precise-math-namespace-functions.md#erfcinvf)|计算 _X 的反互补错误函数|  
|[erff 函数](concurrency-precise-math-namespace-functions.md#erff)|计算 _X 的错误函数|  
|[erfinv 函数](concurrency-precise-math-namespace-functions.md#erfinv)|已重载。 计算 _X 的反向错误函数|  
|[erfinvf 函数](concurrency-precise-math-namespace-functions.md#erfinvf)|计算 _X 的反向错误函数|  
|[exp 函数](concurrency-precise-math-namespace-functions.md#exp)|已重载。 计算以 e 为底的参数的指数|  
|[exp10 函数](concurrency-precise-math-namespace-functions.md#exp10)|已重载。 计算的以&10; 为基数的参数的指数|  
|[exp10f 函数](concurrency-precise-math-namespace-functions.md#exp10f)|计算的以&10; 为基数的参数的指数|  
|[exp2 函数](concurrency-precise-math-namespace-functions.md#exp2)|已重载。 计算&2; 为底的参数的指数|  
|[exp2f 函数](concurrency-precise-math-namespace-functions.md#exp2f)|计算&2; 为底的参数的指数|  
|[expf 函数](concurrency-precise-math-namespace-functions.md#expf)|计算以 e 为底的参数的指数|  
|[expm1 函数](concurrency-precise-math-namespace-functions.md#expm1)|已重载。 计算自变量的以 e 为底的指数，减去 1|  
|[expm1f 函数](concurrency-precise-math-namespace-functions.md#expm1f)|计算自变量的以 e 为底的指数，减去 1|  
|[fabs 函数](concurrency-precise-math-namespace-functions.md#fabs)|已重载。 返回参数的绝对值|  
|[fabsf 函数](concurrency-precise-math-namespace-functions.md#fabsf)|返回参数的绝对值|  
|[fdim 函数](concurrency-precise-math-namespace-functions.md#fdim)|已重载。 确定参数之间的正数差异|  
|[fdimf 函数](concurrency-precise-math-namespace-functions.md#fdimf)|确定参数之间的正数差异|  
|[floor 函数](concurrency-precise-math-namespace-functions.md#floor)|已重载。 计算参数的下限|  
|[floorf 函数](concurrency-precise-math-namespace-functions.md#floorf)|计算参数的下限|  
|[fma 函数](concurrency-precise-math-namespace-functions.md#fma)|已重载。 计算 (_X * _Y) + _Z，舍入为一次三元操作|  
|[fmaf 函数](concurrency-precise-math-namespace-functions.md#fmaf)|计算 (_X * _Y) + _Z，舍入为一次三元操作|  
|[fmax 函数](concurrency-precise-math-namespace-functions.md#fmax)|已重载。 确定参数的最大数值|  
|[fmaxf 函数](concurrency-precise-math-namespace-functions.md#fmaxf)|确定参数的最大数值|  
|[fmin 函数](concurrency-precise-math-namespace-functions.md#fmin)|已重载。 确定参数的最小数值|  
|[fminf 函数](concurrency-precise-math-namespace-functions.md#fminf)|确定参数的最小数值|  
|[fmod 函数 (c + + AMP)](concurrency-precise-math-namespace-functions.md#fmod)|已重载。 计算 _X/_Y 的浮点余数|  
|[fmodf 函数](concurrency-precise-math-namespace-functions.md#fmodf)|计算 _X/_Y 的浮点余数|  
|[fpclassify 函数](concurrency-precise-math-namespace-functions.md#fpclassify)|已重载。 将自变量值分类为 NaN、无穷大、正常、次正常、零|  
|[frexp 函数](concurrency-precise-math-namespace-functions.md#frexp)|已重载。 获取的尾数和 _X 的指数|  
|[frexpf 函数](concurrency-precise-math-namespace-functions.md#frexpf)|获取的尾数和 _X 的指数|  
|[hypot 函数](concurrency-precise-math-namespace-functions.md#hypot)|已重载。 计算 _X 和 _Y 平方和的平方根|  
|[hypotf 函数](concurrency-precise-math-namespace-functions.md#hypotf)|计算 _X 和 _Y 平方和的平方根|  
|[ilogb 函数](concurrency-precise-math-namespace-functions.md#ilogb)|已重载。 以有符号整数值形式提取 _X 的指数|  
|[ilogbf 函数](concurrency-precise-math-namespace-functions.md#ilogbf)|以有符号整数值形式提取 _X 的指数|  
|[isfinite 函数](concurrency-precise-math-namespace-functions.md#isfinite)|已重载。 确定参数是否具有有限值|  
|[isinf 函数](concurrency-precise-math-namespace-functions.md#isinf)|已重载。 确定参数是否为无穷大|  
|[isnan 函数](concurrency-precise-math-namespace-functions.md#isnan)|已重载。 确定参数是否为 NaN|  
|[isnormal 函数](concurrency-precise-math-namespace-functions.md#isnormal)|已重载。 确定自变量是否规范|  
|[ldexp 函数](concurrency-precise-math-namespace-functions.md#ldexp)|已重载。 将实数从尾数和指数计算|  
|[ldexpf 函数](concurrency-precise-math-namespace-functions.md#ldexpf)|将实数从尾数和指数计算|  
|[lgamma 函数](concurrency-precise-math-namespace-functions.md#lgamma)|已重载。 计算自变量伽玛绝对值的自然对数|  
|[lgammaf 函数](concurrency-precise-math-namespace-functions.md#lgammaf)|计算自变量伽玛绝对值的自然对数|  
|[log 函数](concurrency-precise-math-namespace-functions.md#log)|已重载。 计算参数的以 e 为底对数|  
|[log10 函数](concurrency-precise-math-namespace-functions.md#log10)|已重载。 计算参数的以&10; 为基数的对数|  
|[log10f 函数](concurrency-precise-math-namespace-functions.md#log10f)|计算参数的以&10; 为基数的对数|  
|[log1p 函数](concurrency-precise-math-namespace-functions.md#log1p)|已重载。 计算 1 加自变量的以 e 为底的对数|  
|[log1pf 函数](concurrency-precise-math-namespace-functions.md#log1pf)|计算 1 加自变量的以 e 为底的对数|  
|[log2 函数](concurrency-precise-math-namespace-functions.md#log2)|已重载。 计算参数的&2; 为底对数|  
|[log2f 函数](concurrency-precise-math-namespace-functions.md#log2f)|计算参数的&2; 为底对数|  
|[logb 函数](concurrency-precise-math-namespace-functions.md#logb)|已重载。 以浮点格式的有符号整数值形式提取 _X 的指数|  
|[logbf 函数](concurrency-precise-math-namespace-functions.md#logbf)|以浮点格式的有符号整数值形式提取 _X 的指数|  
|[logf 函数](concurrency-precise-math-namespace-functions.md#logf)|计算参数的以 e 为底对数|  
|[modf 函数](concurrency-precise-math-namespace-functions.md#modf)|已重载。 将拆分到小数的 _X 和整数部分。|  
|[modff 函数](concurrency-precise-math-namespace-functions.md#modff)|将拆分到小数的 _X 和整数部分。|  
|[nan 函数](concurrency-precise-math-namespace-functions.md#nan)|返回一个静态 NaN|  
|[nanf 函数](concurrency-precise-math-namespace-functions.md#nanf)|返回一个静态 NaN|  
|[nearbyint 函数](concurrency-precise-math-namespace-functions.md#nearbyint)|已重载。 通过使用当前舍入方向，将自变量舍入为浮点格式的整数值。|  
|[nearbyintf 函数](concurrency-precise-math-namespace-functions.md#nearbyintf)|通过使用当前舍入方向，将自变量舍入为浮点格式的整数值。|  
|[nextafter 函数](concurrency-precise-math-namespace-functions.md#nextafter)|已重载。 确定该函数的类型中的下一步可表示值之后 _Y 方向的 _X|  
|[nextafterf 函数](concurrency-precise-math-namespace-functions.md#nextafterf)|确定该函数的类型中的下一步可表示值之后 _Y 方向的 _X|  
|[phi 函数](concurrency-precise-math-namespace-functions.md#phi)|已重载。 返回参数的累积分布函数|  
|[phif 函数](concurrency-precise-math-namespace-functions.md#phif)|返回参数的累积分布函数|  
|[pow 函数](concurrency-precise-math-namespace-functions.md#pow)|已重载。 计算 _X 的 _Y 次幂|  
|[powf 函数](concurrency-precise-math-namespace-functions.md#powf)|计算 _X 的 _Y 次幂|  
|[probit 函数](concurrency-precise-math-namespace-functions.md#probit)|已重载。 返回参数的反转累积分布函数|  
|[probitf 函数](concurrency-precise-math-namespace-functions.md#probitf)|返回参数的反转累积分布函数|  
|[rcbrt 函数](concurrency-precise-math-namespace-functions.md#rcbrt)|已重载。 返回参数的立方根的倒数|  
|[rcbrtf 函数](concurrency-precise-math-namespace-functions.md#rcbrtf)|返回参数的立方根的倒数|  
|[remainder 函数](concurrency-precise-math-namespace-functions.md#remainder)|已重载。 计算余数：_X REM _Y|  
|[remainderf 函数](concurrency-precise-math-namespace-functions.md#remainderf)|计算余数：_X REM _Y|  
|[remquo 函数](concurrency-precise-math-namespace-functions.md#remquo)|已重载。 计算 _X REM _Y 作为相同的余数。 此外计算较低的 23 位整数的商 _X/_y，并提供该值作为 _X/_Y 的符号相同。 它将此符号的值存储在 _Quo 所指向的整数。|  
|[remquof 函数](concurrency-precise-math-namespace-functions.md#remquof)|计算 _X REM _Y 作为相同的余数。 此外计算较低的 23 位整数的商 _X/_y，并提供该值作为 _X/_Y 的符号相同。 它将此符号的值存储在 _Quo 所指向的整数。|  
|[round 函数](concurrency-precise-math-namespace-functions.md#round)|已重载。 将舍入为最接近整数的 _X|  
|[roundf 函数](concurrency-precise-math-namespace-functions.md#roundf)|将舍入为最接近整数的 _X|  
|[rsqrt 函数](concurrency-precise-math-namespace-functions.md#rsqrt)|已重载。 返回参数的平方根的倒数|  
|[rsqrtf 函数](concurrency-precise-math-namespace-functions.md#rsqrtf)|返回参数的平方根的倒数|  
|[scalb 函数](concurrency-precise-math-namespace-functions.md#scalb)|已重载。 用 _X 乘以 FLT_RADIX 的 _Y 次方|  
|[scalbf 函数](concurrency-precise-math-namespace-functions.md#scalbf)|用 _X 乘以 FLT_RADIX 的 _Y 次方|  
|[scalbn 函数](concurrency-precise-math-namespace-functions.md#scalbn)|已重载。 用 _X 乘以 FLT_RADIX 的 _Y 次方|  
|[scalbnf 函数](concurrency-precise-math-namespace-functions.md#scalbnf)|用 _X 乘以 FLT_RADIX 的 _Y 次方|  
|[signbit 函数](concurrency-precise-math-namespace-functions.md#signbit)|已重载。 确定 _X 的符号是否为负号|  
|[signbitf 函数](concurrency-precise-math-namespace-functions.md#signbitf)|确定 _X 的符号是否为负号|  
|[sin 函数](concurrency-precise-math-namespace-functions.md#sin)|已重载。 计算参数的正弦值|  
|[sincos 函数](concurrency-precise-math-namespace-functions.md#sincos)|已重载。 计算 _X 的正弦和余弦值|  
|[sincosf 函数](concurrency-precise-math-namespace-functions.md#sincosf)|计算 _X 的正弦和余弦值|  
|[sinf 函数](concurrency-precise-math-namespace-functions.md#sinf)|计算参数的正弦值|  
|[sinh 函数](concurrency-precise-math-namespace-functions.md#sinh)|已重载。 计算参数的双曲正弦值|  
|[sinhf 函数](concurrency-precise-math-namespace-functions.md#sinhf)|计算参数的双曲正弦值|  
|[sinpi 函数](concurrency-precise-math-namespace-functions.md#sinpi)|已重载。 计算 pi * _X 的正弦值|  
|[sinpif 函数](concurrency-precise-math-namespace-functions.md#sinpif)|计算 pi * _X 的正弦值|  
|[sqrt 函数](concurrency-precise-math-namespace-functions.md#sqrt)|已重载。 计算自变量的平方根|  
|[sqrtf 函数](concurrency-precise-math-namespace-functions.md#sqrtf)|计算自变量的平方根|  
|[tan 函数](concurrency-precise-math-namespace-functions.md#tan)|已重载。 计算参数的正切值|  
|[tanf 函数](concurrency-precise-math-namespace-functions.md#tanf)|计算参数的正切值|  
|[tanh 函数](concurrency-precise-math-namespace-functions.md#tanh)|已重载。 计算参数的双曲正切值|  
|[tanhf 函数](concurrency-precise-math-namespace-functions.md#tanhf)|计算参数的双曲正切值|  
|[tanpi 函数](concurrency-precise-math-namespace-functions.md#tanpi)|已重载。 计算 pi * _X 的正切值|  
|[tanpif 函数](concurrency-precise-math-namespace-functions.md#tanpif)|计算 pi * _X 的正切值|  
|[tgamma 函数](concurrency-precise-math-namespace-functions.md#tgamma)|已重载。 计算 _X 的伽玛函数|  
|[tgammaf 函数](concurrency-precise-math-namespace-functions.md#tgammaf)|计算 _X 的伽玛函数|  
|[trunc 函数](concurrency-precise-math-namespace-functions.md#trunc)|已重载。 将截断的整数部分的参数|  
|[truncf 函数](concurrency-precise-math-namespace-functions.md#truncf)|将截断的整数部分的参数|  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_math.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

