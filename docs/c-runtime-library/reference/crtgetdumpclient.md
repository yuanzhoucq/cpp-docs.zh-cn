---
title: "_CrtGetDumpClient | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtGetDumpClient"
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
  - "CrtGetDumpClient"
  - "_CrtGetDumpClient"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtGetDumpClient 函数"
  - "CrtGetDumpClient 函数"
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _CrtGetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了转储 `_CLIENT_BLOCK` 类型内存块，检索当前自定义的应用程序函数。  
  
## 语法  
  
```  
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );  
```  
  
## 返回值  
 返回当前转储实例。  
  
## 备注  
 为了转储 C 运行时调试内存转储进程中保存在 `_CLIENT_BLOCK` 内存块中的对象， `_CrtGetDumpClient` 函数检索当前挂钩函数。  
  
 有关使用其他运行时钩子函数并编写客户定义钩子函数的更多信息，请参见[编写调试挂钩函数](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtGetDumpClient`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)