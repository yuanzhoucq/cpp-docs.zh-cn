---
title: "/vmb、/vmg（表示方法） | Microsoft Docs"
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
  - "/vmb"
  - "/vmg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmb 编译器选项 [C++]"
  - "/vmg 编译器选项 [C++]"
  - "表示方法编译器选项 [C++]"
  - "vmb 编译器选项 [C++]"
  - "-vmb 编译器选项 [C++]"
  - "vmg 编译器选项 [C++]"
  - "-vmg 编译器选项 [C++]"
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /vmb、/vmg（表示方法）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些选项选择编译器用来表示指向类成员的指针的方法。  
  
 如果始终在声明指向类成员的指针之前定义类，请使用 **\/vmb**。  
  
 在定义类之前，请使用 **\/vmg** 来声明指向类成员的指针。  当在两个互相引用的不同类中定义成员时可能有这种需要。  对这种互相引用的类，其中一个类必须在定义前引用。  
  
## 语法  
  
```  
/vmb  
/vmg  
```  
  
## 备注  
 还可以在代码中使用 [pointers\_to\_members](../../preprocessor/pointers-to-members.md) 或 [继承关键字](../../cpp/inheritance-keywords.md) 来指定指针的表示形式。  
  
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