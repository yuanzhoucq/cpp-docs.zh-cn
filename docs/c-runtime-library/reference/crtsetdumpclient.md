---
title: "_CrtSetDumpClient | Microsoft Docs"
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
  - "_CrtSetDumpClient"
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
  - "_CrtSetDumpClient"
  - "CrtSetDumpClient"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtSetDumpClient 函数"
  - "CrtSetDumpClient 函数"
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安装一个应用定义的函数来转储 `_CLIENT_BLOCK`类型的内存块（仅调试版本）。  
  
## 语法  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### 参数  
 `dumpClient`  
 新客户端自定义内存转储函数挂接到 C 运行时调试内存转储进程。  
  
## 返回值  
 返回以前定义的客户端定义的块转储函数。  
  
## 备注  
 `_CrtSetDumpClient` 函数允许应用程序挂钩它的函数到转储对象到C运行时调试内存转储进程的 `_CLIENT_BLOCK` 内存块  因此，每一次调试转储功能，如 [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 或 [\_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) 转储 `_CLIENT_BLOCK` 内存块，应用程序的转储函数也被调用。  `_CrtSetDumpClient` 提供应用程序一个简单的方法，用于检测内存泄漏和验证或报告存储在 `_CLIENT_BLOCK` 块的数据内容。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtSetDumpClient` 的调用。  
  
 `_CrtSetDumpClient` 函数安装在 `dumpClient` 指定的新的应用自定义转储函数，并返回之前自定义的转储函数。  客户端块转储函数的示例如下所示：  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` 参数是一个内存块用户数据开始的指针，并 `blockSize` 指定按比特分配给内存块的大小。  客户端块转储函数必须返回 `void`。  传递给 `_CrtSetDumpClient` 的客户端转储函数指针是 `_CRT_DUMP_CLIENT` 类型的，在 Crtdbg.h 定义：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 有关更多关于操作 `_CLIENT_BLOCK` 类型内存块的函数，请参阅 [客户端块挂钩函数](../Topic/Client%20Block%20Hook%20Functions.md)。  [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) 函数可以被用来返回关于块类和子类型的信息。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtSetDumpClient`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)