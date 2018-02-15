---
title: "lrint、lrintf、lrintl、llrint、llrintf、llrintl | Microsoft 文档"
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
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
dev_langs:
- C++
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80a331618df913040ea145346299ebd30509ce8e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint、lrintf、lrintl、llrint、llrintf、llrintl
使用当前舍入模式和方向将指定浮点值舍入到最接近的整数值。  
  
## <a name="syntax"></a>语法  
  
```  
long int lrint(  
   double x  
);  
  
long int lrint(  
   float x  
); //C++ only  
  
long int lrint(  
   long double x  
); //C++ only  
  
long int lrintf(  
   float x  
);  
  
long int lrintl(  
   long double x  
);  
  
long long int llrint(  
   double x  
);  
  
long long int llrint(  
   float x  
); //C++ only  
  
long long int llrint(  
   long double x  
); //C++ only  
  
long long int llrintf(  
   float x  
);  
  
long long int llrintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 要舍入的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `x` 的舍入的整数值。  
  
|问题|返回|  
|-----------|------------|  
|`x` 超出了返回类型的范围<br /><br /> `x` = ±∞<br /><br /> `x` = NaN|引发 FE_INVALID 并返回零 (0)。|  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用采用浮点型和长双精度型的 `lrint` 和 `llrint` 的重载。 在 C 程序中，`lrint` 和 `llrint` 始终采用双精度型值。  
  
 如果 `x` 不表示等效于整数值的浮点值，则这些函数引发将 FE_INEXACT。  
  
 **特定于 Microsoft**：当结果超出返回类型的范围时，或者当参数为 NaN 或 无穷大时，返回值是定义的实现。 Microsoft 编译器返回零 (0) 值。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`lrint`,                `lrintf`, `lrintl`, `llrint`, `llrintf`, `llrintl`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)