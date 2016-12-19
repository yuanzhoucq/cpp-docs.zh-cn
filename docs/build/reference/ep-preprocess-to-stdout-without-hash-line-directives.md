---
title: "/EP（不使用 #line 指令预处理到 stdout） | Microsoft Docs"
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
  - "/ep"
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EP 编译器选项 [C++]"
  - "将预处理器输出复制到 stdout"
  - "EP 编译器选项 [C++]"
  - "-EP 编译器选项 [C++]"
  - "预处理器输出, 复制到 stdout"
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /EP（不使用 #line 指令预处理到 stdout）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项预处理 C 和 C\+\+ 源文件，并将预处理后的文件复制到标准输出设备中。  
  
## 语法  
  
```  
/EP  
```  
  
## 备注  
 在此过程中，执行所有的预处理器指令，执行宏展开，并移除注释。  若要在预处理输出中保留注释，请将 [\/C（在预处理期间保留注释）](../../build/reference/c-preserve-comments-during-preprocessing.md) 选项与 **\/EP** 一起使用。  
  
 **\/EP** 选项取消编译。  必须重新提交预处理文件以进行编译。  **\/EP** 还取消来自 **\/FA**、**\/Fa** 和 **\/Fm** 选项的输出文件。  有关更多信息，请参见[\/FA、\/Fa（列出文件）](../../build/reference/fa-fa-listing-file.md)和[\/Fm（命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
 在处理后期生成的错误引用的是预处理文件的行号而非原始源文件的行号。  如果希望行号引用原始源文件，请改用 [\/E（预处理到 stdout）](../../build/reference/e-preprocess-to-stdout.md)。  **\/E** 选项出于此目的将 `#line` 指令添加到输出。  
  
 若要将带有 `#line` 指令的预处理输出发送到文件，请改用 [\/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md) 选项。  
  
 若要将带有 `#line` 指令的预处理输出发送到 stdout，请同时使用 **\/P** 和 **\/EP**。  
  
 用 **\/EP** 选项时，不能使用预编译头。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“预处理器”**属性页。  
  
4.  修改**“生成预处理文件”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 示例  
 下列命令行预处理文件 `ADD.C`，保留注释并在标准输出设备上显示结果：  
  
```  
CL /EP /C ADD.C  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)