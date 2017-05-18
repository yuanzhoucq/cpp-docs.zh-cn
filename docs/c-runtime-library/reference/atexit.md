---
title: "atexit | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- atexit
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
- atexit
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
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
ms.openlocfilehash: 6d0d85ffc7f3ed71a26a947dd66c710e76388e96
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="atexit"></a>atexit
处理退出时指定的函数。  
  
## <a name="syntax"></a>语法  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### <a name="parameters"></a>参数  
 `func`  
 要调用的函数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `atexit` 返回 0；如果发生错误，则返回非零值。  
  
## <a name="remarks"></a>备注  
 当程序正常终止时，向 `atexit` 函数传递要调用的函数 (`func`) 的地址。 对 `atexit` 的后续调用将创建一个函数注册表，其中的函数按后进先出 (LIFO) 顺序执行。 传递到 `atexit` 的函数不能接受参数。 `atexit` 和 `_onexit` 使用堆保存函数注册表。 因此，可以注册的函数的数量仅受堆内存限制。  
  
 `atexit` 函数中的代码不应该包含在调用 `atexit` 函数时已卸载的任何 DLL 上的任何依赖项。  
  
 要生成符合 ANSI 的应用程序，请使用 ANSI 标准的 `atexit` 函数（而不是类似的 `_onexit` 函数）。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`atexit`|\<stdlib.h>|  
  
## <a name="example"></a>示例  
 调用 `atexit` 时，该程序将四个函数推送到要执行的函数堆栈。 当程序退出时，这些程序以后进先出的方式执行。  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
```Output  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)
