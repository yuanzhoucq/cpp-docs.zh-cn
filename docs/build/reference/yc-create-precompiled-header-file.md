---
title: "/Yc（创建预编译的头文件） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.UsePrecompiledHeader"
  - "/yc"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough"
  - "VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader"
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 创建"
  - "/Yc 编译器选项 [C++]"
  - "PCH 文件, 创建"
  - "预编译的头文件, 创建"
  - "Yc 编译器选项 [C++]"
  - "-Yc 编译器选项 [C++]"
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yc（创建预编译的头文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示编译器创建表示某一时刻的编译状态的预编译头\(.pch\)文件。  
  
## 语法  
  
```  
/Yc[filename]  
```  
  
## Arguments  
 `filename`  
 指定一个头文件 \(.h\)。  使用此参数时，编译器将对直到 .h 文件（包括该文件）的所有代码进行编译。  
  
## 备注  
 在指定 **\/Yc** 而不使用任何参数时，编译器将编译直到基源文件结尾或基文件中出现 [hdrstop](../../preprocessor/hdrstop.md) 的位置的所有代码。  得到的 .pch 文件与基源文件具有相同的基名称，除非使用 **hdrstop** 杂注或 **\/Fp** 选项指定不同的文件名。  
  
 预编译代码保存在一个文件中，该文件的名称根据用 **\/Yc** 选项指定的文件的基名称创建，且扩展名为 .pch。  还可以使用 [\/Fp（命名 .Pch 文件）](../../build/reference/fp-name-dot-pch-file.md) 选项为预编译头文件指定名称。  
  
 如果使用 **\/Yc**`filename`，编译器将编译直到指定文件（包括该文件）的所有代码，以便随后用于 **\/Yu** 选项。  
  
 如果选项 **\/Yc**`filename` 和 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)`filename` 出现在同一命令行上，并且两者都引用或暗示同一文件名，则 **\/Yc**`filename` 优先。  此功能简化了生成文件的编写。  
  
 有关预编译头的更多信息，请参见：  
  
-   [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  选择一个 .cpp 文件。  该 .cpp 文件必须 \#include 包含预编译头信息的 .h 文件。  项目的 **\/Yc** 设置可以在文件级别上重写。  
  
2.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
3.  单击**“C\/C\+\+”**文件夹。  
  
4.  单击**“预编译头”**属性页。  
  
5.  修改**“通过文件创建\/使用 PCH”**属性或**“创建\/使用预编译头”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## 示例  
 考虑下列代码：  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 使用命令 `CL /YcMYAPP.H PROG.CPP` 编译此代码时，编译器会将 AFXWIN.h、RESOURCE.h 和 MYAPP.h 的所有预处理保存在称为 MYAPP.pch 的预编译头文件中。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)