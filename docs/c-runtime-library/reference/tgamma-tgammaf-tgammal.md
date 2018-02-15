---
title: "tgamma、tgammaf、tgammal | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs:
- C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7525da71d114179d40b937816f9ebe08d5a892a9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal
确定指定值的 gamma 函数。  
  
## <a name="syntax"></a>语法  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要查找其伽玛值的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `x` 的伽玛值。  
  
 如果 `x` 的度量值对于数据类型而言过大或过小，则出现范围错误。 如果 `x`  <=0，则出现域错误或范围错误。  
  
|问题|返回|  
|-----------|------------|  
|x = ±0|±INFINITY|  
|x = 负整数|NaN|  
|x =  -INFINITY|NaN|  
|x = +INFINITY|+INFINITY|  
|x = NaN|NaN|  
|域错误|NaN|  
|极点错误|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|  
|溢出范围错误|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|  
|下溢范围错误|舍入后的正确值。|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中所指定的报告错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用采用并返回浮点型和长双精度型 tgamma 的重载。 在 C 程序中，tgamma 始终采用和返回双精度型值。  
  
 如果 x 是自然数，则此函数返回 (x-1) 的阶乘。  
  
## <a name="requirements"></a>惠?  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`tgamma`,                `tgammaf`,  `tgammal`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma、lgammaf、lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)