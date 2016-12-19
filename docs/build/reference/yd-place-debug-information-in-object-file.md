---
title: "/Yd（将调试信息放在对象文件中） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yd 编译器选项 [C++]"
  - "调试 [C++], 调试信息文件"
  - "Yd 编译器选项 [C++]"
  - "-Yd 编译器选项 [C++]"
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yd（将调试信息放在对象文件中）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当与 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) 选项一起使用时，将完整的调试信息放在从预编译头 \(.pch\) 文件创建的所有对象文件中。  已否决。  
  
## 语法  
  
```  
/Yd  
```  
  
## 备注  
 已弃用 **\/Yd**；[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 现在支持将多个对象写入单个 .pdb 文件中，并改用 **\/Zi**。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
 除非需要分发包含调试信息的库，否则请使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 选项，而不要使用 **\/Z7** 和 **\/Yd**。  
  
 仅在发布包含调试信息的库时才需要在每个 .obj 文件中存储完整的调试信息。  它降低了编译速度，并需要大量的磁盘空间。  当使用 **\/Yc** 和 **\/Z7** 而不使用 **\/Yd** 时，编译器将公共调试信息存储在从 .pch 文件创建的第一个 .obj 文件中。  编译器不将此信息插入到随后从 .pch 文件创建的 .obj 文件中；它插入对此信息的交叉引用。  不论有多少 .obj 文件使用 .pch 文件，只有一个 .obj 文件包含公共调试信息。  
  
 虽然这种默认行为导致较少的生成时间并降低磁盘空间要求，但当细微更改要求重新生成包含公共调试信息的 .obj 文件时，它并不可取。  在这种情况下，编译器必须重新生成所有包含对原始 .obj 文件的交叉引用的 .obj 文件。  而且，如果公共 .pch 文件由不同项目使用，则很难依靠对单个 .obj 文件的交叉引用。  
  
 有关预编译头的更多信息，请参见：  
  
-   [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 示例  
 假设有两个基文件 F.cpp 和 G.cpp，每个均包含这些 **\#include** 语句：  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 下列命令创建预编译头文件 ETC.pch 和对象文件 F.obj：  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 对象文件 F.obj 包含 WINDOWS.h 和 ETC.h（和它们包含的任何其他头文件）的类型信息和符号信息。  现在可以使用预编译头 ETC.pch 编译源文件 G.cpp：  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 对象文件 G.obj 不包含预编译头的调试信息，而只引用 F.obj 文件中的此信息。  请注意，必须与 F.obj 文件链接。  
  
 如果预编译头不是用 **\/Z7** 编译的，仍可以在以后使用 **\/Z7** 编译时使用它。  然而，调试信息被放在当前对象文件中，并且调试器不能使用在预编译头中定义的函数和类型的局部符号。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)