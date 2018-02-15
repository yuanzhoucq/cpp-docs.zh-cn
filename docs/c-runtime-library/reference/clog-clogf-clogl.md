---
title: "clog、clogf、clogl | Microsoft 文档"
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
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
dev_langs:
- C++
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 045eaee50f988e5712fd23845bd91db68c75ba65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="clog-clogf-clogl"></a>clog、clogf、clogl
检索复数的自然对数，沿负实轴进行分支切割。  
  
## <a name="syntax"></a>语法  
  
```  
_Dcomplex clog(   
   _Dcomplex z   
);  
_Fcomplex clog(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex clog(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clogf(   
   _Fcomplex z   
);  
_Lcomplex clogl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>参数  
 `z`  
 对数的底。  
  
## <a name="return-value"></a>返回值  
 `z` 的自然对数。 结果是实际轴和间隔中，不受限制 [-iπ，+ iπ] 轴虚部的复数。  
  
 可能的返回值为：  
  
|z 参数|返回值|  
|-----------------|------------------|  
|正|以 10 为底的 z 对数|  
|零|- ∞|  
|负数|NaN|  
|NaN|NaN|  
|+ ∞|+ ∞|  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用采用并返回 `clog` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中，`clog` 始终采用并返回 `_Dcomplex` 值。  
  
## <a name="requirements"></a>要求  
  
|例程|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`clog`,               `clogf`, `clogl`|\<complex.h>|\<ccomplex>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp、cexpf、cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow、cpowf、cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10、clog10f、clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)