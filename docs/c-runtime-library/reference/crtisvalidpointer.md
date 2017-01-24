---
title: "_CrtIsValidPointer | Microsoft Docs"
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
  - "_CrtIsValidPointer"
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
  - "CrtlsValidPointer"
  - "_CrtIsValidPointer"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtIsValidPointer 函数"
  - "CrtIsValidPointer 函数"
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtIsValidPointer
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

验证指针是否不为 Null。  在 Visual Studio 2010 之前的 C 运行时库版本中，验证指定的内存范围对于读取和写入是否有效（仅限调试版本）。  
  
## 语法  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### 参数  
 地址  
 指向内存范围的开始位置以进行有效性测试。  
  
 `size`  
 指定的内存范围大小（以字节为单位）。  
  
 access  
 确定对内存范围的读\/写访问能力。  
  
## 返回值  
 如果指定的指针不为 Null，则 `_CrtIsValidPointer` 返回 TRUE。  在 Visual Studio 2010 之前的 CRT 库版本中，如果内存范围对于指定的一个或多个操作有效，则将返回 TRUE。  否则，该函数将返回 FALSE。  
  
## 备注  
 从 Visual Studio 2010 中的 CRT 库开始，大小和访问参数将被忽略，并且 `_CrtIsValidPointer` 仅验证指定的地址是否不为 Null。  由于可轻松自行执行此测试，因此不建议使用此函数。  在 Visual Studio 2010 之前的版本中，该函数验证从 `address` 开始并扩展了 `size` 个字节的内存范围对于指定的一个或多个可访问操作是否有效。  当将 `access` 设置为 TRUE 时，内存范围对于读取和写入都有效。  当 `access` 为 FALSE 时，内存范围仅对于读取有效。  未定义 [\_DEBUG](../../c-runtime-library/debug.md) 时，将在预处理过程中删除对 `_CrtIsValidPointer` 的调用。  
  
 因为此函数返回 TRUE 或 FALSE，因此可将它传递到一个 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。  如果内存范围对于读取和写入操作都无效，则以下示例将导致断言失败：  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 有关如何将 `_CrtIsValidPointer` 与其他调试函数和宏一起使用的详细信息，请参阅[用于报告的宏](../Topic/Macros%20for%20Reporting.md)。  有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtIsValidPointer`|\<crtdbg.h\>|  
  
 `_CrtIsValidPointer` 是 Microsoft 扩展。  有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 请参阅 [\_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 主题的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)