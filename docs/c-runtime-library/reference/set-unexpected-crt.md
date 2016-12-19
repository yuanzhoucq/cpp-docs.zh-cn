---
title: "set_unexpected (CRT) | Microsoft Docs"
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
  - "set_unexpected"
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
  - "set_unexpected"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "异常处理, 终止"
  - "set_unexpected 函数"
  - "unexpected 函数"
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_unexpected (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安装你自己的通过 `unexpected` 被调用的终端函数。  
  
## 语法  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### 参数  
 `unexpFunction`  
 编写的用于替换 `unexpected` 的函数的指针。  
  
## 返回值  
 返回指向由 `_set_unexpected` 注册的前终端函数，以便前面的函数之后可能还原。  如果以前尚未设置函数，返回值可用于还原默认行为；此值可能为 NULL。  
  
## 备注  
 `set_unexpected` 函数安装 `unexpFunction` 作为 `unexpected`调用的函数。  在当前 C\+\+异常处理实现中不使用`unexpected`。  `unexpected_function` type定义为指向用户定义的异常函数的指针，`unexpFunction` 返回 `void` 自定义 `unexpFunction` 函数不应返回到调用方。  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 `unexpected` 默认调用 `terminate`。  通过编写您自己终止函数和通过你的函数作为它的参数来调用 `set_unexpected` 来更改此默认行为。  `unexpected` 调用指定为 `set_unexpected` 的参数的最后一个函数。  
  
 与通过调用`set_terminate`安装的自定义终端函数不同，异常可能从`unexpFunction`中被抛出。  
  
 在多线程环境中，每个线程都是单独维护异常函数。  每个新线程需要安装自己意外的函数。  因此，每个线程都负责自己意外处理。  
  
 在当前的 C\+\+ 异常处理 Microsoft 实现中，`unexpected` 调用 `terminate` 默认调用,从不被异常处理的运行库调用。  调用 `unexpected` 而不是 `terminate`没有特定的优势。  
  
 所有的动态链接DLLs 或 EXEs 有单`set_unexpected`，即使您调用`set_unexpected`处理程序可能会被另一个替代，或者您用另外的DLL 或 EXE替代处理程序。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`set_unexpected`|\<eh.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)