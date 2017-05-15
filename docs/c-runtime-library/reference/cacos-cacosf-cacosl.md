---
title: "cacos、cacosf、cacosl | Microsoft 文档"
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
- cacos
- cacosf
- cacosl
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
- cacos
- cacosf
- cacosl
- complex/cacos
- complex/cacosf
- complex/cacosl
dev_langs:
- C++
helpviewer_keywords:
- cacos function
- cacosf function
- cacosl function
ms.assetid: 78118c00-0a07-49c1-8a13-4bf19ce3aea8
caps.latest.revision: 13
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
ms.openlocfilehash: e61472ce3ae0fa35a772f5b628b468e398c25722
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="cacos-cacosf-cacosl"></a>cacos、cacosf、cacosl
检索复数，与实际轴间隔 [-1，+ 1] 外的分支刮痕反余弦的值。  
  
## <a name="syntax"></a>语法  
  
```  
_Dcomplex cacos(   
  _Dcomplex z   
);  
_Fcomplex cacos(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cacos(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cacosf(   
   _Fcomplex z   
);  
_Lcomplex cacosl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 表示角度的复数（以弧度为单位）。  
  
## <a name="return-value"></a>返回值  
 `z` 的反余弦值（以弧度为单位）。 沿虚轴的结果为无限，并位于沿实轴的间隔 [0, π] 中。 如果 `z` 超出间隔 [-1, +1]，则会发生域错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `cacos` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中，`cacos` 始终采用并返回 `_Dcomplex` 值。  
  
## <a name="requirements"></a>要求  
  
|例程|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`cacos`,               `cacosf`, `cacosl`|\<complex.h>|\<ccomplex>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh、catanhf、catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh、ctanhf、ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan、catanf、catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh、csinhf、csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh、casinhf、casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh、ccoshf、ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh、cacoshf、cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [ctan、ctanf、ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin、csinf、csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin、casinf、casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos、ccosf、ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt、csqrtf、csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)
