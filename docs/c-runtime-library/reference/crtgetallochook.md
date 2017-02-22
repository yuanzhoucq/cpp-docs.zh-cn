---
title: "_CrtGetAllocHook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtGetAllocHook"
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
  - "CrtGetAllocHook"
  - "_CrtGetAllocHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtGetAllocHook 函数"
  - "CrtGetAllocHook 函数"
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtGetAllocHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索当前客户端定义的分配函数以便连接到 C 运行时调试内存的分配过程 \(仅限调试版本\)。  
  
## 语法  
  
```  
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );  
```  
  
## 返回值  
 返回当前定义的分配挂钩函数。  
  
## 备注  
 `_CrtGetAllocHook`为 C 运行时调试库内存的分配过程检索当前客户端定义的应用程序分配钩子函数。  
  
 有关使用其他运行时钩子函数并编写客户定义钩子函数的更多信息，请参见[编写调试挂钩函数](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtGetAllocHook`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetAllocHook](../../c-runtime-library/reference/crtsetallochook.md)