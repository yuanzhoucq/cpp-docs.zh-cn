---
title: "_scalb | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _scalb
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
- scalb
- _scalb
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- _scalb function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f68d1e14a4f92c2ed7ee481966dc46c4384341f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="scalb"></a>_scalb
按 2 的幂缩放自变量。  
  
## <a name="syntax"></a>语法  
  
```  
double _scalb(  
   double x,  
   long exp   
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 双精度浮点值。  
  
 `exp`  
 长整数指数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回指数值。 在溢出 (具体取决于的符号`x`)，`_scalb`返回 + /- `HUGE_VAL`;`errno`变量设置为`ERANGE`。  
  
 有关此代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_scalb` 函数计算 `x *` 2exp 的值。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_scalb`|\<float.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)