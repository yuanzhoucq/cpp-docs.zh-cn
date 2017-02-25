---
title: "/Gd、/Gr、/Gv、/Gz（调用约定） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gr"
  - "/Gv"
  - "/gz"
  - "/Gd"
  - "VC.Project.VCCLCompilerTool.CallingConvention"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gd 编译器选项 [C++]"
  - "/Gr 编译器选项 [C++]"
  - "/Gv 编译器选项 [C++]"
  - "/Gz 编译器选项 [C++]"
  - "Gd 编译器选项 [C++]"
  - "-Gd 编译器选项 [C++]"
  - "Gr 编译器选项 [C++]"
  - "-Gr 编译器选项 [C++]"
  - "Gv 编译器选项 [C++]"
  - "-Gv 编译器选项 [C++]"
  - "Gz 编译器选项 [C++]"
  - "-Gz 编译器选项 [C++]"
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /Gd、/Gr、/Gv、/Gz（调用约定）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些选项用于确定函数参数入栈的顺序，调用结束时调用方函数或被调用函数是否从堆栈中移除参数，以及编译器用来标识各个函数的名称修饰约定。  
  
## 语法  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## 备注  
 **\/Gd** 为默认设置，为除 C\+\+ 成员函数和标记为 [\_\_stdcall](../../cpp/stdcall.md)、[\_\_fastcall](../../cpp/fastcall.md) 或 [\_\_vectorcall](../../cpp/vectorcall.md) 的函数以外的所有函数指定 [\_\_cdecl](../../cpp/cdecl.md) 调用约定。  
  
 **\/Gr** 为除 C\+\+ 成员函数和名为 `main` 的函数以及标记为 `__cdecl`、`__stdcall` 或 `__vectorcall` 的函数以外的所有函数指定 `__fastcall` 调用约定。  所有 `__fastcall` 函数必须具有原型。  此调用约定只能用于面向 x86 的编译器，而对于面向其他体系结构的编译器，将忽略此调用约定。  
  
 **\/Gz** 为除 C\+\+ 成员函数和名为 `main` 的函数以及标记为 `__cdecl`、`__fastcall` 或 `__vectorcall` 的函数以外的所有函数指定 `__stdcall` 调用约定。  所有 `__stdcall` 函数必须具有原型。  此调用约定只能用于面向 x86 的编译器，而对于面向其他体系结构的编译器，将忽略此调用约定。  
  
 **\/Gv** 为所有函数（除了 C\+\+ 成员函数、名为主功能的函数、带有 `vararg` 变量参数列表的函数或者标记有冲突的 `__cdecl`、 `__stdcall` 或  `__fastcall` 属性的函数）指定了 `__vectorcall` 调用约定。  此调用约定只能用于支持 \/arch:SSE2 及以上的 x86 和 x64 体系结构，而对于面向 ARM 体系结构的编译器，将忽略此调用约定。  
  
 参数个数可变的函数必须标记为 `__cdecl`。  
  
 **\/Gd**、**\/Gr**、**\/Gv** 和 **\/Gz** 与 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 不兼容。  
  
> [!NOTE]
>  对于 x86 处理器，默认情况下 C\+\+ 成员函数使用 [\_\_thiscall](../../cpp/thiscall.md)。  
  
 对于所有处理器，显式标记为 `__cdecl`、`__fastcall`、 `__vectorcall` 或 `__stdcall` 的成员函数采用指定的调用约定（如果在该体系结构上没有将其忽略）。  采用的参数个数可变的成员函数总是使用 `__cdecl` 调用约定。  
  
 这些编译器选项对 C\+\+ 方法和函数的名称修饰无效。  除非声明为 `extern "C"`，否则 C\+\+ 方法和函数将使用不同的名称修饰方案。  有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。  
  
 有关调用约定的更多信息，请参见 [调用约定](../../cpp/calling-conventions.md)。  
  
## \_\_cdecl 细节  
 在 x86 处理器上，所有函数参数都在堆栈上从右向左传递。  在 ARM 和 x64 体系结构，有些参数通过注册传递，其余内容在堆栈上从右向左传递。  调用例程在堆栈中弹出参数。  
  
 对于 C，`__cdecl` 命名约定使用前面带下划线 \(`_`\) 的函数名；不执行任何大小写转换。  除非声明为 `extern "C"`，否则 C\+\+ 函数将使用不同的名称修饰方案。  有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。  
  
## \_\_fastcall 细节  
 `__fastcall` 函数的一些参数传入寄存器（对于 x86 处理器，为 ECX 和 EDX），而其余的参数按从右向左的顺序入栈。  被调用例程在返回之前从堆栈中弹出这些参数。  通常，**\/Gr** 将缩短执行时间。  
  
> [!NOTE]
>  在对用内联程序集语言编写的任何函数使用 `__fastcall` 调用约定时，一定要小心。  您对寄存器的使用可能与编译器对它们的使用发生冲突。  
  
 对于 C，`__fastcall` 命名约定使用前面带“at”符 \(`@`\) 的函数名，后跟函数参数大小（以字节为单位）。  不执行任何大小写转换。  编译器使用此命名约定模板：  
  
```c  
@function_name@number  
```  
  
 当您使用 `__fastcall` 命名约定时，请使用标准包含文件。  否则，您将获取无法解析的外部引用。  
  
## \_\_stdcall 细节  
 `__stdcall` 函数的参数被从右到左推送到堆栈上，被调用函数在返回之前从堆栈中弹出这些参数。  
  
 对于 C，`__stdcall` 命名约定使用前面带下划线 \(`_`\) 的函数名，后跟“at”符 \(@\) 和函数的参数大小（以字节为单位）。  不执行任何大小写转换。  编译器使用此命名约定模板：  
  
```c  
_functionname@number  
```  
  
## \_\_vectorcall 特定  
 `__vectorcall` 函数的整数参数由值传递，共使用两个（在 x86 上）或四个（在 x64 上）整数寄存器，六个浮点和检测值 XMM 寄存器，剩下的参数在堆栈上从右向左传递。  所调用的函数会在返回之前清理堆栈。  在 XMM0 中返回向量和浮点返回值。  
  
 对于 C，`__vectorcall` 命名约定使用后跟两个“at”符 \(@@\) 的函数名以及函数参数大小（以字节为单位）。  不执行任何大小写转换。  编译器使用此命名约定模板：  
  
```c  
functionname@@number  
```  
  
### To set this compiler option in the Visual Studio development environment  
  
1.  Open the project's **Property Pages** dialog box.  For details, see [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md).  
  
2.  Select the **C\/C\+\+** folder.  
  
3.  Select the **Advanced** property page.  
  
4.  Modify the **Calling Convention** property.  
  
### To set this compiler option programmatically  
  
-   See <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)