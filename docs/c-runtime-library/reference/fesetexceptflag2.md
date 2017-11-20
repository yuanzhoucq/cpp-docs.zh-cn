---
title: "fesetexceptflag2 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs: C++
helpviewer_keywords: fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 786970d63482f2cede5e6b20af605accebe87da7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fesetexceptflag"></a>fesetexceptflag
在当前浮点环境中设置指定的浮点状态标志。  
  
## <a name="syntax"></a>语法  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstatus`  
 指向 `fexcept_t` 对象的指针，其中包含要设置为异常状态标志的值。 可由以前对 [fegetexceptflag](fegetexceptflag2.md) 的调用设置该对象。  
  
 `excepts`  
 要设置的浮点异常状态标志。  
  
## <a name="return-value"></a>返回值  
 如果成功设置所有指定的异常状态标志，则返回 0。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `fesetexceptflag` 函数将由 `excepts` 指定的浮点异常状态标志的状态设置为由 `pstatus` 指向的 `fexcept_t` 对象中设置的相应值。  它不会引发异常。 `pstatus` 指针必须指向有效的 `fexcept_t` 对象，或未定义后续行为。 `fesetexceptflag` 函数支持 `excepts` 中在 \<fenv.h> 中定义的这些异常宏值：  
  
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
|`fesetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)