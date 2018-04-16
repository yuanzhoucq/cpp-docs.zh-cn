---
title: "fmin，fminf，fminl |Microsoft 文档"
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
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d90de1e734b2d2da4770c7a5ad85a5ee60a15408
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fmin-fminf-fminl"></a>fmin、fminf、fminl
确定两个指定值的较小值。  
  
## <a name="syntax"></a>语法  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要比较的第一个值。  
  
 `y`  
 要比较的第二个值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `x` 或 `y` 的较小值。  
  
|输入|结果|  
|-----------|------------|  
|`x` 为 NaN|`y`|  
|`y` 为 NaN|`x`|  
|`x` 和 `y` 为 NaN|NaN|  
  
 该函数不会导致 [_matherr](../../c-runtime-library/reference/matherr.md) 被调用，不会导致任何浮点异常，不会更改 `errno` 的值。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用 `fmin` 重载，以采用并返回浮点型和长双精度型值 。 在 C 程序中，`fmin` 始终采用及返回双精度型。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`fmin`, `fminf`, `fminl`|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)  
 [fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)  