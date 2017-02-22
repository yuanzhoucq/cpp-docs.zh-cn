---
title: "使用 __declspec(dllexport) 从 DLL 导出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dllexport"
  - "__declspec"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllexport) 关键字 [C++]"
  - "导出指令 [C++]"
  - "导出 DLL [C++], __declspec(dllexport) 关键字"
  - "名称 [C++], DLL 导出"
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 使用 __declspec(dllexport) 从 DLL 导出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 在 Visual C\+\+ 的 16 位编译器版本中引入了 **\_\_export**，使编译器得以自动生成导出名并将它们放到一个 .lib 文件中。  然后，此 .lib 文件就可以像静态 .lib 那样用于与 DLL 链接。  
  
 在更新的编译器版本中，可以使用 **\_\_declspec\(dllexport\)** 关键字从 DLL 导出数据、函数、类或类成员函数。  **\_\_declspec\(dllexport\)** 会将导出指令添加到对象文件中，因此您不需要使用 .def 文件。  
  
 当尝试导出 C\+\+ 修饰函数名时，这种便利最明显。  由于对名称修饰没有标准规范，因此导出函数的名称在不同的编译器版本中可能有所变化。  如果使用 **\_\_declspec\(dllexport\)**，仅当解决任何命名约定更改时才必须重新编译 DLL 和依赖 .exe 文件。  
  
 许多导出指令（如序号、NONAME 和 PRIVATE）只能在 .def 文件中创建，并且必须使用 .def 文件来指定这些特性。  不过，在 .def 文件的基础上另外使用 **\_\_declspec\(dllexport\)** 不会导致生成错误。  
  
 若要导出函数，**\_\_declspec\(dllexport\)** 关键字必须出现在调用约定关键字的左边（如果指定了关键字）。  例如：  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 若要导出类中的所有公共数据成员和成员函数，关键字必须出现在类名的左边，如下所示：  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` 不能应用于具有 `__clrcall` 调用约定的函数。  
  
 生成 DLL 时，通常创建一个包含正在导出的函数原型和\/或类的头文件，并将 **\_\_declspec\(dllexport\)** 添加到头文件中的声明中。  若要提高代码的可读性，请为 **\_\_declspec\(dllexport\)** 定义一个宏并对正在导出的每个符号使用该宏：  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **\_\_declspec\(dllexport\)** 将函数名存储在 DLL 的导出表中。  如果希望优化表的大小，请参见[按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
> [!NOTE]
>  将 DLL 源代码从 Win16 移植到 Win32 时，请用 **\_\_declspec\(dllexport\)** 替换 **\_\_export** 的每个实例。  
  
 作为参考，请在 Win32 Winbase.h 头文件中搜索。  它包含 **\_\_declspec\(dllimport\)** 的用法示例。  
  
## 你希望做什么？  
  
-   [使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [\_\_declspec 关键字](../cpp/declspec.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)