---
title: "_CrtCheckMemory | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtCheckMemory"
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
  - "CrtCheckMemory"
  - "_CrtCheckMemory"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtCheckMemory 函数"
  - "CrtCheckMemory 函数"
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtCheckMemory
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定分配在调试堆得内存块的完整性\(仅限调试版本\)。  
  
## 语法  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## 返回值  
 如果成功，则 `_CrtCheckMemory` 返回 TRUE；否则函数返回 FALSE。  
  
## 备注  
 `_CrtCheckMemory` 函数通过验证基本堆和检查每个内存块来确定调试堆管理器分配的内存。  如果在基础堆、调试头信息或是重写缓冲区中遇到错误或是内存不一致，则 `_CrtCheckMemory` 生成描述错误情况信息的调试报告。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtCheckMemory` 的调用。  
  
 通过使用[\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 设置[\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志的位字段来控制`_CrtCheckMemory` 的行为。  打开 **\_CRTDBG\_CHECK\_ALWAYS\_DF** 位字段导致每次请求内存分配操作就调用 `_CrtCheckMemory` 。  虽然此方法会减慢执行，但是有利于快速查看错误。  关闭 **\_CRTDBG\_ALLOC\_MEM\_DF** 位字段导致 `_CrtCheckMemory` 不能核实堆并且立即返回 **TRUE**。  
  
 因为函数返回 **TRUE** 或 **FALSE**， 所以能传递一个[\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏命令来创建一个简单的调试错误处理机制。  如果在堆检测到损坏，下面的示例会造成断言失败：  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 有关`_CrtCheckMemory` 可用在其它调试函数中的详细信息, 请参阅[堆状态报告函数](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions).  对于内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtCheckMemory`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 对于如何使用 `_CrtCheckMemory` 的例子，请参阅 [crt\_dbg1](http://msdn.microsoft.com/zh-cn/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## .NET Framework 等效项  
 [System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)