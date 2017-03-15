---
title: "Concurrency:: fast_math Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 293452bf0a01f7f83a8a41bcb511bc57c9d45f26
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math 命名空间
中的函数`fast_math`命名空间包含支持唯一的单精度的降低准确性 (`float`)，并调用 DirectX 内部函数。 有两个版本的每个函数，例如`cos`和`cosf`。 这两个版本采用并返回`float`，但每个调用同一 DirectX 内部函数。  
  
## <a name="syntax"></a>语法  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>成员  
  
### <a name="functions"></a>函数  
  
|名称|说明|  
|----------|-----------------|  
|[cos 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#cos)|计算参数的反余弦值|  
|[cosf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的反余弦值|  
|[asin 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#asin)|计算参数的反正弦值|  
|[asinf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#asinf)|计算参数的反正弦值|  
|[atan 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#atan)|计算参数的反正切值|  
|[atan2 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#atan2)|计算 _Y/_X 的反正切值|  
|[atan2f 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#atan2f)|计算 _Y/_X 的反正切值|  
|[atanf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#atanf)|计算参数的反正切值|  
|[ceil 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#ceil)|计算参数的上限|  
|[ceilf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#ceilf)|计算参数的上限|  
|[cos 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#cos)|计算参数的余弦值|  
|[cosf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的余弦值|  
|[cosh 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#cosh)|计算参数的双曲余弦值|  
|[coshf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#coshf)|计算参数的双曲余弦值|  
|[exp 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#exp)|计算以 e 为底的参数的指数|  
|[exp2 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#exp2)|计算&2; 为底的参数的指数|  
|[exp2f 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#exp2f)|计算&2; 为底的参数的指数|  
|[expf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#expf)|计算以 e 为底的参数的指数|  
|[fabs 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fabs)|返回参数的绝对值|  
|[fabsf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fabsf)|返回参数的绝对值|  
|[floor 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#floor)|计算参数的下限|  
|[floorf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#floorf)|计算参数的下限|  
|[fmax 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fmax)|确定参数的最大数值|  
|[fmaxf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fmaxf)|确定参数的最大数值|  
|[fmin 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fmin)|确定参数的最小数值|  
|[fminf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fminf)|确定参数的最小数值|  
|[fmod 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fmod)|计算 _X/_Y 的浮点余数|  
|[fmodf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#fmodf)|计算 _X/_Y 的浮点余数|  
|[frexp 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#frexp)|获取的尾数和 _X 的指数|  
|[frexpf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#frexpf)|获取的尾数和 _X 的指数|  
|[isfinite 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#isfinite)|确定参数是否具有有限值|  
|[isinf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#isinf)|确定参数是否为无穷大|  
|[isnan 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#isnan)|确定参数是否为 NaN|  
|[ldexp 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#ldexp)|将实数从尾数和指数计算|  
|[ldexpf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#ldexpf)|将实数从尾数和指数计算|  
|[log 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#log)|计算参数的以 e 为底对数|  
|[log10 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#log10)|计算参数的以&10; 为基数的对数|  
|[log10f 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#log10f)|计算参数的以&10; 为基数的对数|  
|[log2 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#log2)|计算参数的&2; 为底对数|  
|[log2f 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#log2f)|计算参数的&2; 为底对数|  
|[logf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#logf)|计算参数的以 e 为底对数|  
|[modf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#modf)|将拆分到小数的 _X 和整数部分。|  
|[modff 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#modff)|将拆分到小数的 _X 和整数部分。|  
|[pow 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#pow)|计算 _X 的 _Y 次幂|  
|[powf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#powf)|计算 _X 的 _Y 次幂|  
|[round 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#round)|将舍入为最接近整数的 _X|  
|[roundf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#roundf)|将舍入为最接近整数的 _X|  
|[rsqrt 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#rsqrt)|返回参数的平方根的倒数|  
|[rsqrtf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#rsqrtf)|返回参数的平方根的倒数|  
|[signbit 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#signbit)|返回参数的符号|  
|[signbitf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#signbitf)|返回参数的符号|  
|[sin 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sin)|计算参数的正弦值|  
|[sincos 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sincos)|计算 _X 的正弦和余弦值|  
|[sincosf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sincosf)|计算 _X 的正弦和余弦值|  
|[sinf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sinf)|计算参数的正弦值|  
|[sinh 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sinh)|计算参数的双曲正弦值|  
|[sinhf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sinhf)|计算参数的双曲正弦值|  
|[sqrt 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sqrt)|计算参数的平方根|  
|[sqrtf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#sqrtf)|计算参数的平方根|  
|[tan 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#tan)|计算参数的正切值|  
|[tanf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#tanf)|计算参数的正切值|  
|[tanh 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#tanh)|计算参数的双曲正切值|  
|[tanhf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#tanhf)|计算参数的双曲正切值|  
|[trunc 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#trunc)|将截断的整数部分的参数|  
|[truncf 函数 (fast_math)](concurrency-fast-math-namespace-functions.md#truncf)|将截断的整数部分的参数|  

## <a name="requirements"></a>要求  
 **标头︰** amp_math.h  
  
 **Namespace:** concurrency:: fast_math  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

