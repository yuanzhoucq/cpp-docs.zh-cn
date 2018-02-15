---
title: "cexp、cexpf、cexpl | Microsoft 文档"
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
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
dev_langs:
- C++
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce5f42c8a13db45e3f75345b873bc6ec76885052
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cexp-cexpf-cexpl"></a>cexp、cexpf、cexpl
计算复数的以 e 为底的指数。  
  
## <a name="syntax"></a>语法  
  
```  
_Dcomplex cexp(   
   _Dcomplex z   
);  
_Fcomplex cexp(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cexp(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cexpf(   
  _Fcomplex z   
);  
_Lcomplex cexpl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 表示指数的复数。  
  
## <a name="return-value"></a>返回值  
 `e` 的 `z`次幂值。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `cexp` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中，`cexp` 始终采用并返回 `_Dcomplex` 值。  
  
## <a name="requirements"></a>要求  
  
|例程|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`cexp`,               `cexpf`, `cexpl`|\<complex.h>|\<complex.h>|  
  
 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cpow、cpowf、cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10、clog10f、clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [clog、clogf、clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)