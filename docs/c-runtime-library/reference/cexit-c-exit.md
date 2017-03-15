---
title: "_cexit、_c_exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_c_exit"
  - "_cexit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_cexit"
  - "c_exit"
  - "_c_exit"
  - "cexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_c_exit 函数"
  - "_cexit 函数"
  - "c_exit 函数"
  - "cexit 函数"
  - "过程期间的清理操作"
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _cexit、_c_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行清理操作并返回，不终止进程。  
  
## 语法  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## 备注  
 `_cexit` 函数调用，后进先出 \(LIFO\)顺序，函数由 `atexit` 和 `_onexit`注册。  然后 `_cexit` 刷新所有 I\/O 缓冲区并在返回之前关闭所有打开流。  `_c_exit` 与 `_exit` 相同，但返回到调用进程时，不处理 `atexit` 或 `_onexit` 或者流刷新缓冲区。  下表中显示了`exit`,`_exit`, `_cexit`，和 `_c_exit`的行为。  
  
|功能|行为|  
|--------|--------|  
|`exit`|执行完整的 C 库停止程序，终止该进程，并以所提供的状态代码退出。|  
|`_exit`|执行快速的 C 库停止程序，终止该进程，并以所提供的状态代码退出。|  
|`_cexit`|执行完整的 C 库停止程序并返回调用方，但是不会终止进程。|  
|`_c_exit`|执行快速的 C 库停止程序并返回调用方，但是不会终止进程。|  
  
 当调用`_cexit` 或 `_c_exit` 的功能时，析构函数在调用时存在的任何临时或自动对象不会被调用。  一个自动对象在对象没有声明为静态函数被定义。  临时对象是由编译器创建的对象。  若要在调用 `_cexit` 或 `_c_exit`之前销毁一个自动对象，请显式调用该对象的析构函数，如下所示：  
  
```  
myObject.myClass::~myClass( );  
```  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cexit`|\<process.h\>|  
|`_c_exit`|\<process.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn, \_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)