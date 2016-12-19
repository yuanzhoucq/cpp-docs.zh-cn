---
title: "set_terminate (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "set_terminate"
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
  - "set_terminate"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "异常处理, 终止"
  - "set_terminate 函数"
  - "terminate 函数"
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_terminate (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安装被`terminate` 调用的终端函数。  
  
## 语法  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### 参数  
 `termFunction`  
 指向自己编写的终止函数的指针。  
  
## 返回值  
 返回指向由 `set_terminate` 注册的前终端函数，以便前面的函数之后可能还原。  如果以前尚未设置函数，返回值可用于还原默认行为；此值可能为 NULL。  
  
## 备注  
 `set_terminate` 函数安装 `termFunction` 作为 `terminate`调用的函数。  C\+\+ 异常处理使用`set_terminate`，且在抛出异常之前， 在程序中可以随时调用。  `terminate` 默认调用 `abort`。  通过编写您自己终止函数和通过你的函数作为它的参数来调用 `set_terminate` 来更改此默认。  `terminate` 调用指定为 `set_terminate` 的参数的最后一个函数。  在执行任何所需的清理任务后，`termFunction` 应该退出程序。  如果不退出 \(如果它返回到调用方\)，则调用 `abort`。  
  
 在多线程环境中，每个线程都是单独维护终止函数。  每个新线程需要安装自己的终止函数。  因此，每个线程都控制自己终止处理。  
  
 `terminate_function` type定义为指向用户定义的终止函数的指针，`termFunction` 返回 `void` 自定义 `termFunction` 函数不采用参数，不应返回到调用方。  如果是，调用 `abort`。  不能从 `termFunction`抛出异常。  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  `set_terminate` 函数仅在调试器外部运行。  
  
 所有的动态链接DLLs 或 EXEs 有单`set_terminate`，即使您调用`set_terminate`处理程序可能会被另一个替代，或者您用另外的DLL 或 EXE替代处理程序。  
  
 **\/clr:pure**不支持此功能。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`set_terminate`|\<eh.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 有关示例，请参见 [terminate](../../c-runtime-library/reference/terminate-crt.md) 类。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)