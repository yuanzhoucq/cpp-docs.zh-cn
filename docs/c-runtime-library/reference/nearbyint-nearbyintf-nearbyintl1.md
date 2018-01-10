---
title: "nearbyint、nearbyintf、nearbyintl1 | Microsoft 文档"
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
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs: C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95f92d15dcf4b8baf84b762b994bdb52930346d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl
将指定的浮点值舍入为整数，并以浮点格式返回该值。  
  
## <a name="syntax"></a>语法  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要舍入的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `x`，舍入到最接近的整数，使用由 fegetround 定义的当前舍入格式。 否则，该函数返回以下值之一：  
  
|问题|返回|  
|-----------|------------|  
|`x`= ±INFINITY|±INFINITY 修改|  
|`x` = ±0|±0 修改|  
|`x` = NaN|NaN|  
  
 错误不通过 [_matherr](../../c-runtime-library/reference/matherr.md) 报告；具体来说，此函数不报告任何 FE_INEXACT 异常。  
  
## <a name="remarks"></a>备注  
 此函数和 `rint` 的主要区别是此函数不会引发不精确的浮点异常。  
  
 因为最大浮点值均为精确的整数，所以此函数本身不会溢出；而输出可能会溢出返回值，具体取决于所使用函数的版本。  
  
## <a name="requirements"></a>惠?  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)