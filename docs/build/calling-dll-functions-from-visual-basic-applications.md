---
title: "从 Visual Basic 应用程序调用 DLL 函数 | Microsoft Docs"
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
  - "__stdcall 关键字 [C++]"
  - "从 VB 应用程序调用 DLL 函数 [C++]"
  - "DLL 函数 [C++]"
  - "DLL 函数 [C++], 调用"
  - "DLL [C++], 调用"
  - "函数调用 [C++], DLL 函数"
  - "函数 [C++], 从 Visual Basic 中调用 DLL 函数"
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 从 Visual Basic 应用程序调用 DLL 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为使 Visual Basic 应用程序（或使用 Pascal 或 Fortran 等其他语言的应用程序）可以调用 C\/C\+\+ DLL 中的函数，必须使用正确的调用约定导出函数，但不要让编译器进行任何名称修饰。  
  
 `__stdcall` 为函数创建正确的调用约定（被调用函数清理堆栈，而参数从右向左传递），但以不同的方式修饰函数名。  因此，当在 DLL 中的导出函数上使用 **\_\_declspec\(dllexport\)** 时，修饰名被导出。  
  
 `__stdcall` 名称修饰用下划线 \(\_\) 作为符号名的前缀，并在符号的后面追加一个 @ 符，@ 符后是参数列表中的字节数（所需的堆栈空间）。  因此，函数声明为：  
  
```  
int __stdcall func (int a, double b)  
```  
  
 其修饰名为：  
  
```  
_func@12  
```  
  
 C 调用约定 \(`__cdecl`\) 将该名称修饰为 `_func`。  
  
 若要获取修饰名，请使用 [\/MAP](../build/reference/map-generate-mapfile.md)。  使用 **\_\_declspec\(dllexport\)** 将完成下列工作：  
  
-   如果函数是用 C 调用约定 \(**\_cdecl**\) 导出的，则它在导出名称时抽出前导下划线 \(\_\)。  
  
-   如果函数不是用 C 调用约定（例如，`__stdcall`）导出的，则它导出修饰名。  
  
 由于没有办法重写堆栈清理发生的位置，因此必须使用 `__stdcall`。  若要使用 `__stdcall` 取消修饰名，必须通过在 .def 文件的 EXPORTS 节中使用别名来指定它们。  如以下函数声明所示：  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 在 .DEF 文件中：  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 对于将由用 Visual Basic 编写的程序调用的 DLL，在 .def 文件中需要使用本主题介绍的别名技术。  如果在 Visual Basic 程序中完成了别名，则不需要在 .def 文件中使用别名。  在 Visual Basic 程序中，这可以通过将别名子句添加到 [Declare](../Topic/Declare%20Statement.md) 语句来完成。  
  
## 您想进一步了解什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)