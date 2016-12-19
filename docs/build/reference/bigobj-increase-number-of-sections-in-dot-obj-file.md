---
title: "/bigobj（增加 .Obj 文件中的节数） | Microsoft Docs"
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
  - "/bigobj"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/bigobj 编译器选项 [C++]"
  - "bigobj 编译器选项 [C++]"
  - "-bigobj 编译器选项 [C++]"
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /bigobj（增加 .Obj 文件中的节数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/bigobj** 增加对象文件可包含的节数。  
  
## 语法  
  
```  
/bigobj  
```  
  
## 备注  
 默认情况下，对象文件最多可存放 65,536 \(2^16\) 个可寻址的节。  这种情况不管指定哪个目标平台。  **\/bigobj** 可将该地址容量增加至 4,294,967,296 \(2^32\)。  
  
 大多数模块将从来不会生成包含节数超过 65,536 的 .obj 文件。  但是，计算机生成的代码或大量使用模板库的代码可能需要可存放更多节的 .obj 文件。  因为计算机给定的 XAML 代码包含大量头文件，在 Windows 应用商店项目中**\/bigobj** 默认已开启。  在 Windows 应用商店应用项目中如果禁用此选项，可能会遇到编译器错误 C1128。  
  
 Visual C\+\+ 2005 之前的版本中所提供的链接器不能读取使用 **\/bigobj** 生成的 .obj 文件。  
  
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