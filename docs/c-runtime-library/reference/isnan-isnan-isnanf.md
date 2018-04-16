---
title: "isnan、_isnan、_isnanf | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs:
- C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10d0997b1a6b304634c612f0f1615a059fd812b2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf
测试浮点值是否不是一个数字 (NAN)。  
  
## <a name="syntax"></a>语法  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 要测试的浮点值。  
  
## <a name="return-value"></a>返回值  
 在 C 中，如果该参数 `x` 是 NAN，则 `isnan` 宏和 `_isnan` 及 `_isnanf` 函数将返回一个非零值；否则它们会返回 0。  
  
 在 C++ 中，如果参数 `x` 是 NAN，则 `isnan` 模板函数将返回 `true`；否则它们会返回 `false`。  
  
## <a name="remarks"></a>备注  
 C `isnan` 宏和 `_isnan` 及 `_isnanf` 函数测试浮点值 *x*，如果 *x* 不是数字 (NAN) 值，则返回一个非零值。 如果无法为指定类型以 IEEE 754 浮点格式表示浮点运算的结果，则会生成 NAN。 有关如何将 NAN 表示为输出的信息，请参阅 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
 作为 C++ 编译时，不会定义 `isnan` 宏，而是定义 `isnan` 模板函数。 它将返回 `bool` 类型的值而不是整数。  
  
 `_isnan` 和 `_isnanf` 函数是 Microsoft 的特定函数。 `_isnanf` 函数仅在编译 x64 时可用。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头 (C)|必需的标头 (C++)|  
|-------------|---------------------------|-------------------------------|  
|`isnan`, `_isnanf`|\<math.h>|\<math.h> 或 \<cmath>|  
|`_isnan`|\<float.h>|\<float.h> 或 \<cfloat>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_finite、_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [_fpclass、_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)