---
title: "使用 __declspec(dllimport) 导入到应用程序中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 关键字 [C++]"
  - "导入 DLL [C++], __declspec(dllimport)"
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 __declspec(dllimport) 导入到应用程序中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果一个程序使用 DLL 定义的公共符号，就说该程序是在导入公共符号。  为使用 DLL 生成的应用程序创建头文件时，在公共符号的声明上使用 **\_\_declspec\(dllimport\)**。  不论是用 .def 文件导出还是用 **\_\_declspec\(dllexport\)** 关键字导出，**\_\_declspec\(dllimport\)** 关键字均有效。  
  
 若要提高代码的可读性，请为 **\_\_declspec\(dllimport\)** 定义一个宏，然后使用此宏声明每个导入的符号：  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 在函数声明上使用 **\_\_declspec\(dllimport\)** 是可选操作，但如果使用此关键字，编译器将生成更有效的代码。  但是，为使导入的可执行文件能够访问 DLL 的公共数据符号和对象，必须使用 **\_\_declspec\(dllimport\)**。  请注意，DLL 的用户仍然需要与导入库链接。  
  
 对 DLL 和客户端应用程序可以使用相同的头文件。  为此，请使用特殊的预处理器符号来指示是生成 DLL 还是生成客户端应用程序。  例如：  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## 你希望做什么？  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## 请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)