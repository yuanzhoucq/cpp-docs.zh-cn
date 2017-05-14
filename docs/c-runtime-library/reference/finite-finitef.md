---
title: "_finite、_finitef | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
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
ms.openlocfilehash: 90eff10a00ecfdfd772acc7caa624ff35dd392d7
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="finite-finitef"></a>_finite _finitef
确定浮点值是否是有限的。  
  
## <a name="syntax"></a>语法  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要测试的浮点值。  
  
## <a name="return-value"></a>返回值  
 同时`_finite`和`_finitef`返回非零值，如果自变量*x*是有限; 即，如果-INF < `x` < + INF。 如果该参数为无限值或为 NAN，则其返回 0。  
  
## <a name="remarks"></a>备注  
 `_finite` 和 `_finitef` 函数是 Microsoft 特定函数。 `_finitef` 函数仅在编译 x86、ARM、或 ARM64 平台时可用。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头 (C)|必需的标头 (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h 1> 或 \<math.h 1>|\<float.h 1>、\<math.h 1>、\<cfloat 1> 或 \<cmath 1>|  
|`_finitef`|\<math.h>|\<math.h> 或 \<cmath>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass、_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)
