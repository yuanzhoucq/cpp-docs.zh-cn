---
title: "/Qimprecise_fwaits（移除 Try 块中的 fwaits） | Microsoft Docs"
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
  - "/Qimprecise_fwaits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qimprecise_fwaits 编译器选项 (C++)"
  - "-Qimprecise_fwaits 编译器选项 (C++)"
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qimprecise_fwaits（移除 Try 块中的 fwaits）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md) 编译器选项时，移除 `try` 块内部的 `fwait` 命令。  
  
## 语法  
  
```  
/Qimprecise_fwaits  
```  
  
## 备注  
 如果未同时指定 **\/fp:except**，此选项将不起任何作用。  如果指定了 **\/fp:except** 选项，编译器将在 `try` 块中每行代码周围插入 `fwait` 命令。  这样，编译器可以标识生成异常的特定代码行。  **\/Qimprecise\_fwaits** 移除 `fwait` 的内部指令，仅在 `try` 块周围保留等待。  这样做虽提高了性能，但编译器将只能指出是哪个 `try` 块导致了异常，而不能具体指出是哪个代码行。  
  
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