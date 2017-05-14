---
title: "carg、cargf、cargl | Microsoft 文档"
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
- carg
- cargf
- cargl
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
- carg
- cargf
- cargl
- complex/carg
- complex/cargf
- complex/cargl
dev_langs:
- C++
helpviewer_keywords:
- carg function
- cargf function
- cargl function
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
caps.latest.revision: 8
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
ms.openlocfilehash: f4239a5d0834938d80ae2054396e485eef127e4b
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="carg-cargf-cargl"></a>carg、cargf、cargl
检索复数的自变量，沿负实轴进行分支切割。  
  
## <a name="syntax"></a>语法  
  
```  
double carg(   
   _Dcomplex z   
);  
float carg(   
   _Fcomplex z   
);  // C++ only  
long double carg(   
   _Lcomplex z   
);  // C++ only  
float cargf(   
   _Fcomplex z   
);  
long double cargl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 一个复数。  
  
## <a name="return-value"></a>返回值  
 `z` 的自变量（也称为相位）。 结果处于间隔 [-π，+ π]。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此可以调用采用 `_Fcomplex` 或 `_Lcomplex` 值的 `carg` 的重载，并返回 `float` 或 `long double` 值。 在 C 程序中，`carg` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## <a name="requirements"></a>要求  
  
|例程|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`carg`,               `cargf`, `cargl`|\<complex.h>|\<ccomplex>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj、cprojf、cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag、cimagf、cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)
