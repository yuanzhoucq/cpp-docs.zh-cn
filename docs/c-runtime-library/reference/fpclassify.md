---
title: "fpclassify | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname: fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f1dac5272bbc8cf956bf8bcfdbd31b1f71b4708
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fpclassify"></a>fpclassify
返回参数的浮点分类。  
  
## <a name="syntax"></a>语法  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要测试的浮点值。  
  
## <a name="return-value"></a>返回值  
 `fpclassify` 返回一个指示参数 `x` 的浮点类的整数值。 此表列出了由 `fpclassify` 返回的在 \<math.h 1> 中定义的可能值。  
  
|“值”|描述|  
|-----------|-----------------|  
|`FP_NAN`|静态、信令或不确定的 NaN|  
|`FP_INFINITE`|正或负无穷大|  
|`FP_NORMAL`|标准化非零正值或负值|  
|`FP_SUBNORMAL`|非标准化的正值或负值|  
|`FP_ZERO`|零正值或负值|  
  
## <a name="remarks"></a>备注  
 在 C 中，`fpclassify` 是一个宏；在 C++ 中，`fpclassify` 是使用参数类型 `float`、`double` 或 `long double` 的重载函数。 在任一情况下，返回的值取决于参数表达式的有效类型，而不是任何中间表示形式。 例如，转换为 `float` 时，正常 `double` 或 `long double` 值可能成为无穷大、非常规，或零值。  
  
## <a name="requirements"></a>惠?  
  
|函数/宏|必需的标头 (C)|必需的标头 (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<math.h>|\<math.h> 或 \<cmath>|  
  
 `fpclassify` 宏和 `fpclassify` 函数符合 C99 C++11 规范。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)