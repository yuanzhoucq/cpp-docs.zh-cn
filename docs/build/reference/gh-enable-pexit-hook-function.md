---
title: "/GH（启用 _pexit 挂钩函数） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_pexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh 编译器选项 [C++]"
  - "_pexit 函数"
  - "Gh 编译器选项 [C++]"
  - "-Gh 编译器选项 [C++]"
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /GH（启用 _pexit 挂钩函数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在每个方法或函数的末尾调用 `_pexit`  函数。  
  
## 语法  
  
```  
/GH  
```  
  
## 备注  
 `_pexit`  函数不是任何库的组成部分，由您负责提供 `_pexit` 的定义。  
  
 除非打算显式调用 `_pexit`，否则不需要提供原型。  该函数必须看起来似乎具有下列原型，并且必须在进入时推送所有寄存器的内容，在退出时弹出未更改的内容：  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit` 类似于 `_penter`；有关如何编写 `_pexit` 函数的示例，请参见 [\/Gh（启用 \_penter 挂钩函数）](../../build/reference/gh-enable-penter-hook-function.md)。  
  
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