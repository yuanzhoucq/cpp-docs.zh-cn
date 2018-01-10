---
title: "cimag、cimagf、cimagl | Microsoft 文档"
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
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
dev_langs: C++
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b499786cbcb1516fb9746d69c7e124f14d00f011
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cimag-cimagf-cimagl"></a>cimag、cimagf、cimagl
检索复数的虚部。  
  
## <a name="syntax"></a>语法  
  
```  
double cimag(   
   _Dcomplex z   
);  
float cimag(   
   _Fcomplex z   
);  // C++  
long double cimag(   
  _Lcomplex z   
);  // C++  
float cimagf(   
   _Fcomplex z   
);  
long double cimagl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 一个复数。  
  
## <a name="return-value"></a>返回值  
 `z` 的虚部。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此可以调用采用 `_Fcomplex` 或 `_Lcomplex` 值的 `cimag` 的重载，并返回 `float` 或 `long double` 值。 在 C 程序中，`cimag` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`cimag`,               `cimagf`, `cimagl`|\<complex.h>|\<ccomplex>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj、cprojf、cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [carg、cargf、cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)