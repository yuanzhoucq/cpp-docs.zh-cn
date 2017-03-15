---
title: "/arch (x64) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /arch (x64)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 x64 上为代码生成指定体系结构。  另请参阅 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 [\/arch \(ARM\)](../../build/reference/arch-arm.md)。  
  
## 语法  
  
```  
/arch:[AVX|AVX2]  
```  
  
## 参数  
 **\/arch:AVX**  
 启用对 Intel 高级矢量扩展指令的使用。  
  
 **\/arch:AVX2**  
 启用对 Intel 高级矢量扩展 2 指令的使用。  
  
## 备注  
 **\/arch** 仅影响本机函数的代码生成。  当使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时，**\/arch** 对托管的函数的代码生成没有影响。  
  
 指定 `__AVX__` 编译器选项时，将定义 **\/arch:AVX** 预处理器符号。  指定 `__AVX2__` 编译器选项时，将定义 **\/arch:AVX2** 预处理器符号。  有关详细信息，请参阅[预定义的宏](../../preprocessor/predefined-macros.md)。  Visual Studio 2013 Update 2（版本 12.0.34567.1）中引入了 **\/arch:AVX2** 选项。  
  
### 在 Visual Studio 中设置 \/arch:AVX 或 \/arch:AVX2 编译器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  依次选择**“配置属性”**、**“C\/C\+\+”**文件夹。  
  
3.  选择**“代码生成”**属性页。  
  
4.  在**启用增强指令集**下拉框中，选择**高级矢量扩展 \(\/arch:AVX\)**或**高级矢量扩展 2 \(\/arch:AVX2\)**。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## 请参阅  
 [\/arch（最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)