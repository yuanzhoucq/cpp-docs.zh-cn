---
title: "导入和导出 | Microsoft Docs"
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
  - "__declspec(dllimport) 关键字 [C++]"
  - "DLL [C++], 导出自"
  - "DLL [C++], 导入"
  - "导出 DLL [C++]"
  - "导入 DLL [C++]"
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 导入和导出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用两种方法将公共符号导入到应用程序中或从 DLL 导出函数：  
  
-   生成 DLL 时使用模块定义 \(.def\) 文件  
  
-   在主应用程序的函数定义中使用关键字 **\_\_declspec\(dllimport\)** 或 **\_\_declspec\(dllexport\)**  
  
## 使用 .def 文件  
 模块定义 \(.def\) 文件是包含一个或多个描述 DLL 各种特性的 Module 语句的文本文件。  如果不使用 **\_\_declspec\(dllimport\)** 或 **\_\_declspec\(dllexport\)** 导出 DLL 函数，则 DLL 需要 .def 文件。  
  
 可以使用 .def 文件[导入到应用程序中](../build/importing-using-def-files.md)或[从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)。  
  
## 使用 \_\_declspec  
 Visual C\+\+ 用 **\_\_declspec\(dllimport\)** 和 **\_\_declspec\(dllexport\)** 取代以前在 16 位版的 Visual C\+\+ 中使用的 **\_\_export** 关键字。  
  
 不使用 **\_\_declspec\(dllimport\)** 也能正确编译代码，但使用它可以使编译器生成更好的代码。  编译器之所以能够生成更好的代码，是因为它可以确定函数是否存在于 DLL 中，这使得编译器可以生成跳过间接寻址级别的代码，而这些代码通常会出现在跨 DLL 边界的函数调用中。  但是，必须使用 **\_\_declspec\(dllimport\)** 才能导入 DLL 中使用的变量。  
  
 如果有正确的 .def 文件 EXPORTS 节，则不需要 **\_\_declspec\(dllexport\)**。  添加 **\_\_declspec\(dllexport\)** 是为了提供不使用 .def 文件从 .exe 或 .dll 文件导出函数的简单方法。  
  
 Win32 可移植可执行文件格式旨在最小化为修改导入而必须访问的页数。  为此，它将所有程序的所有导入地址都放在一个称为“导入地址表”的位置。  这使得加载程序在访问这些导入时可以只修改一两页。  
  
## 你希望做什么？  
  
-   [导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)