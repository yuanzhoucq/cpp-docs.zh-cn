---
title: "/GF（消除重复的字符串） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.StringPooling"
  - "VC.Project.VCCLWCECompilerTool.StringPooling"
  - "/gf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GF 编译器选项 [C++]"
  - "重复字符串"
  - "“消除重复字符串”编译器选项 [C++]"
  - "GF 编译器选项 [C++]"
  - "-GF 编译器选项 [C++]"
  - "池字符串编译器选项 [C++]"
  - "字符串 [C++], 池"
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GF（消除重复的字符串）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用编译器在程序映像和执行时的内存中创建相同字符串的一个副本。  这是一种优化，被称为“字符串池”，可用于创建较小的程序。  
  
## 语法  
  
```  
/GF  
```  
  
## 备注  
 如果使用 **\/GF**，操作系统将不交换内存的字符串部分，并可从映像文件读回字符串。  
  
 **\/GF** 将字符串汇集为只读字符串。  如果尝试在 **\/GF** 下修改字符串，则会发生应用程序错误。  
  
 字符串池允许将作为指向多个缓冲区的多个指针用作指向单个缓冲区的多个指针。  在下列代码中，`s` 和 `t` 用相同字符串初始化。  字符串池使它们指向相同的内存：  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  用于“编辑并继续”的 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 选项会自动设置 **\/GF** 选项。  
  
> [!NOTE]
>  **\/GF** 编译器选项为每个唯一的字符串创建一个可寻址的节。  默认情况下，一个对象文件最多可包含 65,536 个可寻址的节。  如果您的程序包含的字符串超过 65536 个，则请使用 [\/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) 编译器选项创建更多节。  
  
 在使用 [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 **\/O2** 时，**\/GF** 有效。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改**“启用字符串池”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)