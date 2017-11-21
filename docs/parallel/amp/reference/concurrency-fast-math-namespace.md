---
title: "Concurrency:: fast_math Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: amp_math/Concurrency::fast_math
dev_langs: C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14bdfdf5ab570567f78befd3c99bca5c56c5195e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math 命名空间
函数中`fast_math`命名空间具有降低的准确性，支持仅的单精度 (`float`)，并调用 DirectX 内部函数。 有两个版本的每个函数，例如`cos`和`cosf`。 这两个版本采用并返回`float`，但每个调用相同的 DirectX 内部函数。  
  
## <a name="syntax"></a>语法  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>成员  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|计算参数的反余弦值|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的反余弦值|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|计算自变量的反正弦值|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|计算自变量的反正弦值|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|计算参数的反正切值|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|计算 _Y/_X 的反正切值|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|计算 _Y/_X 的反正切值|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|计算参数的反正切值|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|计算自变量的上限|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|计算自变量的上限|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|计算参数的余弦值|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的余弦值|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|计算自变量的双曲余弦值|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|计算自变量的双曲余弦值|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|计算的以 e 为底的自变量指数|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|计算基 2 的自变量的指数|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|计算基 2 的自变量的指数|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|计算的以 e 为底的自变量指数|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|返回自变量的绝对值|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|返回自变量的绝对值|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|计算自变量的下限|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|计算自变量的下限|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|确定自变量的最大数值|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|确定自变量的最大数值|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|确定自变量的最小数值|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|确定自变量的最小数值|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|计算 _X/_Y 的浮点余数|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|计算 _X/_Y 的浮点余数|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|获取的尾数和指数的 _X|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|获取的尾数和指数的 _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|确定参数是否具有有限值|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|确定参数是否为无穷大|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|确定参数是否为 NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|计算之间的尾数和指数的实数|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|计算之间的尾数和指数的实数|  
|[log](concurrency-fast-math-namespace-functions.md#log)|计算自变量的以 e 为底的对数|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|计算自变量的以 10 为基数的对数|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|计算自变量的以 10 为基数的对数|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|计算自变量的 2 为底对数|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|计算自变量的 2 为底对数|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|计算自变量的以 e 为底的对数|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|将拆分到小数部分组成的 _X 和整数部分。|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|将拆分到小数部分组成的 _X 和整数部分。|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|计算 _X 的 _Y 次幂|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|计算 _X 的 _Y 次幂|  
|[round](concurrency-fast-math-namespace-functions.md#round)|将舍入为最接近整数的 _X|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|将舍入为最接近整数的 _X|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|返回自变量的平方根的倒数|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|返回自变量的平方根的倒数|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|返回自变量的符号|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|返回自变量的符号|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|计算参数的正弦值|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|计算 _X 的正弦值和余弦值|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|计算 _X 的正弦值和余弦值|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|计算参数的正弦值|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|计算参数的双曲正弦值|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|计算参数的双曲正弦值|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|计算自变量的平方根|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|计算自变量的平方根|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|计算参数的正切值|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|计算参数的正切值|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|计算参数的双曲正切值|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|计算参数的双曲正切值|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|将截断的整数部分的自变量|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|将截断的整数部分的自变量|  

## <a name="requirements"></a>要求  
 **标头：** amp_math.h  
  
 **Namespace:** concurrency:: fast_math  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
