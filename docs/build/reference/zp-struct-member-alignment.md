---
title: "/Zp（结构成员对齐） | Microsoft Docs"
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
  - "/zp"
  - "VC.Project.VCCLCompilerTool.StructMemberAlignment"
  - "VC.Project.VCCLWCECompilerTool.StructMemberAlignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zp 编译器选项 [C++]"
  - "“结构成员对齐”编译器选项"
  - "Zp 编译器选项"
  - "-Zp 编译器选项 [C++]"
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zp（结构成员对齐）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制结构的成员如何封装到内存并为模块中的所有结构指定相同的封装。  
  
## 语法  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## 备注  
 当指定此选项时，第一个结构成员后的每个结构成员将存储在成员类型大小或 `n` 字节边界（其中 `n` 为 1、2、4、8 或 16）两者中较小的一个边界上。  
  
 下表描述了可用的值。  
  
 1  
 针对 1 字节边界将结构打包。  与 **\/Zp** 相同。  
  
 2  
 针对 2 字节边界将结构打包。  
  
 4  
 针对 4 字节边界将结构打包。  
  
 8  
 针对 8 字节边界将结构打包\(默认设置\)。  
  
 16  
 针对 16 字节边界将结构打包。  
  
 除非有特定的对齐要求，否则不应使用此选项。  
  
 还可以使用 [pack](../../preprocessor/pack.md) 控制结构封装。  有关对齐的详细信息，请参阅：  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [\_\_alignof 运算符](../../cpp/alignof-operator.md)  
  
-   [\_\_unaligned](../../cpp/unaligned.md)  
  
-   [结构对齐示例](../../build/examples-of-structure-alignment.md)（特定于 x64）  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改**“结构成员对齐”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)