---
title: "_CrtGetReportHook | Microsoft Docs"
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
  - "_CrtGetReportHook"
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
  - "CrtGetReportHook"
  - "_CrtGetReportHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtGetReportHook 函数"
  - "_CrtGetReportHook 函数"
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtGetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索用于调试报告进行中挂接到 C 运行时的客户端自定义的报告函数 \(仅限调试版本\)。  
  
## 语法  
  
```  
_CRT_REPORT_HOOK _CrtGetReportHook( void );  
```  
  
## 返回值  
 返回当前客户端定义的报告函数。  
  
## 备注  
 `_CrtGetReportHook` 允许应用程序检索用于 C 运行时调试库报告程序中当前的报告函数。  
  
 有关使用其他运行时钩子函数并编写客户定义钩子函数的更多信息，请参见[编写调试挂钩函数](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtGetReportHook`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 对于如何使用 `_CrtSetReportHook` 的例子，请参阅 [报告](http://msdn.microsoft.com/zh-cn/f6e08c30-6bd9-459a-830a-56deec0d2051)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)