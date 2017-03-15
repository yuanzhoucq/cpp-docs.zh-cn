---
title: "expm1、expm1f、expm1l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
dev_langs:
- C++
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 0fbce9639718ca7316494b1f573a817d8ab0e6f1
ms.lasthandoff: 02/24/2017

---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l
计算以 e 为底的指数减一的值。  
  
## <a name="syntax"></a>语法  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 浮点指数值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `expm1` 函数返回表示 e<sup>x</sup> – 1 的浮点值。 在溢出时，`expm1` 返回 `HUGE_VAL`，`expm1f` 返回 `HUGE_VALF`，`expm1l` 返回 `HUGE_VALL`，且将 `errno` 设置为 `ERANGE`。 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `expm1` 和 `float` 值的 `long double` 重载。 在 C 程序中，`expm1` 始终采用并返回 `double`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp2、exp2f、exp2l](http://msdn.microsoft.com/en-us/a7974629-be1e-4196-a562-6624a0732003)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)
