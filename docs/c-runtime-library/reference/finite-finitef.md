---
title: "_finite、_finitef | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb904e04e8a99bff242d520f6c0ca3d404a74e89
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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
 同时`_finite`和`_finitef`返回非零值，如果自变量*x*是有限; 即，如果-INF < `x` < + INF。 如果该自变量为无限值或为 NAN，则其返回 0。  
  
## <a name="remarks"></a>备注  
 `_finite` 和 `_finitef` 函数是 Microsoft 的特定函数。 `_finitef` 函数仅在编译 x86、ARM、或 ARM64 平台时可用。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头 (C)|必需的标头 (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h 1> 或 \<math.h 1>|\<float.h 1>、\<math.h 1>、\<cfloat 1> 或 \<cmath 1>|  
|`_finitef`|\<math.h>|\<math.h> 或 \<cmath>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass、_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)