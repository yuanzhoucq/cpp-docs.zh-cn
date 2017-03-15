---
title: "/Yu（使用预编译的头文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 使用现有的项"
  - "/Yu 编译器选项 [C++]"
  - "PCH 文件, 使用现有的项"
  - "预编译的头文件, 使用现有的项"
  - "Yu 编译器选项 [C++]"
  - "-Yu 编译器选项 [C++]"
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Yu（使用预编译的头文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示编译器在当前编译中使用现有预编译头\(.pch\)文件。  
  
## 语法  
  
```  
/Yu[filename]  
```  
  
## Arguments  
 *filename*  
 头文件的名称，它包含在使用 **\#include** 预处理器指令的源文件中。  
  
## 备注  
 对于创建预编译头的 **\/Yc** 选项和任何随后指示使用预编译头的 **\/Yu** 选项，包含文件的名称必须相同。  
  
 对于 **\/Yc**，`filename` 指定预编译停止的位置；编译器预编译直到 `filename` 的所有代码，并使用包含文件的基名称和 .pch 扩展名对得到的预编译头进行命名。  
  
 该 .pch 文件必须是使用 **\/Yc** 创建的。  
  
 编译器将所有在 .h 文件之前出现的代码视为已经过预编译。  它刚好跳到与 .h 文件关联的 **\#include** 指令之外，使用 .pch 文件中包含的代码，然后编译 `filename` 之后的所有代码。  
  
 在命令行上，**\/Yu** 和 `filename` 之间不允许存在空格。  
  
 如果指定 **\/Yu** 选项但不带文件名，则源程序必须包含指定预编译头（.pch 文件）的文件名的 [\#pragma hdrstop](../../preprocessor/hdrstop.md) 杂注。  在这种情况下，编译器将使用由 [\/Fp（命名 .Pch 文件）](../../build/reference/fp-name-dot-pch-file.md) 命名的预编译头（.pch 文件）。  编译器跳到该杂注所在的位置，从由杂注指定的预编译头文件还原编译状态，然后只编译杂注后面的代码。  如果 **\#pragma hdrstop** 没有指定文件名，编译器将查找其名称从扩展名为 .pch 的源文件的基名称派生的文件。  还可以使用 **\/Fp** 选项指定不同的 .pch 文件。  
  
 如果指定 **\/Yu** 选项但不带文件名，且未能指定 **hdrstop** 杂注，则生成错误信息，且编译不成功。  
  
 如果 **\/Yc**`filename` 和  **\/Yu**`filename` 选项出现在同一命令行上，并且引用同一文件名，则 **\/Yc**`filename` 优先，对直到命名文件（包含该文件）的所有代码进行预编译。  此功能简化了生成文件的编写。  
  
 由于 .pch 文件包含的信息涉及计算机环境以及程序的内存地址，因此，只应在创建 pch 文件的计算机上使用该文件。  
  
 有关预编译头的更多信息，请参见：  
  
-   [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  在项目中的 .cpp 文件中指定 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)。  
  
2.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
3.  单击**“C\/C\+\+”**文件夹。  
  
4.  单击**“预编译头”**属性页。  
  
5.  修改**“通过文件创建\/使用 PCH”**属性或**“创建\/使用预编译头”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## 示例  
 如果下列代码：  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 使用命令行 `CL /YuMYAPP.H PROG.CPP` 进行编译，则编译器不处理这三个 include 语句，但使用 MYAPP.pch 中的预编译代码，从而节省了用于预处理所有这三个文件（以及它们可能包含的任何文件）的时间。  
  
 可以将 [\/Fp（命名 .Pch 文件）](../../build/reference/fp-name-dot-pch-file.md) 选项与 **\/Yu** 选项一起使用，以指定 .pch 文件的名称（如果该名称不同于 **\/Yc** 的文件名参数或源文件的基名称），如下所示：  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 此命令指定名为 MYPCH.pch 的预编译头文件。  编译器使用其内容还原所有头文件（一直到 MYAPP.h 并包含该文件）的预编译状态。  然后编译器编译在 MYAPP.h 的 **include** 语句之后出现的代码。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)