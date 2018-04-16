---
title: "nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
dev_langs:
- C++
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4fe078e00b28f09284f3b91ad93ee1393bea108
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
返回下一个可表示的浮点值。  
  
## <a name="syntax"></a>语法  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要从其开始的浮点值。  
  
 `y`  
 要达到的浮点值。  
  
## <a name="return-value"></a>返回值  
 返回 `y` 方向中 `x` 之后的返回类型的下一个可表示浮点值。 如果 `x`=`y`，则函数返回 `y`，转换为返回类型，且未触发异常。 如果 `x` 不等于 `y`，并且结果为非正规或零，则会设置 FE_UNDERFLOW 和 FE_INEXACT 浮点异常状态，并返回正确的结果。 如果 `x` 或 `y` 是 NaN，则返回值为输入 NaN 之一。 如果 `x` 是有限的，并且结果是无穷大或无法在类型中表示，则返回正确的有符号无穷大或 NAN，并设置 FE_OVERFLOW 和 FE_INEXACT 浮点异常状态，并将 `errno` 设置为 ERANGE。  
  
## <a name="remarks"></a>备注  
 `nextafter` 和 `nexttoward` 函数系列是等同的，只不过参数类型为 `y`。 如果 `x` 和 `y` 相等，则返回的值是转换为返回类型的 `y`。  
  
 由于 C++ 允许重载，因此如果包括 \<cmath>，则你可以调用返回 `float` 和 `long double` 类型的 `nextafter` 和 `nexttoward` 重载。 在 C 程序中，`nextafter` 和 `nexttoward` 始终返回 `double`。  
  
 `_nextafter` 和 `_nextafterf` 函数是 Microsoft 特定函数。 `_nextafterf` 函数仅在编译 x64 时可用。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|  
|-------------|---------------------------|-------------------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h>|\<math.h> 或 \<cmath>|  
|`_nextafter`|\<float.h>|\<float.h> 或 \<cfloat>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)