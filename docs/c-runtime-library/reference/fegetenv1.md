---
title: "fegetenv1 | Microsoft 文档"
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
- fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 025b934ec6a2d9bc98d46cabbd13b93e263cd777
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="fegetenv"></a>fegetenv
在指定对象中存储当前浮点环境。  
  
## <a name="syntax"></a>语法  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `penv`  
 指向 `fenv_t` 对象，以包含当前浮点环境值的指针。  
  
## <a name="return-value"></a>返回值  
 如果在 `penv` 中成功存储了浮点环境，则返回 0。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `fegetenv` 函数存储由 `penv` 指向的对象中的当前浮点环境。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 包括舍入方向模式和浮点异常的状态标志。  如果 `penv` 不指向有效的 `fenv_t` 对象，则不定义后续行为。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`fegetenv`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)