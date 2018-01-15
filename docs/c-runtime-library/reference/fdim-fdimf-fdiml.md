---
title: "fdim、fdimf、fdiml | Microsoft 文档"
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
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs: C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecf0b0590942aad133cb7b8f478200525e4f4519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fdim-fdimf-fdiml"></a>fdim、fdimf、fdiml
确定第一个值和第二个值之间的正数差。  
  
## <a name="syntax"></a>语法  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 第一个值。  
  
 [in] `y`  
 第二个值。  
  
## <a name="return-value"></a>返回值  
 返回 `x` 和 `y` 之间的正数差：  
  
|返回值|方案|  
|------------------|--------------|  
|x-y|如果 x > y|  
|0|如果 x <= y|  
  
 否则，可能返回以下错误之一：  
  
|问题|返回|  
|-----------|------------|  
|溢出范围错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|  
|下溢范围错误|正确值（舍入后）|  
|`x` 或 `y` 为 NaN|NaN|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中所指定的报告错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用 `fdim` 重载，以采用并返回浮点型和长双精度型值 。 在 C 程序中，`fdim` 始终采用及返回双精度型。  
  
 除 NaN 处理中，此函数相当于`fmax(x - y, 0)`。  
  
## <a name="requirements"></a>惠?  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax、fmaxf、fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs、labs、llabs、_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)