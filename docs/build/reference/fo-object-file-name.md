---
title: "/Fo（对象文件名） | Microsoft Docs"
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
  - "/Fo"
  - "VC.Project.VCCLCompilerTool.ObjectFile"
  - "VC.Project.VCCLWCECompilerTool.ObjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fo 编译器选项 [C++]"
  - "Fo 编译器选项 [C++]"
  - "-Fo 编译器选项 [C++]"
  - "对象文件, 命名"
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fo（对象文件名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项指定要使用的对象 \(.obj\) 文件名或目录而不使用默认设置。  
  
## 语法  
  
```  
/Fopathname  
```  
  
## 备注  
 如果不使用此选项，对象文件将使用源文件的基名称和 .obj 扩展名。  可以使用任何所需名称和扩展名，但建议按约定使用 .obj。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“输出文件”**属性页。  
  
4.  修改**“对象文件名”**属性。在开发环境中，对象文件必须具有 .obj 的扩展名。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>。  
  
## 示例  
 下列命令行在驱动器 B 上的现有目录 \\OBJECT 中创建名为 THIS.obj 的对象文件。  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)