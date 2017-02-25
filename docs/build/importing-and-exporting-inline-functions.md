---
title: "导入和导出内联函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 导出自"
  - "DLL [C++], 导入"
  - "导出函数 [C++], 内联函数"
  - "函数 [C++], 导出"
  - "函数 [C++], 导入"
  - "导入函数 [C++]"
  - "导入内联函数 [C++]"
  - "内联函数 [C++], 导出"
  - "内联函数 [C++], 导入"
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 导入和导出内联函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以将导入函数定义为内联。  其效果与将标准函数定义为内联大致相同；函数调用扩展到内联代码中，这一点非常像宏。  这主要用作支持 DLL 中可能内联某些成员函数以提高效率的 C\+\+ 类的一种手段。  
  
 导入内联函数的一项功能是您可以在 C\+\+ 中获取其地址。  编译器返回驻留在 DLL 中的内联函数副本的地址。  导入内联函数的另一项功能是您可以初始化导入函数的静态局部数据，这一点与全局导入数据不同。  
  
> [!CAUTION]
>  提供导入的内联函数时要小心，因为它们可能会导致版本冲突。  内联函数扩展到应用程序代码中；因此，如果以后重写内联函数，除非重新编译应用程序本身，否则内联函数不会被更新。（通常，不用重新生成使用 DLL 函数的应用程序就可以更新 DLL 函数。）  
  
## 你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## 请参阅  
 [导入和导出](../build/importing-and-exporting.md)