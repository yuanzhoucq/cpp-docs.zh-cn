---
title: "lgamma、lgammaf、lgammal | Microsoft 文档"
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
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
dev_langs: C++
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afc048d131bd75a9645c045b3bceae90344c07eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma、lgammaf、lgammal
确定指定值的伽玛函数绝对值的自然对数。  
  
## <a name="syntax"></a>语法  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要计算的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `x.` 的伽玛函数绝对值的自然对数  
  
|问题|返回|  
|-----------|------------|  
|`x` = NaN|NaN|  
|`x` = ±0|+INFINITY|  
|`x`= 负整数|+INFINITY|  
|±INFINITY|+INFINITY|  
|极点错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|  
|溢出范围错误|±HUGE_VAL、±HUGE_VALF 或 ±HUGE_VALL|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中指定的内容报告错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用 `lgamma` 重载，以采用并返回浮点型和长双精度型值 。 在 C 程序中，`lgamma` 始终采用并返回双精度型值。  
  
 如果 x 是有理数，则此函数返回 (`x`-1) 的阶乘的对数。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`lgamma`,                `lgammaf`,  `lgammal`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma、tgammaf、tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)