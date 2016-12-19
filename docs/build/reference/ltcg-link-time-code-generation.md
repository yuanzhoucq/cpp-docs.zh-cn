---
title: "/LTCG（链接时代码生成） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.LinkTimeCodeGeneration"
  - "VC.Project.VCConfiguration.WholeProgramOptimization"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
  - "/ltcg"
  - "VC.Project.VCCLCompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LTCG 链接器选项"
  - "C++ 链接器中的链接时代码生成"
  - "LTCG 链接器选项"
  - "-LTCG 链接器选项"
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LTCG（链接时代码生成）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## 备注  
 :INCREMENTAL（可选）  
 指定链接器仅将全程序优化或链接时间代码生成 \(LTCG\) 应用于受编辑影响的文件集，而不是应用于整个项目。默认情况下，当指定 \/LTCG 时，不会设置此标志，并且通过使用全程序优化链接整个项目。  
  
 :NOSTATUS &#124; :STATUS（可选）  
 指定链接器是否显示指示已完成的链接百分比的进度指示器。默认情况下，不会显示此状态信息。  
  
 :OFF（可选）  
 禁用链接时间代码生成。此行为与在命令行上未指定 \/LTCG 时的行为相同。  
  
 :PGINSTRUMENT（可选）  
 此选项已弃用。请改用 **\/LTCG** 和 **\/GENPROFILE** 或 **\/FASTGENPROFILE** 来生成适用于按配置优化的被检测生成。  
  
 从被检测运行收集的数据用于创建优化的映像。有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。此选项的缩写形式是 \/LTCG:PGI。  
  
 :PGOPTIMIZE（可选）  
 此选项已弃用。请改用 **\/LTCG** 和 **\/USEPROFILE** 来生成优化的映像。有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。此选项的缩写形式是 \/LTCG:PGO。  
  
 :PGUPDATE（可选）  
 此选项已弃用。请改用 **\/LTCG** 和 **\/USEPROFILE** 来生成优化的映像。有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。此选项的缩写形式是 \/LTCG:PGU。  
  
 \/LTCG 选项通知链接器调用编译器并执行全程序优化。你也可以执行按配置优化。有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。  
  
 存在以下例外情况，你无法将链接器选项添加到先前未在 \/LTCG 和 \/GENPROFILE 选项的 PGO 初始化组合中指定的 \/LTCG 和 \/USEPROFILE 的 PGO 组合：  
  
-   [\/BASE](../../build/reference/base-base-address.md)  
  
-   [\/FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   \/LTCG  
  
-   [\/MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [\/OUT](../../build/reference/out-output-file-name.md)  
  
-   [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [\/PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [\/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 当你通过使用 \/LTCG 和 \/USEPROFILE 生成时，不一定必须指定与要初始化 PGO 的 \/LTCG 和 \/GENPROFILE 选项一起指定的任何链接器选项；它们是隐式指定的。  
  
 本主题的其余部分从链接时间代码生成方面讨论了 \/LTCG。  
  
 \/LTCG 隐式包含 [\/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
 如果它传递使用 **\/GL** 或 MSIL 模块编译的模块，链接器则调用链接时间代码生成（请参阅 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)）。如果在将 **\/GL** 或 MSIL 模块传递给链接器时未显式指定 **\/LTCG**，链接器最终将检测到此问题并使用 **\/LTCG** 重新启动链接。  
  
当你将 **\/GL** 和 MSIL 模块传递给链接器，以实现可能最快的生成性能时，显式指定 **\/LTCG**。  
  
如需实现更快的性能，请使用 **\/LTCG:INCREMENTAL**。此选项通知链接器仅重新优化受到源文件更改影响的文件集，而不是重新优化整个项目。这可以显著减少所需的链接时间。此选项与增量链接选项不同。  
  
 **\/LTCG** 与 [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 一起使用无效。  
  
通过使用 [\/Og](../../build/reference/og-global-optimizations.md)、[\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、[\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 [\/Ox](../../build/reference/ox-full-optimization.md) 用 **\/LTCG** 链接编译的模块时，执行以下优化：  
  
-   跨模块内联  
  
-   程序间寄存器分配（仅限 64 位操作系统）  
  
-   自定义调用约定（仅限 x86）  
  
-   小 TLS 位移（仅限 x86）  
  
-   堆栈双倍对齐对齐（仅限 x86）  
  
-   改进的内存消歧（更好的全局变量和输入参数干扰信息）  
  
> [!NOTE]
> 链接器确定用于编译每个函数的优化，并在链接时间应用相同的优化。  
  
使用 **\/LTCG** 和 **\/Ogt** 会产生双倍字长对齐优化。  
  
如果指定 **\/LTCG** 和 **\/Ogs**，则不执行双倍字长对齐。如果应用程序中的大多数函数是为速度编译的，只有少数几个函数是为大小编译的（例如，通过使用 [optimize](../../preprocessor/optimize.md) 杂注），当这些为大小优化的函数调用需要双倍字长对齐的函数时，编译器会双倍字长对齐它们。  
  
如果编译器可标识函数的所有调用站点，则编译器会忽略函数上的显式调用约定修饰符并尝试优化函数的调用约定：  
  
-   在寄存器中传递参数  
  
-   重新将参数排序以对齐  
  
-   删除未使用的参数  
  
如果通过函数指针调用函数，或者在用 **\/GL** 编译的模块外部调用函数，则编译器不尝试优化函数的调用约定。  
  
> [!NOTE]
> 如果使用 **\/LTCG** 并重定义 mainCRTStartup，则应用程序可能在初始化全局对象之前执行与用户代码相关的不可预知的行为。有三种方法可以解决此问题：不重定义 mainCRTStartup、不使用 **\/LTCG** 编译包含 mainCRTStartup 的文件，或以静态方式初始化全局变量和对象。  
  
## \/LTCG 和 MSIL 模块  
指定 **\/LTCG** 时，使用 [\/GL](../../build/reference/gl-whole-program-optimization.md) 和 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译的模块可用作链接器的输入：  
  
-   **\/LTCG** 可接受本机对象文件、混合本机\/托管对象文件（使用 **\/clr** 编译）、纯对象文件（使用 **\/clr:pure** 编译）和安全对象文件（使用 **\/clr:safe** 编译）  
  
-   **\/LTCG** 可接受安全的 .netmodule，此文件可使用 Visual C\+\+ 中的 **\/clr:safe \/LN** 和任何其他 Visual Studio 编译器中的 **\/target:module** 创建。**\/clr** 不接受使用 **\/clr:pure** 或 **\/LTCG** 生成的 .Netmodule。  
  
-   \/LTCG:PGI 不接受使用 **\/GL** 和 **\/clr** 编译的本机模块，也不接受纯模块（使用 **\/clr:pure** 生成）  
  
#### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”对话框。 请参阅 [使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**“配置属性”**文件夹。  
  
3.  选择**“常规”**属性页。  
  
4.  修改“全程序优化”属性。  
  
您还可以将 **\/LTCG** 应用于特定生成，方法是选择**“生成”**，再选择菜单栏上的**“按配置优化”**，或者选择项目的快捷菜单上的“按配置优化”选项之一。  
  
#### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。  
  
## 请参阅  
[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)