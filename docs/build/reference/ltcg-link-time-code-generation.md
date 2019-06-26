---
title: /LTCG（链接时间代码生成）
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 1e33d62694fe782b1a1719fa3c5a36c6fb04670a
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400620"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG（链接时间代码生成）

使用 /LTCG 执行全程序优化，或者创建按配置优化 (PGO) 检测、执行训练并创建按配置优化的生成  。

## <a name="syntax"></a>语法

> **/LTCG**[ **:** {**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]

这些选项自 Visual Studio 2015 开始已弃用：

> **/LTCG:** {**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}

### <a name="arguments"></a>自变量

**INCREMENTAL**<br/>
（可选）指定链接器仅将全程序优化或链接时间代码生成 (LTCG) 应用于受编辑影响的文件集，而不是应用于整个项目。 默认情况下，在指定了 /LTCG 时不会设置此标志，且会通过使用全程序优化链接整个项目  。

**NOSTATUS** &#124; **STATUS**<br/>
（可选）指定链接器是否显示用来指示链接的完成百分比的进度指示器。 默认情况下不显示此状态信息。

**OFF**<br/>
（可选）禁用链接时代码生成。 此行为与在命令行上未指定 /LTCG 时的行为相同  。

**PGINSTRUMENT**<br/>
（可选）这些选项自 Visual Studio 2015 开始已弃用。 请改用 /LTCG 和 [/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 来生成按配置优化的检测的生成  。 从检测过的运行中收集的数据用于创建优化的映像。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。 此选项的缩写为 /LTCG:PGI  。

**PGOPTIMIZE**<br/>
（可选）这些选项自 Visual Studio 2015 开始已弃用。 请改用 /LTCG 和 [/USEPROFILE](useprofile.md) 来生成优化的映像  。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。 此选项的缩写为 /LTCG:PGO  。

**PGUPDATE**<br/>
（可选）这些选项自 Visual Studio 2015 开始已弃用。 请改用 /LTCG 和 /USEPROFILE 来重新生成优化的映像   。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。 此选项的缩写为 /LTCG:PGU  。

## <a name="remarks"></a>备注

/LTCG 选项通知链接器调用编译器并执行全程序优化  。 还可以执行按配置优化。 有关详细信息，请参阅[按配置优化](../profile-guided-optimizations.md)。

在以下例外情况中，无法将链接器选项添加到 /LTCG 和 /USEPROFILE 的 PGO 组合，这些组合未在 /LTCG 和 /GENPROFILE 选项之前的 PGO 初始化组合中指定     ：

- [/BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

在通过使用 /LTCG 和 /USEPROFILE 进行生成时，不需要指定与 /LTCG 和 /GENPROFILE 一起指定以初始化 PGO 的任何链接器选项，它们是隐含的     。

本文其余部分将从链接时间代码生成方面讨论 /LTCG  。

/LTCG 是使用 [/GL](gl-whole-program-optimization.md) 隐含的  。

如果将使用 /GL 编译的模块或 MSIL 模块传递给链接器，链接器将调用链接时代码生成（有关详细信息，请参阅[用作链接器输入的 .netmodule 文件](netmodule-files-as-linker-input.md)）  。 如果在将 /GL 或 MSIL 模块传递给链接器时未显式指定 /LTCG，链接器最终将检测到此问题并使用 /LTCG 重新启动链接    。 在将 /GL 和 MSIL 模块传递给链接器时，请显式指定 /LTCG，以获得尽可能高的生成性能   。

为了获得更高的性能，请使用 /LTCG:INCREMENTAL  。 此选项通知链接器仅重新优化受到源文件更改影响的文件集，而不是重新优化整个项目。 这可以显著减少所需的链接时间。 该选项与增量链接选项不同。

/LTCG 与 [/INCREMENTAL](incremental-link-incrementally.md) 一起使用无效  。

当 /LTCG 用于链接使用 [/Og](og-global-optimizations.md)、[/O1](o1-o2-minimize-size-maximize-speed.md)、[/O2](o1-o2-minimize-size-maximize-speed.md) 和 [/Ox](ox-full-optimization.md) 编译的模块时，将执行以下优化  ：

- 跨模块内联

- 过程间寄存器分配（仅限 64 位操作系统）

- 自定义调用约定（仅限 x86）

- 小型 TLS 置换（仅限 x86）

- 堆栈双倍字长对齐（仅限 x86）

- 改进了内存消歧（改善全局变量和输入参数的干扰信息）

> [!NOTE]
> 链接器确定编译每个函数时采用哪种优化并在链接时应用相同的优化。

使用 /LTCG 和 /Ogt 会产生双倍字长对齐优化   。

如果指定 /LTCG 和 /Ogs，则不执行双倍字长对齐   。 如果应用程序中的大多数函数针对速度进行了编译，只有少数几个函数针对大小进行了编译（例如，通过使用 [optimize](../../preprocessor/optimize.md) 杂注），则当这些函数调用需要双倍字长对齐的函数时，编译器将对针对进行了大小优化的函数进行双倍字长对齐。

如果编译器可标识函数的所有调用站点，编译器将忽略函数上的显式调用约定修饰符并尝试优化函数的调用约定：

- 在寄存器中传递参数

- 重新排列参数以进行对齐

- 删除未使用的参数

如果通过函数指针调用某个函数，或者在使用 /GL 编译的模块外部调用某个函数生成，则编译器不会尝试优化函数的调用约定  。

> [!NOTE]
> 如果使用 /LTCG 并重新定义 `mainCRTStartup`，则应用程序可能有与在初始化全局对象之前执行的用户代码相关的不可预知的行为  。 有三种方法可以解决此问题：不重新定义 `mainCRTStartup`、不使用 /LTCG 编译包含 `mainCRTStartup` 的文件，或以静态方式初始化全局变量和对象  。

### <a name="ltcg-and-msil-modules"></a>/LTCG 和 MSIL 模块

指定 [/LTCG](gl-whole-program-optimization.md) 时，使用 [/GL](clr-common-language-runtime-compilation.md) 和 **/clr** 编译的模块可用作链接器的输入：

- /LTCG 可以接受本机对象文件以及混合本机/托管对象文件（通过使用 /clr 编译的文件）   。 “/clr:pure”和“/clr:safe”编译器选项在 Visual Studio 2015 中已弃用，并且在 Visual Studio 2017 和更高版本中不受支持   。

- /LTCG:PGI 不接受使用 /GL 和 /clr 编译的本机模块   

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “常规”属性页   。

1. 修改  “全程序优化”属性。

还可以将 /LTCG 应用于特定生成，方法是选择菜单栏上的“生成” > “按配置优化”，或者选择项目的快捷菜单上的“按配置优化”选项之一    。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
