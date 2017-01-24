---
title: "/arch (ARM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /arch (ARM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为 ARM 上的代码生成指定体系结构。  另请参见 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 [\/arch \(x64\)](../../build/reference/arch-x64.md)。  
  
## 语法  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## 参数  
 **\/arch:ARMv7VE**  
 允许使用 ARMv7VE 虚拟化扩展指令。  
  
 **\/arch:VFPv4**  
 允许使用 ARM VFPv4 指令。  如果未指定此选项，则默认为 VFPv3。  
  
## 备注  
 `_M_ARM_FP` 宏（仅用于 ARM）指示使用了哪个 **\/arch** 编译器选项（如果有）。  有关详细信息，请参阅 [预定义的宏](../../preprocessor/predefined-macros.md)。  
  
 当使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时，**\/arch** 对托管的函数的代码生成没有影响。  **\/arch** 仅影响本机函数的代码生成。  
  
### 在 Visual Studio 中设置 \/arch:ARMv7VE 或 \/arch:VFPv4 编译器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 C\/C\+\+ 文件夹。  
  
3.  选择“命令行”属性页。  
  
4.  在“附加选项”框中，添加 `/arch:ARMv7VE` 或 `/arch:VFPv4`。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## 请参阅  
 [\/arch（最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)