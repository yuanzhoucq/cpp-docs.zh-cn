---
title: "/GL（全程序优化） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gl"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GL 编译器选项 [C++]"
  - "GL 编译器选项 [C++]"
  - "-GL 编译器选项 [C++]"
  - "全程序优化和 C++ 编译器"
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /GL（全程序优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用全程序优化。  
  
## 语法  
  
```  
/GL[-]  
```  
  
## 备注  
 全程序优化允许编译器用有关程序中所有模块的信息执行优化。  如果不执行全程序优化，则基于每个模块 \(compiland\) 执行优化。  
  
 默认情况下，权全程序优化是关闭的，因此必须显式地启用它。  但是，也可以用 **\/GL\-** 显式地禁用它。  
  
 使用有关所有模块的信息，编译器能够：  
  
-   跨越函数边界优化寄存器的使用。  
  
-   更好地跟踪对全局数据的修改，允许减少加载和存储的数目。  
  
-   更好地跟踪可能由取消指针引用所修改的项组，减少加载和存储的数目。  
  
-   在模块中内联某个函数，即使该函数在另一个模块中定义。  
  
 用 **\/GL** 生成的 .obj 文件将不可用于 [EDITBIN](../../build/reference/editbin-reference.md) 和 [DUMPBIN](../../build/reference/dumpbin-reference.md) 等链接器实用工具。  
  
 如果用 **\/GL** 和 [\/c](../../build/reference/c-compile-without-linking.md) 编译程序，应使用 \/LTCG 链接器选项创建输出文件。  
  
 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 无法与 **\/GL** 一起使用。  
  
 以后的 Visual C\+\+ 版本可能无法读取用当前版本中的 **\/GL** 生成的文件格式。  不应提供由用 **\/GL** 生成的 .obj 文件组成的 .lib 文件，除非您永远愿意为希望用户使用的所有 Visual C\+\+ 版本提供 .lib 文件的副本。  
  
 用 **\/GL** 生成的 .obj 文件和预编译的头文件不应该用于生成 .lib 文件，除非将在生成 **\/GL** .obj 文件的同一计算机上链接此 .lib 文件。  链接时需要 .obj 文件的预编译头文件中的信息。  
  
 有关优化随和全程序优化限制的更多信息，请参见 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。**\/GL** 还支持按配置优化可用；参见 \/LTCG。按配置优化进行编译时，如果希望函数按配置优化排序，则必须使用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 或隐含使用 \/Gy 的编译器选项进行编译。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  有关如何在开发环境中指定 **\/GL** 的信息，请参见 [\/LTCG（链接时代码生成）](../../build/reference/ltcg-link-time-code-generation.md)。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)