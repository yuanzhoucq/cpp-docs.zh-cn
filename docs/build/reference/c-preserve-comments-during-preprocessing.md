---
title: "/C（在预处理期间保留注释） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.KeepComments"
  - "/c"
  - "VC.Project.VCCLWCECompilerTool.KeepComments"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c 编译器选项 [C++]"
  - "c 编译器选项 [C++]"
  - "-c 编译器选项 [C++]"
  - "注释, 在预处理过程中不去除"
  - "在预处理过程中保留注释"
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /C（在预处理期间保留注释）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在预处理期间保留注释。  
  
## 语法  
  
```  
/C  
```  
  
## 备注  
 此编译器选项需要 **\/E**、**\/P** 或 **\/EP** 选项。  
  
 下面的代码示例将显示源代码注释。  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 此示例将生成以下输出。  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“预处理器”**属性页。  
  
4.  修改**“保留注释”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\/E（预处理到 stdout）](../../build/reference/e-preprocess-to-stdout.md)   
 [\/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)   
 [\/EP（不使用 \#line 指令预处理到 stdout）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)