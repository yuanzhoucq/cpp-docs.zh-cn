---
title: "/DEBUGTYPE（调试信息选项） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/debugtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEBUGTYPE 链接器选项"
  - "DEBUGTYPE 链接器选项"
  - "-DEBUGTYPE 链接器选项"
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# /DEBUGTYPE（调试信息选项）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/DEBUGTYPE 选项指定 \/DEBUG 选项生成的调试信息的类型。  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## 参数  
 CV  
 指示链接器针对 PDB 文件中的符号、行号和其他对象编译信息发出调试信息。  默认情况下，如果指定了 **\/DEBUG**，而未指定 **\/DEBUGTYPE**，此选项将处于启用状态。  
  
 PDATA  
 指示链接器向 PDB 文件中的调试流信息添加 .pdata 和 .xdata 条目。  默认情况下，如果同时指定了 **\/DEBUG** 和 **\/DRIVER** 选项，此选项将处于启用状态。  如果单独指定 **\/DEBUGTYPE:PDATA**，链接器将自动在 PDB 文件中包含调试符号。  如果指定 **\/DEBUGTYPE:PDATA,FIXUP**，链接器不会在 PDB 文件中包含调试符号。  
  
 FIXUP  
 指示链接器向 PDB 文件中的调试流信息添加重定位表条目。  默认情况下，如果同时指定了 **\/DEBUG** 和 **\/PROFILE** 选项，此选项将处于启用状态。  如果指定 **\/DEBUGTYPE:FIXUP** 或 **\/DEBUGTYPE:FIXUP,PDATA**，链接器不会在 PDB 文件中包含调试符号。  
  
 **\/DEBUGTYPE** 的参数可按任意顺序进行组合（彼此之间用逗号分隔）。  **\/DEBUGTYPE** 选项及其参数均不区分大小写。  
  
## 备注  
 使用 **\/DEBUGTYPE** 选项指定在调试流中包含重定位表数据或 .pdata 和 .xdata 标头信息。  这导致链接器包含有关破坏内核模式代码时内核调试程序中可见的用户模式代码的信息。  要使调试符号在指定 **FIXUP** 时可用，请包含 **CV** 参数。  
  
 要在用户模式下调试代码（对于应用程序很常见），无需 **\/DEBUGTYPE** 选项。  默认情况下，用于指定调试输出的编译器开关（[\/Z7、\/Zi、\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)）会发出 Visual Studio 调试器所需的所有信息。  使用 **\/DEBUGTYPE:PDATA** 或 **\/DEBUGTYPE:CV,PDATA,FIXUP** 可调试由用户模式组件和内核模式组件组合而成的代码，比如设备驱动程序的配置应用。  有关内核模式调试程序的详细信息，请参阅[适用于 Windows 的调试工具（WinDbg、KD、CDB、NTSD）](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## 请参阅  
 [\/DEBUG（生成调试信息）](../../build/reference/debug-generate-debug-info.md)   
 [\/DRIVER（Windows NT 内核模式驱动程序）](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [\/PROFILE（性能工具分析器）](../../build/reference/profile-performance-tools-profiler.md)   
 [适用于 Windows 的调试工具（WinDbg、KD、CDB、NTSD）](http://go.microsoft.com/fwlink/p?LinkID=285651)