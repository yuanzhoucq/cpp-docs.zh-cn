---
title: "/Y-（忽略预编译头选项） | Microsoft Docs"
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
  - "/y-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Y- 编译器选项 [C++]"
  - "-Y- 编译器选项 [C++]"
  - "Y- 编译器选项 [C++]"
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Y-（忽略预编译头选项）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导致所有其他的 `/Y` 编译器选项都被忽略（并且它本身不能被重写）。  
  
## 语法  
  
```  
/Y-  
```  
  
## 备注  
 有关预编译头的更多信息，请参见：  
  
-   [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)