---
title: "_CrtDbgBreak | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtDbgBreak"
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
  - "_CrtDbgBreak"
  - "CrtDbgBreak"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtDbgBreak 函数"
  - "CrtDbgBreak 函数"
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtDbgBreak
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置特定行代码的断点。\(仅限在调试模式下使用。\)  
  
## 语法  
  
```  
void _CrtDbgBreak( void );  
```  
  
## 返回值  
 没有返回值。  
  
## 备注  
 `_CrtDbgBreak` 函数在函数所在代码的特定行设置调试断点。  该函数仅在调试模式下使用，并依赖于`_DEBUG`之前的定义。  
  
 有关使用其他 hook\-capable运行时函数和写自己的客户端定义的挂钩函数相关信息，请看[Writing Your Own Debug Hook Functions](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtDbgBreak`|\<CRTDBG.h\>|  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_\_debugbreak](../../intrinsics/debugbreak.md)