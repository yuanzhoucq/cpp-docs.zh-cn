---
title: "ilogb、ilogbf、ilogbl2 | Microsoft 文档"
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
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8da5ba71b59f64c38a051fd8f31fa7bf58a4556d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb、ilogbf、ilogbl
检索一个整数，以表示指定值以 2 为底的无偏差指数。  
  
## <a name="syntax"></a>语法  
  
```  
int ilogb(  
   double x  
);  
  
int ilogb(  
   float x  
); //C++ only  
  
int ilogb(  
   long double x  
); //C++ only  
  
int ilogbf(  
   float x  
);  
  
int ilogbl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 [in] `x`  
 指定的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 `x` 的以 2 为底的指数作为一个带符号的 `int` 值。  
  
 否则将返回在 \<math.h> 中定义的以下值之一：  
  
|输入|结果|  
|-----------|------------|  
|±0|FP_ILOGB0|  
|±inf，±nan，无限期|FP_ILOGBNAN|  
  
 按 [_matherr](../../c-runtime-library/reference/matherr.md) 中指定的内容报告错误。  
  
## <a name="remarks"></a>备注  
 由于 C++ 支持重载，可以调用 `ilogb` 重载，以采用并返回浮点型和长双精度型值 。 在 C 程序中，`ilogb` 始终采用及返回双精度型。  
  
 调用此函数相当于调用等效 `logb` 函数，然后将返回值转换为 `int`。  
  
## <a name="requirements"></a>要求  
  
|例程|C 标头|C++ 标头|  
|-------------|--------------|------------------|  
|`ilogb`,                `ilogbf`,  `ilogbl`|\<math.h>|\<cmath>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [logb, logbf, logbl, _logb, _logbf](../../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)