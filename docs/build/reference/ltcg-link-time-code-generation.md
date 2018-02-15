---
title: "-LTCG （链接时间代码生成） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69e67755ce5015cdd63ad36625e71380a303d2d4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG（链接时间代码生成）
```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## <a name="remarks"></a>备注  
 : INCREMENTAL （可选）  
 指定链接器仅对组受编辑，而不是整个项目的文件适用全程序优化或链接时间代码生成 (LTCG)。 默认情况下，当指定 /LTCG，并且通过使用全程序优化链接整个项目未设置此标志。  
  
 : NOSTATUS &#124;: STATUS （可选）  
 指定链接器是否显示用来指示链接的完成百分比的进度指示器。 默认情况下不显示此状态信息。  
  
 : OFF （可选）  
 禁用链接时间代码生成。 此行为是在命令行上未指定 /LTCG 时相同。  
  
 : PGINSTRUMENT （可选）  
 此选项已弃用。 请改用**/LTCG**和**/GENPROFILE**或**/FASTGENPROFILE**生成的按配置文件优化的被检测的生成。  
  
 从检测过的运行中收集的数据用于创建优化的映像。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。 此选项的缩写形式是 /ltcg: pgi。  
  
 : PGOPTIMIZE （可选）  
 此选项已弃用。 请改用**/LTCG**和**/USEPROFILE**来生成优化的映像。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。 此选项的缩写形式是 /ltcg: pgo。  
  
 : PGUPDATE （可选）  
 此选项已弃用。 请改用**/LTCG**和**/USEPROFILE**来生成优化的映像。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。 此选项的缩写形式是 /LTCG:PGU。  
  
 /LTCG 选项通知链接器调用编译器并执行全程序优化。 你也可以执行按配置优化。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。  
  
 存在以下例外情况，你无法将链接器选项添加到 /LTCG 和未指定 /LTCG 和 /GENPROFILE 选项的以前的 PGO 初始化组合中的 /USEPROFILE 的 PGO 组合：  
  
-   [/BASE](../../build/reference/base-base-address.md)  
  
-   [/FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   /LTCG  
  
-   [/MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [/OUT](../../build/reference/out-output-file-name.md)  
  
-   [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [/PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 任何与 /LTCG 一起指定的链接器选项和 /GENPROFILE 选项以初始化 PGO 不需要指定你通过使用 /LTCG 和 /USEPROFILE; 在生成时它们是隐式。  
  
 本主题的其余部分将从链接时间代码生成方面讨论 /LTCG。  
  
 与默示 /LTCG [/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
 如果将它传递通过使用已编译的模块，链接器将调用链接时间代码生成**/GL**或 MSIL 模块 (请参阅[用作链接器输入的.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md))。 如果不显式指定**/LTCG**传递时， **/GL**或到链接器链接器最终的 MSIL 模块检测到此和通过重新启动链接**/LTCG**。 显式指定**/LTCG**传递时， **/GL**和生成到链接器以获得尽可能高的 MSIL 模块的性能。  
  
 为了更快的性能，使用**/LTCG： 增量**。 此选项通知链接器仅重新优化受到源文件更改影响的文件集，而不是重新优化整个项目。 这可以显著减少所需的链接时间。 这不是作为增量链接的相同选项。  
  
 **/LTCG**不是有效用于[/增量](../../build/reference/incremental-link-incrementally.md)。  
  
 当**/LTCG**用于链接使用编译的模块[/Og](../../build/reference/og-global-optimizations.md)， [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)，或[/Ox](../../build/reference/ox-full-optimization.md)，将执行以下优化：  
  
-   跨模块内联  
  
-   过程间的寄存器分配 （64 位操作系统仅）  
  
-   自定义调用约定 (仅限 x86)  
  
-   小 TLS 偏移量 (仅限 x86)  
  
-   堆栈双倍字长对齐 (仅限 x86)  
  
-   改进了的内存消除歧义 （更好的全局变量和输入的参数干扰信息）  
  
> [!NOTE]
>  链接器确定哪些优化用于编译每个函数，并在链接时应用相同的优化。  
  
 使用**/LTCG**和**/Ogt**导致双倍字长对齐优化。  
  
 如果**/LTCG**和**/Ogs**指定，则不执行双倍字长对齐。 如果大部分应用程序中的函数编译的速度，只有少数几个函数编译为大小 (例如，通过使用[优化](../../preprocessor/optimize.md)杂注)，编译器双对齐的函数，如果它们调用针对大小进行优化需要双倍字长对齐的函数。  
  
 如果编译器可标识函数的所有调用站点，编译器将忽略函数上的显式调用约定修饰符并尝试优化函数的调用约定：  
  
-   在寄存器中传递参数  
  
-   重新排列参数的对齐方式  
  
-   删除未使用的参数  
  
 如果函数通过指针调用某个函数，或通过使用编译的模块外部从调用的函数**/GL**，编译器不会尝试优化函数的调用约定。  
  
> [!NOTE]
>  如果你使用**/LTCG**并重定义 mainCRTStartup，你的应用程序可以与在初始化全局对象之前执行的用户代码相关的不可预知的行为。  有三种方法来解决此问题： 不重定义 mainCRTStartup、 不编译包含 mainCRTStartup 使用的文件**/LTCG**，或以静态方式初始化全局变量和对象。  
  
## <a name="ltcg-and-msil-modules"></a>/LTCG 和 MSIL 模块  
 指定 [/LTCG](../../build/reference/gl-whole-program-optimization.md) 时，使用 [/GL](../../build/reference/clr-common-language-runtime-compilation.md) 和 **/clr** 编译的模块可用作链接器的输入：  
  
-   **/LTCG**可接受本机对象文件和混合本机/托管对象文件 (使用编译的**/clr**)。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
-   /Ltcg: pgi 不接受使用编译的本机模块**/GL**和**/clr**  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **“配置属性”** 文件夹。  
  
3.  选择 **“常规”** 属性页。  
  
4.  修改  “全程序优化”属性。  
  
 您还可以将 **/LTCG** 应用于特定生成，方法是选择 **“生成”**，再选择菜单栏上的 **“按配置优化”** ，或者选择项目的快捷菜单上的“按配置优化”选项之一。  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)