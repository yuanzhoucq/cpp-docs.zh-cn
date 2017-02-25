---
title: "/Gm（启用最小重新生成） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.MinimalRebuild"
  - "/Gm"
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.MinimalRebuild"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gm 编译器选项 [C++]"
  - "启用最小重新生成编译器选项 [C++]"
  - "Gm 编译器选项 [C++]"
  - "-Gm 编译器选项 [C++]"
  - "最小重新生成"
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Gm（启用最小重新生成）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项启用最小重新生成，它确定是否需要重新编译包含已更改的 C\+\+ 类定义的 C\+\+ 源文件，该定义存储在头 \(.h\) 文件中。  
  
## 语法  
  
```  
/Gm  
```  
  
## 备注  
 在首次编译期间，编译器在项目的 .idb 文件中存储源文件和类定义之间的依赖关系信息。  （依赖关系信息表明每个源文件所依赖的类定义以及该定义位于哪个 .h 文件中。）后面的编译使用存储在 .idb 文件中的信息确定是否需要编译某个源文件（即使它包含已修改的 .h 文件）。  
  
> [!NOTE]
>  最小重新生成依赖于类定义不会在包含文件之间更改。  类定义对于项目必须是全局的（对于给定类应只有一个定义），因为 .idb 文件中的依赖关系信息是为整个项目创建的。  如果项目中的某个类有多个定义，请禁用最小重新生成。  
  
 由于增量链接器不支持通过使用 [\/ZW（Windows 运行时编译）](../../build/reference/zw-windows-runtime-compilation.md) 选项将 Windows 元数据包含在 .obj 文件中，因此 **\/Gm** 选项与 **\/ZW** 不兼容。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改**“启用最小重新生成”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)