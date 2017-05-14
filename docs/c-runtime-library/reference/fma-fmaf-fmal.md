---
title: "fma、fmaf、fmal | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fma
- fmaf
- fmal
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 59238cf511be936b0d882c2f00320ee7422904e0
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal
两个值相乘，添加第三个值，然后将结果舍入，由于中间舍入不会丢失任何精度。  
  
## <a name="syntax"></a>语法  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要相乘的第一个值。  
  
 [in] `y`  
 要相乘的第二个值。  
  
 [in] `z`  
 要相加的值。  
  
## <a name="return-value"></a>返回值  
 返回 `(x * y) + z`。 然后使用当前舍入格式舍入返回值。  
  
 否则，可能返回以下值之一：  
  
|问题|返回|  
|-----------|------------|  
|`x` = INFINITY、`y` = 0 或<br /><br /> `x` = -0、`y` = INFINITY|NaN|  
|`x` 或 `y` = 确切 ± INFINITY、`z` = 带相反符号的 INFINITY|NaN|  
|`x` 或 `y` = NaN|NaN|  
|非（`x` = 0，`y`= 不定值）和 `z` = NaN<br /><br /> 非（`x`= 不定值，`y`= 0）和 `z` = NaN|NaN|  
|溢出范围错误|±HUGE_VAL、±HUGE_VALF 或 ±HUGE_VALL|  
|下溢范围错误|舍入后的正确值。|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中所指定的报告错误。  
  
## <a name="remarks"></a>备注  
 由于 c + + 允许重载，你可以调用的重载`fma`采用并返回**float**和**长双精度**类型。 在 C 程序中，`fma`始终采用并返回**double**。  
  
 此函数计算值就好像它采取了无限精度，然后将最终结果舍入。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fma`, `fmaf`, `fmal`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [remainder、remainderf、remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)
