---
title: "feupdateenv | Microsoft 文档"
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
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd4a74515b2b3ab29b30fb07d80121e35d950ee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="feupdateenv"></a>feupdateenv
保存当前引发的浮点异常，还原指定的浮点环境状态，并引发已保存的浮点异常。  
  
## <a name="syntax"></a>语法  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
### <a name="parameters"></a>参数  
 `penv`  
 指向 `fenv_t` 对象的指针，其中包含通过调用 [fegetenv](fegetenv1.md) 或 [feholdexcept](feholdexcept2.md) 设置的浮点环境。 此外，也可以通过使用 FE_DFL_ENV 宏指定默认启动浮点环境。  
  
## <a name="return-value"></a>返回值  
 如果所有操作已成功完成，则返回 0。 否则，返回一个非零值。  
  
## <a name="remarks"></a>备注  
 `feupdateenv` 函数执行多个操作。 首先，它在自动存储中存储当前引发的浮点异常状态标志。 然后，它将从存储在由 `penv` 指向 `fenv_t` 的对象中的值设置当前浮点环境。 如果 `penv` 不是 FE_DFL_ENV 或未指向有效的 `fenv_t` 对象，则不定义后续行为。 最后，`feupdateenv` 引发本地存储的浮点异常。  
  
 若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|C 标头|C++ 标头|  
|--------------|--------------|------------------|  
|`feupdateenv`|\<fenv.h>|\<cfenv>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)