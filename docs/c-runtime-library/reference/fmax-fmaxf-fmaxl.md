---
title: "fmax、fmaxf、fmaxl | Microsoft 文档"
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
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs:
- C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 8953e3bd81158ce183e1abb5dfa969164c1f9ced
ms.openlocfilehash: 2c8520367d07f0c42f9245421040cbc665771722
ms.lasthandoff: 02/24/2017

---
# <a name="fmax-fmaxf-fmaxl"></a>fmax、fmaxf、fmaxl
确定两个指定数字值的较大值。  
  
## <a name="syntax"></a>语法  
  
```  
double fmax(  
   double x,   
   double y  
);  
  
float fmax(  
   float x,   
   float y  
); //C++ only  
  
long double fmax(  
   long double x,   
   long double y  
); //C++ only  
  
float fmaxf(  
   float x,   
   float y  
);  
  
long double fmaxl(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要比较的第一个值。  
  
 [in] `y`  
 要比较的第二个值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回较大的 `x` 或 `y`。 返回的为准确值，且不依赖于任何形式的舍入。  
  
 否则，可能返回以下值之一：  
  
|问题|返回|  
|-----------|------------|  
|`x` = NaN|`y`|  
|`y` = NaN|`x`|  
|`x` 和 `y` = NaN|NaN|  
  
 此函数不使用 [_matherr](../../c-runtime-library/reference/matherr.md) 中指定的错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用采用并返回浮点型和长双精度型的 fmax 的重载。 在 C 程序中，fmax 始终采用和返回双精度型。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<math.h>|\<cmath> 或 \<math.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin、fminf、fminl](fmin-fminf-fminl.md)  
