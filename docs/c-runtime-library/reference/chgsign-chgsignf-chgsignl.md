---
title: "_chgsign、_chgsignf、_chgsignl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
dev_langs: C++
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d21b7904bdd048a87f699a6999e79c407f15ec1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chgsign-chgsignf-chgsignl"></a>_chgsign、_chgsignf、_chgsignl
颠倒浮点型参数的符号。  
  
## <a name="syntax"></a>语法  
  
```  
double _chgsign(   
   double x   
);  
float _chgsignf(  
   float x   
);  
long double _chgsignl(   
   long double x   
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要更改的浮点值。  
  
## <a name="return-value"></a>返回值  
 `_chgsign` 函数返回一个值，该值等于浮点型参数 `x`，但符号颠倒。 无错误返回。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_chgsign`|\<float.h>|  
|`_chgsignf`, `_chgsignl`|\<math.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)