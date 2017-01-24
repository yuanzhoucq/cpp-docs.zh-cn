---
title: "从 DLL 导出 | Microsoft Docs"
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
  - "DLL 导出 [C++]"
  - "DLL [C++], 导出自"
  - "导出 DLL [C++]"
  - "导出 DLL [C++], 关于从 DLL 导出"
  - "导出函数 [C++], DLL（导出自）"
  - "导出表 [C++]"
  - "函数 [C++], 导出"
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 从 DLL 导出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

.DLL 文件的布局与 .exe 文件非常相似，但有一个重要的差异：DLL 文件包含导出表。  导出表包含 DLL 导出到其他可执行文件的每个函数的名称。  这些函数是 DLL 中的入口点；只有导出表中的函数可由其他可执行文件访问。  DLL 中的任何其他函数都是 DLL 私有的。  通过使用带 \/EXPORTS 选项的 [Dumpbin](../build/reference/dumpbin-reference.md) 工具，可以查看 DLL 的导出表。  
  
 有两种从 DLL 导出函数的方法：  
  
-   在生成 DLL 时，创建一个模块定义 \(.def\) 文件并使用该 .def 文件。  如果希望[按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)，则请使用此方法。  
  
-   在函数的定义中使用 **\_\_declspec\(dllexport\)** 关键字。  
  
 用上述任何方法导出函数时，确保使用 [\_\_stdcall](../cpp/stdcall.md) 调用约定。  
  
## 你希望做什么？  
  
-   [使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [导入到应用程序中](../build/importing-into-an-application.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## 请参阅  
 [导入和导出](../build/importing-and-exporting.md)