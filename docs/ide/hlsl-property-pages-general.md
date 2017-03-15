---
title: "HLSL 属性页：常规 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.FXCompilerTool.ShaderModel"
  - "VC.Project.FXCompilerTool.PreprocessorDefinitions"
  - "VC.Project.FXCompilerTool.ShaderType"
  - "VC.Project.FXCompilerTool.EnableDebuggingInformation"
  - "VC.Project.FXCompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.FXCompilerTool.DisableOptimizations"
  - "VC.Project.FXCompilerTool.EntryPointName"
dev_langs: 
  - "C++"
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: 8
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 8
---
# HLSL 属性页：常规
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要配置 HLSL 编译器 \(fxc.exe\) 的下列属性，请使用其 **常规** 属性页。  有关访问 HLSL 文件夹的 **常规** 属性页的信息，请参见 [如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)"。  
  
## UIElement 列表  
 **附加包含目录**  
 添加一个或多个目录添加到包含路径。  使用分号分隔内容。  
  
 此属性对应于 **\/I\[path\]** 命令行参数。  
  
 **入口点名称**  
 指定着色器访问点。  默认情况下，值作为 **主**。  
  
 此属性对应于 **\/E\[name\]** 命令行参数。  
  
 **禁用优化**  
 禁用优化的**是 \(\/Od\)** ;否则，**否**。  默认情况下，此值为 **调试** 配置和 **否** 的 **是 \(\/Od\)发布** 配置的。  
  
 为 HLSL 编译器的 **\/Od** 命令行参数隐式应用 **\/Gfp** 命令行参数，但是，输出可能不是与是通过显式通过 **\/Od** 和 **\/Gfp** 命令行参数生成的输出。  
  
 **启用调试信息**  
 启用调试信息的**是 \(\/Zi\)** ;否则，**否**。  默认情况下，此值为 **调试** 配置和 **否** 的 **是 \(\/Zi\)发布** 配置的。  
  
 **着色器类型**  
 指定着色器。  不同类型的图像着色器实现管线的不同部分。  某些类型的着色器只能在 **着色器模型** 属性指定\) 的最近着色器模型 \(—示例，计算着色器在中引入着色器设计 5。  
  
 此属性对应于 **\/T \[type\]\_\[model\]** 命令行参数的 **\[type\]** 部分于 HLSL 编译器。  **着色器模型** 属性指定参数的 **\[model\]** 部分。  
  
 **着色器模型**  
 指定着色器模型。  不同的着色器模型具有不同的功能。  通常，最近着色器模型提供扩展功能，但需要更多现代的图形硬件运行着色器代码。  **着色器类型** 由属性指定\) 的某些类型的着色器 \(只能在最近着色器模型 \(例如，计算着色器在中引入着色器设计 5。  
  
 此属性对应于 **\/T \[type\]\_\[model\]** 命令行参数的 **\[model\]** 部分于 HLSL 编译器。  **着色器类型** 属性指定参数的 **\[type\]** 部分。  
  
 **预处理器定义**  
 添加一个或多个预处理器符号定义应用于 HLSL 源代码文件。  使用分号分隔符号定义。  
  
 此属性对应于 **\/D \[definitions\]** 命令行参数于 HLSL 编译器。  
  
## 请参阅  
 [“HLSL”属性页](../ide/hlsl-property-pages.md)   
 [HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)   
 [HLSL 属性页：输出文件](../ide/hlsl-property-pages-output-files.md)