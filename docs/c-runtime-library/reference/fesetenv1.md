---
title: "fesetenv |Microsoft 文档"
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
- fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2717c0fee2582cac3c9013f3f49ff37744cbde9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fesetenv"></a>fesetenv
设置当前的浮点环境。  
  
## <a name="syntax"></a>语法  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>参数  
 `penv`  
 指向 `fenv_t` 对象的指针，其中包含通过调用 [fegetenv](fegetenv1.md) 或 [feholdexcept](feholdexcept2.md) 设置的浮点环境。 此外，也可以通过使用 FE_DFL_ENV 宏指定默认启动浮点环境。  
  
## <a name="return-value"></a>返回值  
 如果已成功设置环境，则返回 0。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `fesetenv` 函数将从存储在由 `penv` 指向的 `fenv_t` 对象中的值设置当前浮点环境。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 这包括舍入模式和浮点异常的状态标志。  如果 `penv` 不是 FE_DFL_ENV 或未指向有效的 `fenv_t` 对象，则不定义后续行为。  
  
 对此函数的调用设置 `penv` 对象中的异常状态标志，但它不会引发这些异常。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fesetenv`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)