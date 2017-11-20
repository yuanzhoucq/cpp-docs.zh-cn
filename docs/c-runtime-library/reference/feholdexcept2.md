---
title: "feholdexcept2 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: feholdexcept
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
- feholdexcept
- fenv/feholdexcept
dev_langs: C++
helpviewer_keywords: feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfc0ce4da07bb83fbe003e7ea23029628f4e199b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="feholdexcept"></a>feholdexcept
将当前浮点环境保存在指定对象中，清除浮点状态标志，如果可能，请将浮点环境置于不间断模式。  
  
## <a name="syntax"></a>语法  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>参数  
 `penv`  
 指向 `fenv_t` 对象，以包含浮点环境的副本。  
  
## <a name="return-value"></a>返回值  
 当且仅当函数是能够成功启用非停止浮点异常处理，则返回零。  
  
## <a name="remarks"></a>备注  
 `feholdexcept` 函数用于存储 `penv` 指向的 `fenv_t` 对象中的当前浮动点环境状态，并设置环境以确保不中断浮点异常执行。 这被称为不间断模式。  此模式将继续，直到使用 [fesetenv](fesetenv1.md) 或 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md) 恢复环境。  
  
 在需要隐藏来自调用方的一个或多个浮点异常的子例程的开头，可以使用此函数。 若要报告异常，只需通过使用 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md) 清除不需要的异常，然后通过对 `feupdateenv` 的调用结束不间断模式。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](fesetenv1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)