---
title: "/Fp（命名 .Pch 文件） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderFile"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 命名"
  - "/Fp 编译器选项 [C++]"
  - "Fp 编译器选项 [C++]"
  - "-Fp 编译器选项 [C++]"
  - "名称 [C++], PCH"
  - "命名预编译器头文件"
  - "PCH 文件, 命名"
  - "预编译的头文件, 命名"
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fp（命名 .Pch 文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为预编译头提供路径名，而不使用默认路径名。  
  
## 语法  
  
```  
/Fppathname  
```  
  
## 备注  
 将此选项与 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md) 或 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md) 一起使用以便为预编译头提供路径名，而不使用默认路径名。  也可以将 **\/Fp** 与 **\/Yc** 一起使用，以指定使用不同于 **\/Yc** `filename` 参数和源文件基名称的预编译头文件。  
  
 如果在路径名中未指定扩展名部分，则假定扩展名为 .pch。  如果指定目录但未指定文件名，则默认文件名为 VC`x`0.pch.，其中 `x` 是所使用的 Visual C\+\+ 的主版本。  
  
 还可将 **\/Fp** 选项与 **\/Yu** 一起使用。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“预编译头”**属性页。  
  
4.  修改**“预编译头文件”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>。  
  
## 示例  
 如果要为程序的调试版本创建预编译头文件，并要同时编译头文件和源代码，可以指定如下的命令：  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## 示例  
 下列命令指定使用名为 MYPCH.pch 的预编译头文件。  编译器假定已通过 MYAPP.h 预编译 PROG.cpp 中的源代码且预编译代码驻留在 MYPCH.pch 中。  它使用 MYPCH.pch 的内容，并编译 PROG.cpp 的其余部分以创建 .obj 文件。  此示例的输出是一个名为 PROG.exe 的文件。  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)