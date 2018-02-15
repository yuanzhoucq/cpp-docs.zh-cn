---
title: "fetestexcept1 | Microsoft 文档"
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
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fetestexcept
- fenv/fetestexcept
dev_langs:
- C++
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f70e78e515e50b00992a22eb01988e09a5ccd42
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fetestexcept"></a>fetestexcept
确定当前设置了哪些指定的浮点异常状态标志。  
  
## <a name="syntax"></a>语法  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `excepts`  
 要测试的浮点     状态标志的按位 OR。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回一个包含与当前设置的异常状态标志对应的浮点异常宏的按位 OR 的位掩码。 如果没有设置异常，则返回 0。  
  
## <a name="remarks"></a>备注  
 使用 fetestexcept 函数来确定哪些异常由浮点运算引发。 使用 `excepts` 参数来指定要测试的异常状态标志。 `fetestexcept` 函数使用 `excepts` 中在 \<v.h 1> 中定义的这些异常宏和返回值：  
  
|异常宏|描述|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|  
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|  
|FE_INVALID|早期浮点运算中发生域错误。|  
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|  
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|  
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|  
  
 指定的 `excepts` 参数可能为 0、一个受支持的浮点异常宏，或为两个或多个宏的按位 OR。 未定义任何其他 `excepts` 参数值的效果。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fetestexcept`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)