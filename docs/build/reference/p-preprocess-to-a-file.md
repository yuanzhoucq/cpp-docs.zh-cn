---
title: "/P（预处理到文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFile"
  - "/p"
  - "VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/P 编译器选项 [C++]"
  - "输出文件, 预处理器"
  - "P 编译器选项 [C++]"
  - "-P 编译器选项 [C++]"
  - "预处理输出文件"
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /P（预处理到文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

预处理 C 和 C\+\+ 源文件并将预处理的输出写入到文件。  
  
## 语法  
  
```  
/P  
```  
  
## 备注  
 此文件具有与源文件相同的基名称和一个 .i 扩展名。  在此过程中，执行所有的预处理器指令，执行宏展开，并移除注释。  若要在预处理输出中保留注释，请将 [\/C（在预处理期间保留注释）](../../build/reference/c-preserve-comments-during-preprocessing.md) 选项与 **\/P** 一起使用。  
  
 **\/P** 将 `#line` 指令添加到输出中，位于每个包含文件的开头和结尾以及被条件编译预处理器指令移除的行的周围。  这些指令将预处理文件中的行重新编号。  因此，在处理后期生成的错误引用原始源文件的行号而不是预处理文件中的行的行号。  若要取消生成 `#line` 指令，请使用 [\/EP（不使用 \#line 指令预处理到 stdout）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 和 **\/P**。  
  
 **\/P** 选项取消编译。  它不产生 .obj 文件，即使您使用 [\/Fo（对象文件名）](../../build/reference/fo-object-file-name.md)。  必须重新提交预处理文件以进行编译。  **\/P** 还取消来自 **\/FA**、**\/Fa** 和 **\/Fm** 选项的输出文件。  有关更多信息，请参见[\/FA、\/Fa（列出文件）](../../build/reference/fa-fa-listing-file.md)和[\/Fm（命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“预处理器”**属性页。  
  
4.  修改**“生成预处理文件”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 示例  
 下列命令行预处理 `ADD.C`，保留注释，添加 `#line` 指令，并将结果写入文件 `ADD.I`：  
  
```  
CL /P /C ADD.C  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\/Fi（预处理输出文件名）](../../build/reference/fi-preprocess-output-file-name.md)