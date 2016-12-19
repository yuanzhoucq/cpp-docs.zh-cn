---
title: "/X（忽略标准包含路径） | Microsoft Docs"
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
  - "/x"
  - "VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath"
  - "VC.Project.VCCLWCECompilerTool.IgnoreStandardIncludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/X 编译器选项 [C++]"
  - "“忽略标准包括路径”编译器选项"
  - "包含目录, 忽略标准"
  - "包含文件, 忽略标准路径"
  - "X 编译器选项"
  - "-X 编译器选项 [C++]"
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /X（忽略标准包含路径）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

阻止编译器在 PATH 和 INCLUDE 环境变量中指定的目录中搜索包含文件。  
  
## 语法  
  
```  
/X  
```  
  
## 备注  
 此选项可以与 [\/I（附加包含目录）](../../build/reference/i-additional-include-directories.md) \(**\/I**`directory`\) 一起使用。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“预处理器”**属性页。  
  
4.  修改**“忽略标准包含路径”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。  
  
## 示例  
 在下列命令中，`/X` 通知编译器忽略由 PATH 和 INCLUDE 环境变量指定的位置，`/I` 指定在其中查找包含文件的目录：  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)