---
title: "_cexit、_c_exit | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: a68b803ee7dc444439d7a62f43cf7157e7fbf505
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="cexit-cexit"></a>_cexit、_c_exit
执行清理操作并返回，而不终止进程。  
  
## <a name="syntax"></a>语法  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>备注  
 `_cexit` 函数以后进先出 (LIFO) 顺序调用由 `atexit` 和 `_onexit`.注册的函数。 然后，`_cexit` 刷新所有 I/O 缓冲区并在返回前关闭所有打开的流。 `_c_exit` 与 `_exit` 相同，但前者返回到调用进程，而无需处理 `atexit` 或 `_onexit` 或刷新流缓冲区。 下表中显示了 `exit`、`_exit`、`_cexit` 和 `_c_exit` 的行为。  
  
|函数|行为|  
|--------------|--------------|  
|`exit`|执行完整的 C 库终止过程，终止进程，并使用提供的状态代码退出。|  
|`_exit`|执行快速的 C 库终止过程，终止进程，并使用提供的状态代码退出。|  
|`_cexit`|执行完整的 C 库终止过程并返回给调用方，但不中止进程。|  
|`_c_exit`|执行快速的 C 库终止过程并返回给调用方，但不中止进程。|  
  
 当你调用 `_cexit` 或 `_c_exit` 函数时，不会调用在调用时存在的任何临时或自动对象的析构函数。 自动对象是在对象未声明为静态的函数中进行定义的对象。 临时对象是由编译器创建的对象。 若要在调用 `_cexit` 或 `_c_exit` 之前销毁自动对象，请显式调用该对象的析构函数，如下所示：  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_cexit`|\<process.h>|  
|`_c_exit`|\<process.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)
