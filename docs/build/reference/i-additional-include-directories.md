---
title: "/I（附加包含目录） | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories"
  - "/I"
  - "VC.Project.VCNMakeTool.IncludeSearchPath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/I 编译器选项 [C++]"
  - "“附加包含目录”编译器选项"
  - "I 编译器选项 [C++]"
  - "-I 编译器选项 [C++]"
  - "包含目录, 编译器选项 [C++]"
  - "设置包含目录"
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /I（附加包含目录）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将目录添加到要在其中搜索包含文件的目录列表中。  
  
## 语法  
  
```  
/I[ ]directory  
```  
  
## Arguments  
 `directory`  
 添加到目录列表中的目录，该列表中的目录用于搜索包含文件。  
  
## 备注  
 若要添加多个目录，请多次使用此选项。  直到找到指定包含文件时才停止搜索这些目录。  
  
 可以将此选项与“忽略标准包含路径”\([\/X（忽略标准包含路径）](../../build/reference/x-ignore-standard-include-paths.md)\) 选项一起使用。  
  
 编译器按下列顺序搜索目录：  
  
1.  包含源文件的目录。  
  
2.  用 **\/I** 选项指定的目录（按照 CL 遇到它们的顺序排列）。  
  
3.  在 **INCLUDE** 环境变量中指定的目录。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“常规”**属性页。  
  
4.  修改**“附加包含目录”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。  
  
## 示例  
 下列命令按下列顺序查找 MAIN.c 请求的包含文件：首先是包含 MAIN.c 的目录中，然后是 \\INCLUDE 目录，接着是 \\MY\\INCLUDE 目录，最后是分配给 INCLUDE 环境变量的目录。  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)