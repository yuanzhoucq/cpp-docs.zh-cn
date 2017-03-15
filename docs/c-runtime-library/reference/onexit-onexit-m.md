---
title: "_onexit、_onexit_m | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_onexit"
  - "_onexit_m"
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
apitype: "DLLExport"
f1_keywords: 
  - "_onexit"
  - "onexit_m"
  - "onexit"
  - "_onexit_m"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "onexit 函数"
  - "注册表, 注册退出例程"
  - "_onexit_m 函数"
  - "onexit_m 函数"
  - "_onexit 函数"
  - "注册退出例程"
  - "注册为退出时调用"
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _onexit、_onexit_m
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在退出时间注册一个实例被调用。  
  
## 语法  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### 参数  
 `function`  
 在退出时，要调用的函数指针。  
  
## 返回值  
 如果成功的话，`_onexit` 返回指向函数的指针，如果没有空间存储函数指针，则返回`NULL`。  
  
## 备注  
 当程序正常终止时，`_onexit` 函数传递 \(`function`\) 的地址来调用。   `_onexit` 的成功调用将创建按 LIFO（后进先出）顺序执行的函数的注册。  函数传递给 `_onexit` 不能带参数。  
  
 这种情况下，从 DLL 的内部调用 `_onexit` 时，在`DllMain` 调用 DLL\_PROCESS\_DETACH 之后，注册`_onexit` 的例程运行在动态链接库上。  
  
 `_onexit` 是Microsoft扩展。  对于 ANSI 可移植性，请使用 [atexit](../../c-runtime-library/reference/atexit.md)。  函数的 `_onexit_m` 版本在混合模式中使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_onexit`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
## Output  
  
```  
This is executed first.  
This is executed next.  
```  
  
## .NET Framework 等效项  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_\_dllonexit](../../c-runtime-library/dllonexit.md)