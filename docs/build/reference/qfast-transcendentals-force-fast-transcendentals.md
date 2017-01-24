---
title: "/Qfast_transcendentals（强制快速先验） | Microsoft Docs"
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
  - "/Qfast_transcendentals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qfast_transcendentals"
  - "强制快速先验"
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qfast_transcendentals（强制快速先验）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成先验函数的内联代码。  
  
## 语法  
  
```  
/Qfast_transcendentals  
```  
  
## 备注  
 此编译器选项强制将先验函数转换成内联代码，以提高执行速度。  此选项只在与 **\/fp:except** 或 **\/fp:precise** 成对使用时才有效。  生成先验函数的内联代码已是 **\/fp:fast** 下的默认行为。  
  
 此选项与 **\/fp:strict** 不兼容。  有关浮点编译器选项的更多信息，请参见 [\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)