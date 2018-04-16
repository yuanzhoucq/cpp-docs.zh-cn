---
title: 优化按配置文件 |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca4c79fd46954d59a8fdd892fabbd53d4bc985f
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="profile-guided-optimizations"></a>按配置文件优化

按配置文件优化可以优化输出文件，其中优化程序使用的数据是通过对 .exe 或 .dll 文件进行测试运行得到的。 这些数据表示程序在生产环境中可能采用的执行方式。

按配置优化才可用于 x86 或 x64 本机目标。 按配置优化不适用于在公共语言运行时运行的输出文件。 即使生成包含混合本机和托管代码的程序集 (通过使用**/clr**编译器选项)，也无法仅对本机代码使用按配置文件优化。 如果你尝试使用 IDE 中设置这些选项生成项目时，不会生成错误。

> [!NOTE]
> 通过分析测试运行收集的信息替代本可以生效如果指定的优化**/Ob**， **/Os**，或**/Ot**。 有关详细信息，请参阅[/Ob （内联函数扩展）](../../build/reference/ob-inline-function-expansion.md)和[/Os、 /Ot （代码大小优先、 代码速度优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>若要优化你的应用程序的步骤

若要使用按配置优化，请执行以下步骤优化你的应用程序：

- 编译一个或多个源代码文件与[/GL](../../build/reference/gl-whole-program-optimization.md)。

   使用生成每个模块**/GL**可以按配置优化测试运行，以捕获运行时行为过程检查。 按配置优化生成中的每个模块不需要使用编译**/GL**。 但是，只有这些模块编译与**/GL**是检测和更高版本可用于按配置优化。

- 使用链接[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)和[/GENPROFILE 或 /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。

   同时使用**/LTCG**和**/GENPROFILE**或**/FASTGENPROFILE**运行所检测的应用时，创建.pgd 文件。 将测试运行数据添加到该 .pgd 文件后，该文件可以用作下一个链接步骤（创建优化映像）的输入。 指定时**/GENPROFILE**，你可以选择添加**PGD =**_filename_参数来指定非默认名称或使用.pgd 文件的位置。 组合**/LTCG**和**/GENPROFILE**或**/FASTGENPROFILE**链接器选项将替换不推荐使用**/ltcg: pginstrument**链接器选项。

- 分析应用程序。

   每次进行事件探查的 EXE 会话结束或经过分析的 DLL 被卸载， *appname*！ #.pgc 文件创建。 .pgc 文件包含特定应用程序测试运行的相关信息。 # 是从即会递增基于其他数目的 1 开始的数字*appname*！ #.pgc 文件的目录中。 如果测试运行表示的不是你想要优化的方案，则可以删除对应的 .pgc 文件。

   在测试期间运行，你可以强制关闭当前打开的.pgc 文件，并创建新的.pgc 文件与[pgosweep](../../build/reference/pgosweep.md)实用程序 （例如，当测试方案的结束与应用程序的关闭不同时）。

   你的应用程序还可直接调用 PGO 函数[PgoAutoSweep](pgoautosweep.md)，以捕获为对应的.pgc 文件进行调用的配置文件数据。 这可让你更好地控制涵盖的.pgc 文件中捕获的数据的代码。 有关如何使用此函数的示例，请参阅[PgoAutoSweep](pgoautosweep.md)文档。

   创建时检测的生成，默认情况下，数据收集完成在非线程安全模式下，其速度更快，但可能不完全准确。 通过使用**EXACT**参数**/GENPROFILE**或**/FASTGENPROFILE**，你可以指定在线程安全模式下，但速度较慢更准确的数据收集。 此选项也是将不推荐使用[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)环境变量，或不推荐使用**/POGOSAFEMODE**链接器选项，当你创建检测的生成。

- 使用链接**/LTCG**和**/USEPROFILE**。

   同时使用**/LTCG**和[/USEPROFILE](useprofile.md)链接器选项以创建优化的映像。 此步骤使用 .pgd 文件作为输入。 当指定**/USEPROFILE**，你可以选择添加**PGD =**_filename_参数来指定非默认名称或使用.pgd 文件的位置。 你还可以指定通过使用不推荐使用此名称**/PGD**链接器选项。 组合**/LTCG**和**/USEPROFILE**替换不推荐使用**/ltcg: pgoptimize**和**/LTCG:PGUPDATE**链接器选项。

甚至可能会在创建了优化输出文件之后，才发现可以进行附加分析以创建更为优化的映像。 如果检测到的映像及其.pgd 文件可用，你可以执行附加测试运行，并使用较新的.pgd 文件重新生成优化的映像，使用相同的**/LTCG**和**/USEPROFILE**链接器选项.

## <a name="optimizations-performed-by-pgo"></a>由 PGO 执行的优化

以下是按配置文件优化的列表：

- **内联**-例如，如果存在函数 A 频繁调用函数 B，并且函数 B 相对较小，则按配置优化将将函数 B 内联在函数 a。

- **虚调用推理**-如果某个虚调用或其他通过函数指针的调用频繁将目标为特定函数，配置文件优化可以将插入频繁设定为目标的函数，有条件地执行的直接调用并且可以内联该直接调用。

- **寄存器分配**-优化与配置文件数据会导致更好的寄存器分配。

- **基本块优化**-基本块优化，可以暂时在给定框架放入同一组页面 （区域） 内执行的经常执行基本块。 这样可以让使用的页数减至最少，从而使内存开销最少。

- **大小/速度优化**-耗费大量时间程序的函数可以优化以加快速度。

- **函数布局**-根据调用关系图和分析调用方/被调用方行为，将倾向于沿相同路径执行的函数放在相同的部分。

- **条件分支优化**-使用值探测，按配置文件优化可以确定 switch 语句中的给定的值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以对 if/else 指令执行相同操作，这时，优化程序可以对 if/else 进行排序，以便根据哪个块为 true 的频率更高，将 if 块或 else 块放在最前面。

- **死代码分隔**-分析过程中没有调用的代码移到到一组段的末尾追加一个特殊的段。 这可以有效地将该段排除在常用页面之外。

- **EH 代码分隔**-通常将这些代码执行，可以移到一个单独的段中，按配置优化可以确定仅在异常条件会发生异常时。

- **内存内部函数**-内部函数的扩展可以更好地决定，如果它可以确定是否被频繁调用内部函数。 也可根据移动或复制的块大小对内部函数进行优化。

如果你使用 Visual Studio 2013，则可以使用自动[按配置文件的优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)性能和诊断中心，以简化 Visual Studio 中的优化过程中的 Visual c + +。 此插件在中不可用更高版本的 Visual Studio。

## <a name="next-steps"></a>后续步骤

有关这些环境变量、 函数和工具可以使用按配置优化中阅读的详细信息：

[用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
这些变量可用来指定运行时行为的测试方案。 新的链接器选项; 已弃用它们读取此项可帮助你将从环境变量移到链接器选项。

[PgoAutoSweep](pgoautosweep.md)<br/>
你可以将其添加到您的应用程序，以提供细粒度的.pgc 文件数据捕获控制一个函数。

[pgosweep](../../build/reference/pgosweep.md)<br/>
将所有配置文件数据的.pgc 文件，写入一个命令行实用工具关闭.pgc 文件，并打开新的.pgc 文件。

[pgomgr](../../build/reference/pgomgr.md)<br/>
命令行实用工具，将配置文件数据从一个或多个对应的.pgc 文件添加到该.pgd 文件的说明。

[如何： 合并多个 PGO 配置文件合并到一个配置文件](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)的示例**pgomgr**使用情况。

## <a name="see-also"></a>请参阅

[C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)
