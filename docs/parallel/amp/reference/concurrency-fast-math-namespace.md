---
title: "Concurrency::fast_math 命名空间 | Microsoft Docs"
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
  - "amp_math/Concurrency::fast_math"
dev_langs: 
  - "C++"
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::fast_math 命名空间
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`fast_math` 命名空间的函数具有较低的精确度，仅支持单精度 \(`float`\)，以及调用 DirectX 内部函数。  每个功能有两个版本，例如 `cos` 和 `cosf`。  两个版本采用并返回 `float`，但每个调用相同的 DirectX 内部函数。  
  
## 语法  
  
```  
namespace fast_math;  
```  
  
## 成员  
  
### 函数  
  
|名称|描述|  
|--------|--------|  
|[cos 函数 \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|计算参数的反余弦|  
|[cosf 函数 \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|计算参数的反余弦|  
|[asin 函数 \(fast\_math\)](../Topic/asin%20Function%20\(fast_math\).md)|计算参数的反正弦|  
|[asinf 函数 \(fast\_math\)](../Topic/asinf%20Function%20\(fast_math\).md)|计算参数的反正弦|  
|[atan 函数 \(fast\_math\)](../Topic/atan%20Function%20\(fast_math\).md)|计算参数的反正切|  
|[atan2 函数 \(fast\_math\)](../Topic/atan2%20Function%20\(fast_math\).md)|计算 \_Y\/\_X 的反正切|  
|[atan2f 函数 \(fast\_math\)](../Topic/atan2f%20Function%20\(fast_math\).md)|计算 \_Y\/\_X 的反正切|  
|[atanf 函数 \(fast\_math\)](../Topic/atanf%20Function%20\(fast_math\).md)|计算参数的反正切|  
|[ceil 函数 \(fast\_math\)](../Topic/ceil%20Function%20\(fast_math\).md)|计算参数的上限|  
|[ceilf 函数 \(fast\_math\)](../Topic/ceilf%20Function%20\(fast_math\).md)|计算参数的上限|  
|[cos 函数 \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|计算参数的余弦|  
|[cosf 函数 \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|计算参数的余弦|  
|[cosh 函数 \(fast\_math\)](../Topic/cosh%20Function%20\(fast_math\).md)|计算参数的双曲余弦值|  
|[coshf 函数 \(fast\_math\)](../Topic/coshf%20Function%20\(fast_math\).md)|计算参数的双曲余弦值|  
|[exp 函数 \(fast\_math\)](../Topic/exp%20Function%20\(fast_math\).md)|计算参数以 e 为底的指数|  
|[exp2 函数 \(fast\_math\)](../Topic/exp2%20Function%20\(fast_math\).md)|计算参数以 2 为底的指数|  
|[exp2f 函数 \(fast\_math\)](../Topic/exp2f%20Function%20\(fast_math\).md)|计算参数以 2 为底的指数|  
|[expf 函数 \(fast\_math\)](../Topic/expf%20Function%20\(fast_math\).md)|计算参数以 e 为底的指数|  
|[fabs 函数 \(fast\_math\)](../Topic/fabs%20Function%20\(fast_math\).md)|返回参数的绝对值|  
|[fabsf 函数 \(fast\_math\)](../Topic/fabsf%20Function%20\(fast_math\).md)|返回参数的绝对值|  
|[floor 函数 \(fast\_math\)](../Topic/floor%20Function%20\(fast_math\).md)|计算参数的下限|  
|[floorf 函数 \(fast\_math\)](../Topic/floorf%20Function%20\(fast_math\).md)|计算参数的下限|  
|[fmax 函数 \(fast\_math\)](../Topic/fmax%20Function%20\(fast_math\).md)|决定参数的最大数值|  
|[fmaxf 函数 \(fast\_math\)](../Topic/fmaxf%20Function%20\(fast_math\).md)|决定参数的最大数值|  
|[fmin 函数 \(fast\_math\)](../Topic/fmin%20Function%20\(fast_math\).md)|决定参数的最小数值|  
|[fminf 函数 \(fast\_math\)](../Topic/fminf%20Function%20\(fast_math\).md)|决定参数的最小数值|  
|[fmod 函数 \(fast\_math\)](../Topic/fmod%20Function%20\(fast_math\).md)|计算 \_X\/\_Y 的浮点余数|  
|[fmodf 函数 \(fast\_math\)](../Topic/fmodf%20Function%20\(fast_math\).md)|计算 \_X\/\_Y 的浮点余数|  
|[frexp 函数 \(fast\_math\)](../Topic/frexp%20Function%20\(fast_math\).md)|获取 \_X 的尾数和指数|  
|[frexpf 函数 \(fast\_math\)](../Topic/frexpf%20Function%20\(fast_math\).md)|获取 \_X 的尾数和指数|  
|[isfinite 函数 \(fast\_math\)](../Topic/isfinite%20Function%20\(fast_math\).md)|确定参数是否具有有限的值|  
|[isinf 函数 \(fast\_math\)](../Topic/isinf%20Function%20\(fast_math\).md)|确定参数是否是无穷|  
|[isnan 函数 \(fast\_math\)](../Topic/isnan%20Function%20\(fast_math\).md)|确定参数是否是 NaN|  
|[ldexp 函数 \(fast\_math\)](../Topic/ldexp%20Function%20\(fast_math\).md)|利用尾数和指数计算实数|  
|[ldexpf 函数 \(fast\_math\)](../Topic/ldexpf%20Function%20\(fast_math\).md)|利用尾数和指数计算实数|  
|[log 函数 \(fast\_math\)](../Topic/log%20Function%20\(fast_math\).md)|计算参数以 e 为底的对数|  
|[log10 函数 \(fast\_math\)](../Topic/log10%20Function%20\(fast_math\).md)|计算参数以 10 为底的对数|  
|[log10f 函数 \(fast\_math\)](../Topic/log10f%20Function%20\(fast_math\).md)|计算参数以 10 为底的对数|  
|[log2 函数 \(fast\_math\)](../Topic/log2%20Function%20\(fast_math\).md)|计算参数以 2 为底的对数|  
|[log2f 函数 \(fast\_math\)](../Topic/log2f%20Function%20\(fast_math\).md)|计算参数以 2 为底的对数|  
|[logf 函数 \(fast\_math\)](../Topic/logf%20Function%20\(fast_math\).md)|计算参数以 e 为底的对数|  
|[modf 函数 \(fast\_math\)](../Topic/modf%20Function%20\(fast_math\).md)|将 \_X 拆分为小数部分和整数部分。|  
|[modff 函数 \(fast\_math\)](../Topic/modff%20Function%20\(fast_math\).md)|将 \_X 拆分为小数部分和整数部分。|  
|[pow 函数 \(fast\_math\)](../Topic/pow%20Function%20\(fast_math\).md)|计算 \_X 的 \_Y 次幂。|  
|[powf 函数 \(fast\_math\)](../Topic/powf%20Function%20\(fast_math\).md)|计算 \_X 的 \_Y 次幂。|  
|[round 函数 \(fast\_math\)](../Topic/round%20Function%20\(fast_math\).md)|将 \_X 四舍五入为最接近的整数|  
|[roundf 函数 \(fast\_math\)](../Topic/roundf%20Function%20\(fast_math\).md)|将 \_X 四舍五入为最接近的整数|  
|[rsqrt 函数 \(fast\_math\)](../Topic/rsqrt%20Function%20\(fast_math\).md)|返回参数平方根的倒数|  
|[rsqrtf 函数 \(fast\_math\)](../Topic/rsqrtf%20Function%20\(fast_math\).md)|返回参数平方根的倒数|  
|[signbit 函数 \(fast\_math\)](../Topic/signbit%20Function%20\(fast_math\).md)|返回参数的符号。|  
|[signbitf 函数 \(fast\_math\)](../Topic/signbitf%20Function%20\(fast_math\).md)|返回参数的符号。|  
|[sin 函数 \(fast\_math\)](../Topic/sin%20Function%20\(fast_math\).md)|计算参数的正弦值|  
|[sincos 函数 \(fast\_math\)](../Topic/sincos%20Function%20\(fast_math\).md)|计算 \_X 的正弦和余弦值|  
|[sincosf 函数 \(fast\_math\)](../Topic/sincosf%20Function%20\(fast_math\).md)|计算 \_X 的正弦和余弦值|  
|[sinf 函数 \(fast\_math\)](../Topic/sinf%20Function%20\(fast_math\).md)|计算参数的正弦值|  
|[sinh 函数 \(fast\_math\)](../Topic/sinh%20Function%20\(fast_math\).md)|计算参数的双曲正弦值|  
|[sinhf 函数 \(fast\_math\)](../Topic/sinhf%20Function%20\(fast_math\).md)|计算参数的双曲正弦值|  
|[sqrt 函数 \(fast\_math\)](../Topic/sqrt%20Function%20\(fast_math\).md)|计算参数的平方根。|  
|[sqrtf 函数 \(fast\_math\)](../Topic/sqrtf%20Function%20\(fast_math\).md)|计算参数的平方根。|  
|[tan 函数 \(fast\_math\)](../Topic/tan%20Function%20\(fast_math\).md)|计算参数的正切值|  
|[tanf 函数 \(fast\_math\)](../Topic/tanf%20Function%20\(fast_math\).md)|计算参数的正切值|  
|[tanh 函数 \(fast\_math\)](../Topic/tanh%20Function%20\(fast_math\).md)|计算参数的双曲正切值|  
|[tanhf 函数 \(fast\_math\)](../Topic/tanhf%20Function%20\(fast_math\).md)|计算参数的双曲正切值|  
|[trunc 函数 \(fast\_math\)](../Topic/trunc%20Function%20\(fast_math\).md)|截断参数为整数部分|  
|[truncf 函数 \(fast\_math\)](../Topic/truncf%20Function%20\(fast_math\).md)|截断参数为整数部分|  
  
## 要求  
 **头文件：**amp\_math.h  
  
 **命名空间：**Concurrency::fast\_math  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)