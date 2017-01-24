---
title: "/Tc、/Tp、/TC、/TP（指定源文件类型） | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.CompileAs"
  - "VC.Project.VCCLCompilerTool.CompileAs"
  - "/Tp"
  - "/tc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Tc 编译器选项 [C++]"
  - "/Tp 编译器选项 [C++]"
  - "源文件, 指定到编译器"
  - "Tc 编译器选项 [C++]"
  - "-Tc 编译器选项 [C++]"
  - "Tp 编译器选项 [C++]"
  - "-Tp 编译器选项 [C++]"
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Tc、/Tp、/TC、/TP（指定源文件类型）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/Tc** 选项指定 `filename` 为 C 源文件，即使它没有 .c 扩展名。  **\/Tp** 选项指定 `filename` 为 C\+\+ 源文件，即使它没有 .cpp 或 .cxx 扩展名。  选项和 `filename` 之间的空格是可选的。  每个选项指定一个文件；若要指定其他文件，请重复此选项。  
  
 **\/TC** 和 **\/TP** 是 **\/Tc** 和 **\/Tp** 的全局变量。  它们指定编译器将在命令行上命名的所有文件视为 C 源文件 \(**\/TC**\) 或 C\+\+ 源文件 \(**\/TP**\)，而不考虑它们在命令行上相对于选项的位置。  这些全局选项可通过 **\/Tc** 或 **\/Tp** 在单个文件上重写。  
  
## 语法  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## Arguments  
 `filename`  
 C 或 C\+\+ 源文件。  
  
## 备注  
 默认情况下，CL 假定扩展名为 .c 的文件是 C 源文件，扩展名为 .cpp 或 .cxx 的文件是 C\+\+ 源文件。  
  
 当指定 **TC** 或 **Tc** 选项时，可忽略[\/Zc:wchar\_t（wchar\_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 选项的规范。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“编译为”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。  
  
## 示例  
 下列 CL 命令行指定 MAIN.c、TEST.prg 和 COLLATE.prg 都是 C 源文件。  CL 将不识别 PRINT.prg。  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 下列 CL 命令行指定 TEST1.c、TEST2.cxx、TEST3.huh 和 TEST4.o 作为 C\+\+ 文件编译，TEST5.z 作为 C 文件编译。  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)