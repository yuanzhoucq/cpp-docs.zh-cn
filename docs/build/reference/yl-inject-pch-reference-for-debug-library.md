---
title: "/Yl（为调试库插入 PCH 引用） | Microsoft Docs"
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
  - "/yi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yl 编译器选项 [C++]"
  - "Yl 编译器选项 [C++]"
  - "-Yl 编译器选项 [C++]"
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yl（为调试库插入 PCH 引用）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果创建调试库时使用预编译头且生成失败，则使用它。  
  
## 语法  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## Arguments  
 `symbol`  
 要存储在对象模块中的任意符号。  
  
 \-  
 一个减号 \(\-\) 以显式禁用 **\/Yl** 编译器选项。  
  
## 备注  
 默认情况下，编译器使用 **\/Yl** 选项 \(没有指定 *symbol*\)。  **\/Yl** 选项允许调试器获取有关类型的完整信息。   **\/Yl\-** 让默认行为失效。  
  
 当用 **\/Yc** 和 **\/Yl** `symbol` 编译模块时，编译器创建类似于 \_\_@@\_PchSym\_@00@...@`symbol` 的符号（其中的省略号 \(...\) 表示链接器生成的字符串），并将其存储在对象模块中。  用此预编译头编译的任何源文件都引用指定的符号，这导致链接器包括对象模块及其在库中的调试信息。  
  
 使用此选项，可能生成 LNK1211。  当指定 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md) 选项时，编译器创建包含调试信息的预编译头文件。  当将预编译头存储到库中，使用该库生成对象模块，且源代码不引用预编译头文件定义的任一函数时，可能出错。  
  
 若要解决此问题，当创建不包含任何函数定义的预编译头文件时，请指定 **\/Yl**`symbol`，其中 `symbol` 是库中任意符号的名称。  此选项指示编译器将调试信息存储在预编译头文件中。  
  
 有关预编译头的更多信息，请参见：  
  
-   [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)  
  
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