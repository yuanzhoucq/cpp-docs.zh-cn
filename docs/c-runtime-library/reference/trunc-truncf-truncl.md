---
title: "trunc、truncf、truncl | Microsoft 文档"
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
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
dev_langs: C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 911636e4fa843afa1220dc99e1f679d5bfe88d7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="trunc-truncf-truncl"></a>trunc、truncf、truncl
确定小于或等于指定浮点值的最接近的整数。  
  
## <a name="syntax"></a>语法  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要截断的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回向零舍入的 `x` 的整数值。  
  
 否则，可能返回以下值之一：  
  
|问题|返回|  
|-----------|------------|  
|`x`= ±INFINITY|x|  
|`x` =  ±0|x|  
|`x` = NaN|NaN|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中所指定的报告错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用 `trunc` 重载，以采用并返回浮点型和长双精度型值 。 在 C 程序中，`trunc` 始终采用及返回双精度型。  
  
 由于最大的浮点值是精确的整数，因此该函数不会自行溢出。 但是，将值还原为整型时可能会导致此函数溢出。  
  
 还可以通过从浮点隐式转换为整数来向下舍入；但是此操作仅限于可存储为目标类型的值。  
  
## <a name="requirements"></a>惠?  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`trunc`,                `truncf`,  `truncl`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)