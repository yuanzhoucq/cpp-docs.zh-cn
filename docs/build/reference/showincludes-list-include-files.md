---
title: "/showIncludes（列出包含文件） | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.ShowIncludes"
  - "VC.Project.VCCLCompilerTool.ShowIncludes"
  - "/showincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/showIncludes 编译器选项 [C++]"
  - "包含文件"
  - "包含文件, 在编译时显示"
  - "showIncludes 编译器选项 [C++]"
  - "-showIncludes 编译器选项 [C++]"
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /showIncludes（列出包含文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使编译器输出包含文件的列表。  还显示嵌套包含文件（在您包含的文件内包含的文件）。  
  
## 语法  
  
```  
/showIncludes  
```  
  
## 备注  
 当在编译期间遇到包含文件时，则输出消息，例如：  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 用缩进来指示嵌套包含文件，每个嵌套级别使用一个空格，例如：  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 在本例中，`2.h` 包含在 `1.h` 内，因此使用了缩进。  
  
 **\/showIncludes** 选项发出到 `stderr`，而不是 `stdout`。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“显示包含”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)