---
title: "log1p、log1pf、log1pl2 | Microsoft 文档"
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
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f32799e2eabc54dacdc5144c59483b7a6a641110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="log1p-log1pf-log1pl"></a>log1p、log1pf、log1pl
计算 1 加上指定值的自然对数。  
  
## <a name="syntax"></a>语法  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 浮点型参数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 (`x`+1) 的自然（以 e 为底）对数。  
  
 否则，可能返回以下值之一：  
  
|输入|结果|SEH 异常|errno|  
|-----------|------------|-------------------|-----------|  
|+inf|+inf|||  
|非规格化数|与输入相同|UNDERFLOW||  
|±0|与输入相同|||  
|-1|-inf|DIVBYZERO|ERANGE|  
|< -1|nan|INVALID|EDOM|  
|-inf|nan|INVALID|EDOM|  
|±SNaN|与输入相同|INVALID||  
|±QNaN，无限期|与输入相同|||  
  
 如果 `x` = -1，则将 `errno` 值设置为 ERANGE。 `errno`如果值设置为 EDOM `x` <-1。  
  
## <a name="remarks"></a>备注  
 x 接近 0 时 `log1p` 函数比使用 log(`x`+1) 更准确。  
  
 由于 C++ 支持重载，可以调用采用并返回浮点型和长双精度型的 `log1p` 的重载。 在 C 程序中，`log1p` 始终采用及返回双精度型。  
  
 如果 `x` 是自然数，则此函数返回 (`x`-1) 的阶乘的对数。  
  
## <a name="requirements"></a>惠?  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`log1p`,                `log1pf`,  `log1pl`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2、log2f、log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)