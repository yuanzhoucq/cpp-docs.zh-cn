---
title: "Concurrency::precise_math 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_math/Concurrency::precise_math"
dev_langs: 
  - "C++"
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::precise_math 命名空间
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`precise_math` 命名空间中的函数符合 C99。  包括了每个函数的单精度和双精度版本。  例如，`acos` 是双精度版本，`acosf` 是使用单精度版本。  包含单精度函数的这些函数要求在快捷键上有对扩展的双精度支持。  可以使用 [accelerator::supports\_double\_precision 数据成员](../Topic/accelerator::supports_double_precision%20Data%20Member.md) 确定是否可以在给定的快捷键使用这些函数。  
  
## 语法  
  
```vb  
namespace precise_math;  
```  
  
#### 参数  
  
## 成员  
  
### 函数  
  
|名称|说明|  
|--------|--------|  
|[acos 函数](../Topic/acos%20Function.md)|已重载。  计算参数的反余弦|  
|[acosf 函数](../Topic/acosf%20Function.md)|计算参数的反余弦|  
|[acosh 函数](../Topic/acosh%20Function.md)|已重载。  计算参数的反双曲余弦值|  
|[acoshf 函数](../Topic/acoshf%20Function.md)|计算参数的反双曲余弦值|  
|[asin 函数](../Topic/asin%20Function.md)|已重载。  计算参数的反正弦|  
|[asinf 函数](../Topic/asinf%20Function.md)|计算参数的反正弦|  
|[asinh 函数](../Topic/asinh%20Function.md)|已重载。  计算参数的反双曲正弦值|  
|[asinhf 函数](../Topic/asinhf%20Function.md)|计算参数的反双曲正弦值|  
|[atan 函数](../Topic/atan%20Function.md)|已重载。  计算参数的反正切|  
|[atan2 函数](../Topic/atan2%20Function.md)|已重载。  计算 \_Y\/\_X 的反正切|  
|[atan2f 函数](../Topic/atan2f%20Function.md)|计算 \_Y\/\_X 的反正切|  
|[atanf 函数](../Topic/atanf%20Function.md)|计算参数的反正切|  
|[atanh 函数](../Topic/atanh%20Function.md)|已重载。  计算参数的反双曲正切值|  
|[atanhf 函数](../Topic/atanhf%20Function.md)|计算参数的反双曲正切值|  
|[cbrt 函数](../Topic/cbrt%20Function.md)|已重载。  计算参数的实立方根|  
|[cbrtf 函数](../Topic/cbrtf%20Function.md)|计算参数的实立方根|  
|[ceil 函数](../Topic/ceil%20Function.md)|已重载。  计算参数的上限|  
|[ceilf 函数](../Topic/ceilf%20Function.md)|计算参数的上限|  
|[copysign 函数](../Topic/copysign%20Function.md)|已重载。  用\_X的大小和\_Y的符号来生成值|  
|[copysignf 函数](../Topic/copysignf%20Function.md)|用\_X的大小和\_Y的符号来生成值|  
|[cos 函数](../Topic/cos%20Function.md)|已重载。  计算参数的余弦|  
|[cosf 函数](../Topic/cosf%20Function.md)|计算参数的余弦|  
|[cosh 函数](../Topic/cosh%20Function.md)|已重载。  计算参数的双曲余弦值|  
|[coshf 函数](../Topic/coshf%20Function.md)|计算参数的双曲余弦值|  
|[cospi 函数](../Topic/cospi%20Function.md)|已重载。  计算余弦pi \* \_X的反余弦值|  
|[cospif 函数](../Topic/cospif%20Function.md)|计算余弦pi \* \_X的反余弦值|  
|[erf 函数](../Topic/erf%20Function.md)|已重载。  计算\_X的错误函数|  
|[erfc 函数](../Topic/erfc%20Function.md)|已重载。  计算\_X的互补错误函数|  
|[erfcf 函数](../Topic/erfcf%20Function.md)|计算\_X的互补错误函数|  
|[erfcinv 函数](../Topic/erfcinv%20Function.md)|已重载。  计算\_X 的反互补错误函数|  
|[erfcinvf 函数](../Topic/erfcinvf%20Function.md)|计算\_X 的反互补错误函数|  
|[erff 函数](../Topic/erff%20Function.md)|计算\_X的错误函数|  
|[erfinv 函数](../Topic/erfinv%20Function.md)|已重载。  计算\_X的反向错误函数|  
|[erfinvf 函数](../Topic/erfinvf%20Function.md)|计算\_X的反向错误函数|  
|[exp 函数](../Topic/exp%20Function.md)|已重载。  计算参数以 e 为底的指数|  
|[exp10 函数](../Topic/exp10%20Function.md)|已重载。  计算参数以 10 为底的指数|  
|[exp10f 函数](../Topic/exp10f%20Function.md)|计算参数以 10 为底的指数|  
|[exp2 函数](../Topic/exp2%20Function.md)|已重载。  计算参数以 2 为底的指数|  
|[exp2f 函数](../Topic/exp2f%20Function.md)|计算参数以 2 为底的指数|  
|[expf 函数](../Topic/expf%20Function.md)|计算参数以 e 为底的指数|  
|[expm1 函数](../Topic/expm1%20Function.md)|已重载。  计算参数的以 e 为底的指数，减去 1|  
|[expm1f 函数](../Topic/expm1f%20Function.md)|计算参数的以 e 为底的指数，减去 1|  
|[fabs 函数](../Topic/fabs%20Function.md)|已重载。  返回参数的绝对值|  
|[fabsf 函数](../Topic/fabsf%20Function.md)|返回参数的绝对值|  
|[fdim 函数](../Topic/fdim%20Function.md)|已重载。  决定参数之间的正整数差异。|  
|[fdimf 函数](../Topic/fdimf%20Function.md)|决定参数之间的正整数差异。|  
|[floor 函数](../Topic/floor%20Function.md)|已重载。  计算参数的下限|  
|[floorf 函数](../Topic/floorf%20Function.md)|计算参数的下限|  
|[fma 函数](../Topic/fma%20Function.md)|已重载。  计算\(\_X \* \_Y\) \+ \_Z，舍入为一个三元运算|  
|[fmaf 函数](../Topic/fmaf%20Function.md)|计算\(\_X \* \_Y\) \+ \_Z，舍入为一个三元运算|  
|[fmax 函数](../Topic/fmax%20Function.md)|已重载。  决定参数的最大数值|  
|[fmaxf 函数](../Topic/fmaxf%20Function.md)|决定参数的最大数值|  
|[fmin 函数](../Topic/fmin%20Function.md)|已重载。  决定参数的最小数值|  
|[fminf 函数](../Topic/fminf%20Function.md)|决定参数的最小数值|  
|[fmod 函数 \(C\+\+ AMP\)](../Topic/fmod%20Function%20\(C++%20AMP\).md)|已重载。  计算 \_X\/\_Y 的浮点余数|  
|[fmodf 函数](../Topic/fmodf%20Function.md)|计算 \_X\/\_Y 的浮点余数|  
|[fpclassify 函数](../Topic/fpclassify%20Function.md)|已重载。  分类为 NaN 的参数值，无穷大，常规，低质零，|  
|[frexp 函数](../Topic/frexp%20Function.md)|已重载。  获取 \_X 的尾数和指数|  
|[frexpf 函数](../Topic/frexpf%20Function.md)|获取 \_X 的尾数和指数|  
|[hypot 函数](../Topic/hypot%20Function.md)|已重载。  计算\_X 和\_Y 正方形的总和的平方根|  
|[hypotf 函数](../Topic/hypotf%20Function.md)|计算\_X 和\_Y 正方形的总和的平方根|  
|[ilogb 函数](../Topic/ilogb%20Function.md)|已重载。  提取\_X 指数为无符号整型值|  
|[ilogbf 函数](../Topic/ilogbf%20Function.md)|提取\_X 指数为无符号整型值|  
|[isfinite 函数](../Topic/isfinite%20Function.md)|已重载。  确定参数是否具有有限的值|  
|[isinf 函数](../Topic/isinf%20Function.md)|已重载。  确定参数是否是无穷|  
|[isnan 函数](../Topic/isnan%20Function.md)|已重载。  确定参数是否是 NaN|  
|[isnormal 函数](../Topic/isnormal%20Function.md)|已重载。  确定参数是否是规范|  
|[ldexp 函数](../Topic/ldexp%20Function.md)|已重载。  利用尾数和指数计算实数|  
|[ldexpf 函数](../Topic/ldexpf%20Function.md)|利用尾数和指数计算实数|  
|[lgamma 函数](../Topic/lgamma%20Function.md)|已重载。  计算伽玛参数绝对值的自然对数|  
|[lgammaf 函数](../Topic/lgammaf%20Function.md)|计算伽玛参数绝对值的自然对数|  
|[log 函数](../Topic/log%20Function.md)|已重载。  计算参数以 e 为底的对数|  
|[log10 函数](../Topic/log10%20Function.md)|已重载。  计算参数以 10 为底的对数|  
|[log10f 函数](../Topic/log10f%20Function.md)|计算参数以 10 为底的对数|  
|[log1p 函数](../Topic/log1p%20Function.md)|已重载。  计算1加参数以 e 为底的对数|  
|[log1pf 函数](../Topic/log1pf%20Function.md)|计算1加参数以 e 为底的对数|  
|[log2 函数](../Topic/log2%20Function.md)|已重载。  计算参数以 2 为底的对数|  
|[log2f 函数](../Topic/log2f%20Function.md)|计算参数以 2 为底的对数|  
|[logb 函数](../Topic/logb%20Function.md)|已重载。  用浮点格式提取\_X的指数作为有符号整数值|  
|[logbf 函数](../Topic/logbf%20Function.md)|用浮点格式提取\_X的指数作为有符号整数值|  
|[logf 函数](../Topic/logf%20Function.md)|计算参数以 e 为底的对数|  
|[modf 函数](../Topic/modf%20Function.md)|已重载。  将 \_X 拆分为小数部分和整数部分。|  
|[modff 函数](../Topic/modff%20Function.md)|将 \_X 拆分为小数部分和整数部分。|  
|[nan 函数](../Topic/nan%20Function.md)|返回一个清扫NaN|  
|[nanf 函数](../Topic/nanf%20Function.md)|返回一个清扫NaN|  
|[nearbyint 函数](../Topic/nearbyint%20Function.md)|已重载。  通过使用当前舍入方向，舍入参数为浮点格式的一个整数值，整数。|  
|[nearbyintf 函数](../Topic/nearbyintf%20Function.md)|通过使用当前舍入方向，舍入参数为浮点格式的一个整数值，整数。|  
|[nextafter 函数](../Topic/nextafter%20Function.md)|已重载。  确定下一个可表示的值，类型为函数，在 \_Y 方向中的 \_X 之后。|  
|[nextafterf 函数](../Topic/nextafterf%20Function.md)|确定下一个可表示的值，类型为函数，在 \_Y 方向中的 \_X 之后。|  
|[phi 函数](../Topic/phi%20Function.md)|已重载。  返回参数的累积分布函数|  
|[phif 函数](../Topic/phif%20Function.md)|返回参数的累积分布函数|  
|[pow 函数](../Topic/pow%20Function.md)|已重载。  计算 \_X 的 \_Y 次幂。|  
|[powf 函数](../Topic/powf%20Function.md)|计算 \_X 的 \_Y 次幂。|  
|[probit 函数](../Topic/probit%20Function.md)|已重载。  返回参数的反累积分布函数|  
|[probitf 函数](../Topic/probitf%20Function.md)|返回参数的反累积分布函数|  
|[rcbrt 函数](../Topic/rcbrt%20Function.md)|已重载。  返回参数立方根的倒数|  
|[rcbrtf 函数](../Topic/rcbrtf%20Function.md)|返回参数立方根的倒数|  
|[remainder 函数](../Topic/remainder%20Function.md)|已重载。  计算余数：\_X REM \_Y|  
|[remainderf 函数](../Topic/remainderf%20Function.md)|计算余数：\_X REM \_Y|  
|[remquo 函数](../Topic/remquo%20Function.md)|已重载。  计算和\_X REM \_Y相同的余数。  然后计算整数商\_X\/\_Y的低23 位，并指定该值的符号为\_X\/\_Y的符号。  在由\_Quo指向的整数中存储这个有符号值。|  
|[remquof 函数](../Topic/remquof%20Function.md)|计算和\_X REM \_Y相同的余数。  然后计算整数商\_X\/\_Y的低23 位，并指定该值的符号为\_X\/\_Y的符号。  在由\_Quo指向的整数中存储这个有符号值。|  
|[round 函数](../Topic/round%20Function.md)|已重载。  将 \_X 四舍五入为最接近的整数|  
|[roundf 函数](../Topic/roundf%20Function.md)|将 \_X 四舍五入为最接近的整数|  
|[rsqrt 函数](../Topic/rsqrt%20Function.md)|已重载。  返回参数平方根的倒数|  
|[rsqrtf 函数](../Topic/rsqrtf%20Function.md)|返回参数平方根的倒数|  
|[scalb 函数](../Topic/scalb%20Function.md)|已重载。  以 FLT\_RADIX乘以\_X到乘幂运算\_Y|  
|[scalbf 函数](../Topic/scalbf%20Function.md)|以 FLT\_RADIX乘以\_X到乘幂运算\_Y|  
|[scalbn 函数](../Topic/scalbn%20Function.md)|已重载。  以 FLT\_RADIX乘以\_X到乘幂运算\_Y|  
|[scalbnf 函数](../Topic/scalbnf%20Function.md)|以 FLT\_RADIX乘以\_X到乘幂运算\_Y|  
|[signbit 函数](../Topic/signbit%20Function.md)|已重载。  确定\_X 符号是否为负值|  
|[signbitf 函数](../Topic/signbitf%20Function.md)|确定\_X 符号是否为负值|  
|[sin 函数](../Topic/sin%20Function.md)|已重载。  计算参数的正弦值|  
|[sincos 函数](../Topic/sincos%20Function.md)|已重载。  计算 \_X 的正弦和余弦值|  
|[sincosf 函数](../Topic/sincosf%20Function.md)|计算 \_X 的正弦和余弦值|  
|[sinf 函数](../Topic/sinf%20Function.md)|计算参数的正弦值|  
|[sinh 函数](../Topic/sinh%20Function.md)|已重载。  计算参数的双曲正弦值|  
|[sinhf 函数](../Topic/sinhf%20Function.md)|计算参数的双曲正弦值|  
|[sinpi 函数](../Topic/sinpi%20Function.md)|已重载。  计算余弦pi \* \_X的正弦值|  
|[sinpif 函数](../Topic/sinpif%20Function.md)|计算余弦pi \* \_X的正弦值|  
|[sqrt 函数](../Topic/sqrt%20Function.md)|已重载。  计算参数的平方根。|  
|[sqrtf 函数](../Topic/sqrtf%20Function.md)|计算参数的平方根。|  
|[tan 函数](../Topic/tan%20Function.md)|已重载。  计算参数的正切值|  
|[tanf 函数](../Topic/tanf%20Function.md)|计算参数的正切值|  
|[tanh 函数](../Topic/tanh%20Function.md)|已重载。  计算参数的双曲正切值|  
|[tanhf 函数](../Topic/tanhf%20Function.md)|计算参数的双曲正切值|  
|[tanpi 函数](../Topic/tanpi%20Function.md)|已重载。  计算余弦pi \* \_X的正切值|  
|[tanpif 函数](../Topic/tanpif%20Function.md)|计算余弦pi \* \_X的正切值|  
|[tgamma 函数](../Topic/tgamma%20Function.md)|已重载。  计算\_X 的伽玛函数|  
|[tgammaf 函数](../Topic/tgammaf%20Function.md)|计算\_X 的伽玛函数|  
|[trunc 函数](../Topic/trunc%20Function.md)|已重载。  截断参数为整数部分|  
|[truncf 函数](../Topic/truncf%20Function.md)|截断参数为整数部分|  
  
## 要求  
 **头文件：**amp\_math.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)