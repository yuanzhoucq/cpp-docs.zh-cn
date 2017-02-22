---
title: "HLSL 属性页：输出文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.FXCompilerTool.AssemblerOutput"
  - "VC.Project.FXCompilerTool.ObjectFileOutput"
  - "VC.Project.FXCompilerTool.HeaderFileOutput"
  - "VC.Project.FXCompilerTool.VariableName"
  - "VC.Project.FXCompilerTool.AssemblerOutputFile"
dev_langs: 
  - "C++"
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: 5
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 5
---
# HLSL 属性页：输出文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要配置 HLSL 编译器 \(fxc.exe\) 的下列属性，请使用其 **输出文件** 属性。  有关访问 HLSL 文件夹的 **输出文件** 属性页的信息，请参见 [如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)"。  
  
## UIElement 列表  
 **标头变量名称**  
 指定用于编码 HLSL 对象代码数组的名称。  数组将作为输出由 HLSL 编译器的标头文件中。  标头文件的名称由 **头文件名称** 特性指定。  
  
 此属性对应于 **\/Vn\[name\]** 命令行参数。  
  
 **头文件名称**  
 指定是输出由 HLSL 编译器标头文件的名称。  该标头包含 HLSL 中输入到数组中的对象代码。  数组的名称由 **标头变量名称** 特性指定。  
  
 此属性对应于 **\/Fh\[name\]** 命令行参数。  
  
 **对象文件名**  
 指定是输出由 HLSL 编译器对象文件的名称。  默认情况下，此值为 **$\(OutDir\)%\(Filename\).cso**。  
  
 此属性对应于 **\/Fo\[name\]** 命令行参数。  
  
 **汇编程序输出**  
 输出汇编语言语句的**仅列出程序集 \(\/FA\)**。  输出的**程序集代码和十六进制 \(\/Fx\)** 两个汇编语言语句和相应的操作代码以十六进制。  默认情况下，列表不是输出。  
  
 **汇编程序输出文件**  
 指定列表是输出由 HLSL 编译器的文件的程序集的名称。  
  
 此属性对应于 **\/Fc\[name\]** 和 **\/Fx \[name\]** 命令行参数。  
  
## 请参阅  
 [“HLSL”属性页](../ide/hlsl-property-pages.md)   
 [HLSL 属性页：常规](../ide/hlsl-property-pages-general.md)   
 [HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)