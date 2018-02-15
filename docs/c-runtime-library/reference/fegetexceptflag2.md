---
title: "fegetexceptflag2 | Microsoft 文档"
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
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1180db74e0000f24e12b6d411460e6a4efc9de
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fegetexceptflag"></a>fegetexceptflag
存储指定的浮点异常标志的当前状态。  
  
## <a name="syntax"></a>语法  
  
```  
int fegetexceptflag(   
   fexcept_t* pstatus,   
   int excepts   
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `pstatus`  
 指向 `fexcept_t` 对象以包含由 `excepts` 指定的异常标志的当前值的指针。  
  
 `excepts`  
 要在 `pstatus` 中存储的浮点异常标志。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `fegetexceptflag` 函数存储浮点异常状态标志的当前状态（由 `pstatus` 指向的 `fexcept_t` 对象中的 `excepts` 指定）。  `pstatus` 必须指向有效的 `fexcept_t` 对象，或未定义后续行为。 `fegetexceptflag` 函数支持 \<fenv.h> 中定义的这些异常宏：  
  
|异常宏|描述|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|  
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|  
|FE_INVALID|早期浮点运算中发生域错误。|  
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|  
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|  
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|  
  
 `excepts` 参数可能为零、一个受支持的浮动点异常宏，或为两个或多个宏的按位 OR。 未定义任何其他参数值的效果。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fegetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)