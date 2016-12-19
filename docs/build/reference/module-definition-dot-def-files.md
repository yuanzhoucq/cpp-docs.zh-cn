---
title: "模块定义 (.Def) 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def 文件"
  - "def 文件"
  - "模块定义文件"
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 模块定义 (.Def) 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模块定义 \(.def\) 文件为链接器提供有关被链接程序的导出、特性及其他方面的信息。  生成 DLL 时，.def 文件最有用。  由于存在可代替模块定义语句使用的[链接器选项](../../build/reference/linker-options.md)，通常不需要 .def 文件。  也可以将 [\_\_declspec\(dllexport\)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) 用作指定导出函数的手段。  
  
 在链接器阶段可以使用 [\/DEF（指定模块定义文件）](../../build/reference/def-specify-module-definition-file.md)链接器选项调用 .def 文件。  
  
 如果生成的 .exe 文件没有导出，使用 .def 文件将使输出文件较大并降低加载速度。  
  
 有关示例，请参见[使用 DEF 文件从 DLL 导出](../../build/exporting-from-a-dll-using-def-files.md)。  
  
 有关更多信息，请参见下列章节：  
  
-   [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [NAME](../../build/reference/name-c-cpp.md)  
  
-   [SECTIONS](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [VERSION](../../build/reference/version-c-cpp.md)  
  
-   [保留字](../../build/reference/reserved-words.md)  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/zh-cn/56a3bb8f-0181-4989-bab4-a07ba950ab08)