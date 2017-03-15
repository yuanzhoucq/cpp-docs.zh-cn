---
title: "copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
dev_langs:
- C++
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
caps.latest.revision: 16
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 513ba53a63351b7239c0612103c41977e930eafa
ms.lasthandoff: 02/24/2017

---
# <a name="copysign-copysignf-copysignl-copysign-copysignf-copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
返回一个值，该值具有一个自变量的数值和另一个自变量的符号。  
  
## <a name="syntax"></a>语法  
  
```  
double copysign(   
   double x,  
   double y   
);  
float copysign(   
   float x,  
   float y   
); // C++ only  
long double copysign(   
   long double x,  
   long double y   
); // C++ only  
float copysignf(   
   float x,  
   float y   
); // C++ only  
long double copysignl(   
   long double x,  
   long double y   
); // C++ only  
double _copysign(   
   double x,  
   double y   
);  
long double _copysignl(   
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 作为结果的数值返回的浮点值。  
  
 `y`  
 作为结果的符号返回的浮点值。  
  
 [浮点支持例程](../../c-runtime-library/floating-point-support.md)  
  
## <a name="return-value"></a>返回值  
 `copysign` 函数返回将 `x` 的数值与 `y` 的符号相结合的浮点值。 无错误返回。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `copysign` 或 `float` 值的 `long double` 重载。 在 C 程序中，`copysign` 始终采用并返回 `double`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_copysign`|\<float.h>|  
|`copysign`, `copysignf`, `copysignl`, `_copysignf``_copysignl`|\<math.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [_chgsign、_chgsignf、_chgsignl](../../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)
