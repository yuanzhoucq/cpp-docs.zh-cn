---
title: "feclearexcept1 | Microsoft 文档"
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
- feclearexcept
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
- feclearexcept
- fenv/feclearexcept
dev_langs:
- C++
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 661e93b181005acbd822fbb3ea2a2f970bbedf3d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="feclearexcept"></a>feclearexcept
尝试清除由参数指定的浮点异常标记。  
  
## <a name="syntax"></a>语法  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>参数  
 `excepts`  
 要清除的异常状态标记。  
  
## <a name="return-value"></a>返回值  
 如果 `excepts` 为零，或者如果已成功清除了所有指定的异常，则返回零。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `feclearexcept` 函数尝试清除由 `excepts` 指定的浮点异常状态标记。 此函数支持在 fenv.h 中定义的这些异常宏：  
  
|异常宏|描述|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|  
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|  
|FE_INVALID|早期浮点运算中发生域错误。|  
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|  
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|  
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|  
  
 `excepts` 参数可能为零，或为一个或多个所支持的异常宏的按位 OR。 任何其他参数值的结果均未定义。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`feclearexcept`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)