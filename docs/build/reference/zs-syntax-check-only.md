---
title: "/Zs（只进行语法检查） | Microsoft Docs"
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
  - "/zs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zs 编译器选项 [C++]"
  - "“仅限语法检查”编译器选项"
  - "Zs 编译器选项"
  - "-Zs 编译器选项 [C++]"
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zs（只进行语法检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通知编译器只检查命令行上的源文件的语法。  
  
## 语法  
  
```  
/Zs  
```  
  
## 备注  
 使用此选项时，不创建任何输出文件，同时将错误信息写入标准输出。  
  
 **\/Zs** 选项提供一种在编译和链接源文件之前查找和更正语法错误的快捷方法。  
  
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