---
title: "exit、_Exit、_exit | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.assetid: b1501fa6-27c2-478c-9e93-cc4fd802a01f
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 8d6f75bb19c2cfd89d8714ed87ff91ddf340055e
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit
终止调用进程。 `exit` 函数会在清除后终止调用进程； `_exit` 和 `_Exit` 会立即终止调用进程。  
  
> [!NOTE]
>  请勿使用此方法关闭通用 Windows 平台 (UWP) 应用或 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用，除非在测试或调试方案中。 不允许使用编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用。 有关 Windows 8 和 8.1 应用的详细信息，请参阅 [应用生命周期](http://go.microsoft.com/fwlink/?LinkId=262853)。 有关 Windows 10 应用的详细信息，请参阅 [Windows 10 应用的操作方法指南](http://go.microsoft.com/fwlink/p/?linkid=619133)。  
  
## <a name="syntax"></a>语法  
  
```  
void exit(   
   int const status   
);  
void _Exit(   
   int const status   
);  
void _exit(   
   int const status   
);  
```  
  
#### <a name="parameters"></a>参数  
 `status`  
 退出状态代码。  
  
## <a name="remarks"></a>备注  
 `exit`、 `_Exit` 和 `_exit` 函数会终止调用进程。 `exit` 函数调用线程本地对象的析构函数，然后按照后进先出 (LIFO) 顺序调用由 `atexit` 和 `_onexit`注册的函数，接着在函数终止进程之前刷新所有文件缓冲区。 `_Exit` 和 `_exit` 函数会终止进程，同时无需销毁线程本地对象或处理 `atexit` 或 `_onexit` 函数，且无需刷新流缓冲区。  
  
 尽管 `exit`、 `_Exit` 和 `_exit` 调用不返回值，但是在进程退出后，如果存在， `status` 的低序位字节可用于主机环境或等待调用进程。 通常情况下，调用方将 `status` 值设置为 0 来指示正常退出，或设置为其他值来指示错误。 `status` 值可用于操作系统批处理命令 `ERRORLEVEL` ，并且由两个常量之一表示： `EXIT_SUCCESS`或 `EXIT_FAILURE`，前者表示值为 0，后者表示值为 1。  
  
 `exit`、 `_Exit`、 `_exit`、 `quick_exit`、 `_cexit`和 `_c_exit` 函数的行为如下：  
  
|函数|描述|  
|--------------|-----------------|  
|`exit`|执行完整的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|  
|`_Exit`|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|  
|`_exit`|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|  
|`quick_exit`|执行快速的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|  
|`_cexit`|执行完整的 C 库终止过程并返回给调用方。 不终止进程。|  
|`_c_exit`|执行最少的 C 库终止过程并返回给调用方。 不终止进程。|  
  
 当你调用 `exit`、  `_Exit` 或 `_exit` 函数时，不会调用在调用时存在的任何临时或自动对象的析构函数。 自动对象在该对象未声明为静态的函数中进行定义。 临时对象是由编译器创建的对象。 若要在调用 `exit`、 `_Exit`或 `_exit`之前销毁自动对象，请显式调用该对象的析构函数，如下所示：  
  
```  
myObject.myClass::~myClass();  
```  
  
 请勿使用 `DLL_PROCESS_ATTACH` 从 `exit` 中调用 `DllMain`。 如果你想要退出 `DLLMain` 函数，请从 `FALSE` 返回 `DLL_PROCESS_ATTACH`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`exit`, `_Exit`, `_exit`|\<process.h> 或 \<stdlib.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_exit.c  
// This program returns an exit code of 1. The  
// error code could be tested in a batch file.  
  
#include <stdlib.h>  
  
int main( void )  
{  
   exit( 1 );  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_cexit、_c_exit](../../c-runtime-library/reference/cexit-c-exit.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [quick_exit](../../c-runtime-library/reference/quick-exit1.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)
