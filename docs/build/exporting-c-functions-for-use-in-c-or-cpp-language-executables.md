---
title: "导出 C 函数以用于 C 或 C++ 语言可执行文件 | Microsoft Docs"
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
  - "__cplusplus 宏"
  - "导出 DLL [C++], C++ 可执行文件中的 C 函数"
  - "导出函数 [C++], C++ 可执行文件中的 C 函数"
  - "函数 [C], C 或 C++ 可执行文件和"
  - "函数 [C], 导出"
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 导出 C 函数以用于 C 或 C++ 语言可执行文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果在用 C 编写的 DLL 中有希望从 C 语言或 C\+\+ 语言模块访问的函数，则应使用 **\_\_cplusplus** 预处理器宏确定正在编译的语言，然后，如果是从 C\+\+ 语言模块使用，则用 C 链接声明这些函数。  如果使用此技术并为 DLL 提供头文件，则这些函数可以原封不动地由 C 和 C\+\+ 用户使用。  
  
 以下代码演示可由 C 和 C\+\+ 客户端应用程序使用的头文件：  
  
```  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 如果需要将 C 函数链接到 C\+\+ 可执行文件，并且函数声明头文件没有使用上面的技术，则在 C\+\+ 源文件中添加下列内容以防止编译器修饰 C 函数名：  
  
```  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## 你希望做什么？  
  
-   [使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
-   [链接规范](http://msdn.microsoft.com/zh-cn/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)