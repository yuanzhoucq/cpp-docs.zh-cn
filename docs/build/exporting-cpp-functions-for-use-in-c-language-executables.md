---
title: "导出 C++ 函数以用于 C 语言可执行文件 | Microsoft Docs"
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
  - "导出 DLL [C++], C 可执行文件中的 C++ 函数"
  - "导出函数 [C++], C 可执行文件中的 C++ 函数"
  - "函数 [C++], C 可执行文件中的 C++ 函数"
  - "函数 [C++], 导出"
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 导出 C++ 函数以用于 C 语言可执行文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果在用 C\+\+ 编写的 DLL 中有希望从 C 语言模块访问的函数，应使用 C 链接而不是 C\+\+ 链接来声明这些函数。  除非另外指定，C\+\+ 编译器使用 C\+\+ 类型安全命名约定（也称作名称修饰）和 C\+\+ 调用约定（使用此调用约定从 C 调用会很困难）。  
  
 若要指定 C 链接，请为函数声明指定 **extern** "**C**"。  例如：  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## 你希望做什么？  
  
-   [使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
-   [链接规范](http://msdn.microsoft.com/zh-cn/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)