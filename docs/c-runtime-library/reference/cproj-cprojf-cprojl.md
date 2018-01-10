---
title: "cproj、cprojf、cprojl | Microsoft 文档"
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
- cproj
- cprojf
- cprojl
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
- cproj
- cprojf
- cprojl
- complex/cproj
- complex/cprojf
- complex/cprojl
dev_langs: C++
helpviewer_keywords:
- cproj function
- cprojf function
- cprojl function
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 086abc1446302145eb2749cec10fb07c9d81014a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cproj-cprojf-cprojl"></a>cproj、cprojf、cprojl
检索 Reimann 球体上某个复数的投影。  
  
## <a name="syntax"></a>语法  
  
```  
_Dcomplex cproj(   
   _Dcomplex z   
);  
_Fcomplex cproj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cproj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cprojf(   
   _Fcomplex z   
);  
_Lcomplex cprojl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 一个复数。  
  
## <a name="return-value"></a>返回值  
 Reimann 球体上 `z` 的投影。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `cproj` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中，`cproj` 始终采用并返回 `_Dcomplex` 值。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`cproj`,               `cprojf`, `cprojl`|\<complex.h>|\<ccomplex>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag、cimagf、cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg、cargf、cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)