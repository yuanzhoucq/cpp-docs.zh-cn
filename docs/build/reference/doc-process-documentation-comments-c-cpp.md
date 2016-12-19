---
title: "/doc（处理文档注释）(C/C++) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "/doc"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/doc 编译器选项 [C++]"
  - "注释, C++ 代码"
  - "-doc 编译器选项 [C++]"
  - "XML 文档, 源文件中的注释"
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /doc（处理文档注释）(C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使编译器对源代码文件中的文档注释进行处理，并为每个具有文档注释的源代码文件创建一个 .xdc 文件。  
  
## 语法  
  
```  
/doc[name]  
```  
  
## Arguments  
 `name`  
 编译器将创建的 .xdc 文件的名称。  仅在将一个 .cpp 文件传入编译时有效。  
  
## 备注  
 使用 xdcmake.exe 将 .xdc 文件处理为一个 .xml 文件。  有关详细信息，请参阅[XDCMake 参考](../../ide/xdcmake-reference.md)。  
  
 可以将文档注释添加到源代码文件中。  有关详细信息，请参阅[建议的文档注释标记](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
 **\/doc** 与 **\/clr:oldSyntax** 不兼容。有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 若要在 IntelliSense 中使用生成的 .xml 文件，就要使 .xml 文件与要支持的程序集具有相同的文件名，并使 .xml 文件与该程序集处于同一目录中。  当在 Visual Studio 项目中引用该程序集时，也可以找到该 .xml 文件。  有关更多信息，请参见[使用 IntelliSense](../Topic/Using%20IntelliSense.md)和[提供 XML 代码注释](../Topic/Supplying%20XML%20Code%20Comments.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“C\/C\+\+”**节点。  
  
4.  选择**“输出文件”**属性页。  
  
5.  修改**“生成 XML 文档文件”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)