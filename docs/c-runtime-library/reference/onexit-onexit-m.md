---
title: "_onexit、_onexit_m | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _onexit
- _onexit_m
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
apitype: DLLExport
f1_keywords:
- _onexit
- onexit_m
- onexit
- _onexit_m
dev_langs: C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 476df668657739c9f67ca1323c2c0ce630260110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="onexit-onexitm"></a>_onexit、_onexit_m
注册在退出时要调用的例程。  
  
## <a name="syntax"></a>语法  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### <a name="parameters"></a>参数  
 `function`  
 指向在退出时要调用的函数的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `_onexit` 将返回一个指向此函数的指针；如果没有可用于存储此函数指针的空间，则为 `NULL`。  
  
## <a name="remarks"></a>备注  
 当程序正常终止时，向 `_onexit` 函数传递要调用的函数 (`function`) 的地址。 对 `_onexit` 的后续调用将创建一个函数注册表，其中的函数按 LIFO（后进先出）顺序执行。 传递到 `_onexit` 的函数不能接受参数。  
  
 如果从 DLL 范围内调用 `_onexit`，则在使用 DLL_PROCESS_DETACH 调用 `_onexit` 之后，向 `DllMain` 注册的例程将会在 DLL 卸载时运行。  
  
 `_onexit` 是 Microsoft 扩展。 若要获得 ANSI 可移植性，请使用 [atexit](../../c-runtime-library/reference/atexit.md)。 该函数的 `_onexit_m` 版本适用于混合模式。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_onexit`|\<stdlib.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_onexit.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
/* Prototypes */  
int fn1(void), fn2(void), fn3(void), fn4 (void);  
  
int main( void )  
{  
   _onexit( fn1 );  
   _onexit( fn2 );  
   _onexit( fn3 );  
   _onexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
int fn1()  
{  
   printf( "next.\n" );  
   return 0;  
}  
  
int fn2()  
{  
   printf( "executed " );  
   return 0;  
}  
  
int fn3()  
{  
   printf( "is " );  
   return 0;  
}  
  
int fn4()  
{  
   printf( "This " );  
   return 0;  
}  
```  
  
## <a name="output"></a>输出  
  
```  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [__dllonexit](../../c-runtime-library/dllonexit.md)