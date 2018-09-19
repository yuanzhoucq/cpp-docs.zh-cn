---
title: /LTCG （链接时间代码生成） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e60bb086adbb1c573b21cafb54c61203c888e9a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725161"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG（链接时间代码生成）

使用 **/LTCG**执行全程序优化或用于创建配置文件按配置优化 (PGO) 检测、 进行培训，并创建配置文件引导式优化生成。

## <a name="syntax"></a>语法

> **/LTCG**[**:**{**增量**|**NOSTATUS**|**状态**|**OFF**}]<br/>

这些选项是从 Visual Studio 2015 开始已弃用的：

> **/LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>自变量

**增量**<br/>
（可选）指定链接器仅向受影响的编辑，而不是整个项目文件的一套适用全程序优化或链接时间代码生成 (LTCG)。 默认情况下，此标志未设置何时 **/LTCG**指定，并且通过使用全程序优化链接整个项目。

**NOSTATUS** &AMP;#124; **状态**<br/>
（可选）指定链接器是否显示进度指示器，显示的链接百分比已完成。 默认情况下不显示此状态信息。

**关闭**<br/>
（可选）禁用链接时间代码生成。 此行为是时也是如此 **/LTCG**未指定命令行上。

**PGINSTRUMENT**<br/>
（可选）从 Visual Studio 2015 开始，不建议使用此选项。 请改用 **/LTCG**并[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)生成的按配置优化检测的生成。 从检测过的运行中收集的数据用于创建优化的映像。 有关详细信息，请参阅[按配置优化](profile-guided-optimizations.md)。 此选项的缩写形式是 **/ltcg: pgi**。

**PGOPTIMIZE**<br/>
（可选）从 Visual Studio 2015 开始，不建议使用此选项。 请改用 **/LTCG**并[/USEPROFILE](useprofile.md)来生成优化的映像。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。 此选项的缩写形式是 **/ltcg: pgo**。

**PGUPDATE**<br/>
（可选）从 Visual Studio 2015 开始，不建议使用此选项。 请改用 **/LTCG**并 **/USEPROFILE**重新生成优化的映像。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。 此选项的缩写形式是 **/ltcg: pgu**。

## <a name="remarks"></a>备注

**/LTCG**选项通知链接器调用编译器并执行全程序优化。 你也可以执行按配置优化。 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。

使用以下例外情况，不能将链接器选项添加到的 PGO 组合 **/LTCG**并 **/USEPROFILE**的以前的 PGO 初始化组合中不指定 **/LTCG**并 **/GENPROFILE**选项：

- [/BASE](../../build/reference/base-base-address.md)

- [/FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

与指定的任何链接器选项 **/LTCG**并 **/GENPROFILE**选项以初始化 PGO 无需指定通过使用生成 **/LTCG**和 **/USEPROFILE**; 它们隐式。

这篇文章的其余部分将讨论 **/LTCG**链接时间代码生成方面。

**/LTCG**与隐式[/GL](../../build/reference/gl-whole-program-optimization.md)。

如果它传递通过使用已编译的模块，链接器将调用链接时间代码生成 **/GL**或 MSIL 模块 (请参阅[用作链接器输入的.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md))。 如果未显式指定 **/LTCG**时将传递 **/GL**或 MSIL 模块到链接器链接器最终会检测到这，并通过重新启动链接 **/LTCG**。 显式指定 **/LTCG**时将传递 **/GL**和 MSIL 模块到可能最快的链接器生成性能。

为了实现更快的性能，使用 **/LTCG： 增量**。 此选项通知链接器仅重新优化受到源文件更改影响的文件集，而不是重新优化整个项目。 这可以显著减少所需的链接时间。 这不是作为增量链接的相同选项。

**/LTCG**不是有效用于[/incremental](../../build/reference/incremental-link-incrementally.md)。

当 **/LTCG**用于链接使用编译的模块[/Og](../../build/reference/og-global-optimizations.md)， [/o1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/o2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)，或[/Ox](../../build/reference/ox-full-optimization.md)、将执行以下优化：

- 跨模块内联

- 过程间寄存器分配 （仅 64 位操作系统的系统）

- 自定义调用约定 (仅限 x86)

- 小 TLS 位移 (仅限 x86)

- 堆栈双倍字长对齐 (仅限 x86)

- 改进了的内存消除歧义 （更好的全局变量和输入的参数干扰信息）

> [!NOTE]
> 链接器确定哪些优化，用于编译每个函数，并在链接时应用相同的优化。

使用 **/LTCG**并 **/Ogt**导致双倍字长对齐优化。

如果 **/LTCG**并 **/Ogs**指定，则不执行双倍字长对齐。 如果大部分应用程序中的函数编译为速度、 的少数几个函数编译为大小 (例如，通过使用[优化](../../preprocessor/optimize.md)杂注)，编译器双对齐它们调用针对大小进行了优化的函数需要双倍字长对齐的函数。

如果编译器可标识函数的所有调用站点，编译器将忽略函数上的显式调用约定修饰符并尝试优化函数的调用约定：

- 在寄存器中传递参数

- 重新排列参数的对齐方式

- 删除未使用的参数

如果通过函数指针，调用的函数或函数从调用通过使用编译的模块外部 **/GL**，编译器不会尝试优化函数的调用约定。

> [!NOTE]
> 如果您使用 **/LTCG**重新定义`mainCRTStartup`，应用程序可以具有不可预知的行为与用户代码在初始化全局对象之前执行的相关联。 有三种方法要解决此问题： 不能重新定义`mainCRTStartup`，不编译包含的文件`mainCRTStartup`通过使用 **/LTCG**，或以静态方式初始化全局变量和对象。

### <a name="ltcg-and-msil-modules"></a>/LTCG 和 MSIL 模块

指定 [/LTCG](../../build/reference/gl-whole-program-optimization.md) 时，使用 [/GL](../../build/reference/clr-common-language-runtime-compilation.md) 和 **/clr** 编译的模块可用作链接器的输入：

- **/LTCG**可接受本机对象文件和混合本机/托管对象文件 (通过使用编译 **/clr**)。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

- **/Ltcg: pgi**不接受使用编译的本机模块 **/GL**和 **/clr**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **常规**属性页。

1. 修改  “全程序优化”属性。

您还可以应用 **/LTCG**于通过选择特定生成**构建** > **按配置优化**在菜单栏上，或通过选择其中一个配置文件在项目的快捷菜单上的引导式的优化选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
