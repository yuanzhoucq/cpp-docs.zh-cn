---
title: "/favor（针对体系结构详细信息优化） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/favor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-favor 编译器选项 [C++]"
  - "/favor 编译器选项 [C++]"
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# /favor（针对体系结构详细信息优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成为特定  **\/favor:**`option`结构或为 AMD64 和 64 位内存扩展技术 \(EM64T\) 结构中的特定宏结构进行了优化的代码。  
  
## 语法  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## 备注  
 **\/favor:blend**  
 \(x86 and x64\)生成针对 AMD 和 Intel64 结构中特定的微结构进行优化的代码。  虽然 **\/favor:blend** 可能无法使特定处理器获得最佳性能，但是可以使大多数 x86 and x64 处理器获得最佳性能。  默认情况，**\/favor:blend** 是有效的。  
  
 **\/favor:ATOM**  
 \(x86 和 x64\) 导致为 Intel Atom 处理器和 Intel 处理器 Centrino Atom 的特定技术优化的代码。  代码生成可以使用 **\/favor:ATOM** 还生成 Intel 处理器针对 Intel SSSE3，SSE3、SSE 和 SSE2 指令。  
  
 **\/favor:AMD64**  
 \(x64 only\) 为 AMD Opteron 和支持 64 位扩展的 Athlon 处理器优化生成的代码。  优化的代码可以在所有 x64兼容平台上运行。  使用 **\/favor:AMD64** 可能生成的代码可使支持 Intel64 的 Intel 处理器的性能降低。  
  
 **\/favor:INTEL64**  
 仅可在 \(x64 \) 编译器中使用，它为支持 Intel64 的 Intel 处理器优化生成的代码，而这通常会使该平台的性能得到提高。  生成的代码可在任何x64平台上运行。  使用 **\/favor:INTEL64** 生成的代码会使 AMD Opteron 和支持 64 位扩展的 Athlon 处理器的性能降低。  
  
> [!NOTE]
>  Intel64 结构以前称为 64 位扩展内存技术，相应的编译器选项为 **\/favor:EM64T**。  
  
 更多怎样使用 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架构编程的信息，请查看 [x64 软件约定](../../build/x64-software-conventions.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在“附加选项”框中输入  **编译器选项**。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)