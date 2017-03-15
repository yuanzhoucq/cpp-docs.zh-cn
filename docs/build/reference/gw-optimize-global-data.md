---
title: "/Gw（优化全局数据） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Gw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gw 编译器选项 [C++]"
  - "-Gw 编译器选项 [C++]"
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /Gw（优化全局数据）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 COMDAT 节的程序包全局数据优化的。  
  
## 语法  
  
```  
/Gw[-]  
```  
  
## 备注  
 该**\/Gw**选项使编译器打包在个别的COMDAT节全局数据。  **\/Gw** 默认启用且不能关闭。  要明确地禁用它，使用 **\/Gw\-**。  当**\/Gw** 和 [\/GL](../../build/reference/gl-whole-program-optimization.md)启用，链接器将使用整个程序的优化在多个目标文件进行比较，以排除未引用的全局数据或合并相同只读的全局数据的COMDAT节。  这样可以显着减少范围的最终二进制可执行文件。  
  
 当你编译和链接分开，你可以使用 [\/OPT:REF](../../build/reference/opt-optimizations.md)链接器选项从可执行文件中排除未引用的全局数据与**\/Gw** 选项编译的目标文件。  
  
 您还可以使用 [\/OPT:ICF](../../build/reference/opt-optimizations.md) 和 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)连接器选项一起，在可执行文件的相同只读跨多个目标文件的全局数据与**\/Gw**选项合并。  
  
 欲了解更多信息，请参阅[Introducing \/Gw Compiler Switch](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) 有关Visual C \+ \+团队博客。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改“其它选项”属性以包括**\/Gw**，然后选择“确定”。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)