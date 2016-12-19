---
title: "/Z7、/Zi、/ZI（调试信息格式） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.DebugInformationFormat"
  - "/zi"
  - "/z7"
  - "VC.Project.VCCLWCECompilerTool.DebugInformationFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C7 兼容编译器选项 [C++]"
  - "-Zl 编译器选项 [C++]"
  - "调试信息格式编译器选项"
  - "ZI 编译器选项"
  - "-ZI 编译器选项 [C++]"
  - "/ZI 编译器选项 [C++]"
  - "Z7 编译器选项 [C++]"
  - "调试 [C++]，调试信息文件"
  - "Zi 编译器选项 [C++]"
  - "非编译器选项 [C++]"
  - "/Zi 编译器选项 [C++]"
  - "程序数据库编译器选项 [C++]"
  - "完全符号调试信息"
  - "/Z7 编译器选项 [C++]"
  - "仅限行号编译器选项 [C++]"
  - "cl.exe 编译器，调试选项"
  - "-Z7 编译器选项 [C++]"
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: 21
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Z7、/Zi、/ZI（调试信息格式）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选择为程序创建的调试信息的类型，并选择是将此信息保存在对象\(.obj\)文件中，还是保存在程序数据库\(PDB\)中。  
  
## 语法  
  
```  
/Z{7|i|I}  
```  
  
## 备注  
 下表描述了这些选项。  
  
 无  
 不生成任何调试信息，因此编译较快。  
  
 **\/Z7**  
 生成包含用于调试器的完整符号调试信息的 .obj 文件。  符号化调试信息包含变量的名称和类型以及函数和行号。  不生成任何 .pdb 文件。  
  
 对于第三方库的分发服务器，不生成 .pdb 文件是一个优点。  但是，在链接阶段和调试期间，用于预编译头的 .obj 文件是必需的。  如果 .pch 对象文件中只有类型信息（没有代码），则还必须使用 [\/Yl（为调试库插入 PCH 引用）](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 进行编译。  
  
 **\/Zi**  
 生成一个程序数据库\(PDB\)，其中包含供调试器使用的类型信息和符号化调试信息。  符号化调试信息包含变量的名称和类型以及函数和行号。  
  
 **\/Zi** 不影响优化。  但是，**\/Zi** 的确暗示了 **\/debug**；有关更多信息，请参见 [\/DEBUG（生成调试信息）](../../build/reference/debug-generate-debug-info.md)。  
  
 类型信息放置在 .pdb 文件而不是 .obj 文件中。  
  
 可以将 [\/Gm（启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md) 和 **\/Zi** 结合使用，但使用 **\/Z7** 编译时不能使用 **\/Gm**。  
  
 使用 **\/Zi** 和 **\/clr** 编译时，<xref:System.Diagnostics.DebuggableAttribute> 特性将不会放置到程序集元数据中；如果要使用该特性，则必须在源代码中指定它。  该特性可影响应用程序的运行时性能。  有关 Debuggable 特性如何影响性能以及如何减轻性能影响的更多信息，请参见[令映像更易于调试](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)。  
  
 **\/ZI**  
 采用支持“编辑并继续”功能的格式生成程序数据库\(如上所述\)。  如果想使用“编辑并继续”调试，则必须使用此选项。  因为大多数优化与“编辑并继续”不兼容，所以使用 **\/ZI** 会禁用代码中的所有 `#pragma optimize` 语句。  
  
 **\/ZI** 会导致在编译中使用 [\/Gy（启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md) 和 [\/FC（所诊断源代码文件的完整路径）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。  
  
 **\/ZI** 与 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 不兼容。  
  
> [!NOTE]
>  **\/ZI** 仅可在面向 x86 的编译器中使用；此编译器选项不能在面向 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 处理器的编译器中使用。  
  
 编译器将程序数据库命名为 *project*.pdb。  如果编译没有项目的文件，则编译器将创建名为 VC*x*0.pdb. 的数据库，其中 *x* 是正在使用的 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 的主版本。  编译器将 PDB 的名称嵌入每个使用此选项创建的 .obj 文件中，从而使调试器了解符号和行号信息的位置。  当使用此选项时，.obj 文件将较小，因为调试信息存储在 .pdb 文件中而不是 .obj 文件中。  
  
 如果从使用此选项编译的对象创建库，则在将库链接到程序时，关联 .pdb 文件必须可用。  因此，如果分发此库，就必须分发 PDB。  
  
 若要不使用 .pdb 文件创建包含调试信息的库，必须选择编译器的 C 7.0 兼容 \(**\/Z7**\) 选项。  如果使用预编译头选项，则预编译头和其他源代码的调试信息都放在 PDB 中。  指定了“程序数据库”选项时将忽略 **\/Yd** 选项。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“常规”**属性页。  
  
4.  修改**“调试信息格式”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)