---
title: 按配置优化
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857331"
---
# <a name="profile-guided-optimizations"></a>按配置优化

按配置优化 (PGO)，可以优化整个可执行文件，其中，优化器使用的.exe 或.dll 文件的测试运行中的数据。 数据表示程序在生产环境中可能存在性能。

按配置优化在内仅适用于 x86 或 x64 本机目标。 按配置优化不适用于在公共语言运行时运行的可执行文件。 即使生成包含混合本机和托管代码程序集 (通过使用 **/clr**编译器选项)，不能仅对本机代码中使用的按配置优化。 如果你尝试通过在 IDE 中设置这些选项生成一个项目，会生成错误。

> [!NOTE]
> 通过分析测试运行收集的信息将覆盖本应有效如果指定的优化 **/Ob**， **/Os**，或 **/Ot**。 有关详细信息，请参阅[/Ob （内联函数展开）](reference/ob-inline-function-expansion.md)并[/Os、 /Ot （代码大小优先、 代码速度优先）](reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>优化您的应用程序的步骤

若要使用的按配置优化，请执行以下步骤优化你的应用：

- 编译一个或多个源代码文件与[/GL](reference/gl-whole-program-optimization.md)。

   使用生成的每个模块 **/GL**期间的按配置优化测试运行，以捕获运行时行为可检查。 配置文件优化生成中的每个模块无需使用编译 **/GL**。 但是，只有这些模块编译 **/GL**是检测和更高版本可用于按配置优化。

- 使用链接[/LTCG](reference/ltcg-link-time-code-generation.md)并[/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。

   同时使用这二者 **/LTCG**并 **/GENPROFILE**或 **/FASTGENPROFILE**创建`.pgd`文件所检测的应用运行时。 测试运行数据添加到后`.pgd`文件，它可以用作下一步的链接步骤 （创建优化的映像） 的输入。 指定时 **/GENPROFILE**，你可以选择添加**PGD =**_filename_参数来指定非默认名称或位置`.pgd`文件。 组合 **/LTCG**并 **/GENPROFILE**或 **/FASTGENPROFILE**链接器选项将替换不推荐使用 **/ltcg: pginstrument**链接器选项。

- 分析应用程序。

   每次进行事件探查的 EXE 会话结束，或经过分析的 DLL 已被卸载，`appname!N.pgc`创建文件。 一个`.pgc`文件包含有关特定应用程序测试运行的信息。 *appname*是您的应用程序的名称和*N*开头的数字将递增 1 基于数目的其他`appname!N.pgc`目录中的文件。 可以删除`.pgc`文件如果测试运行并不代表你想要优化的方案。

   在测试期间运行，你可以强制执行的当前打开的闭包`.pgc`文件，并创建一个新`.pgc`文件具有[pgosweep](pgosweep.md)实用程序 （例如，当测试方案的结束不同时与应用程序关闭）。

   你的应用程序可以直接调用 PGO 函数时， [PgoAutoSweep](pgoautosweep.md)，以捕获在作为调用的配置文件数据`.pgc`文件。 它可以为您提供更好地控制受中捕获的数据的代码在`.pgc`文件。 有关如何使用此函数的示例，请参阅[PgoAutoSweep](pgoautosweep.md)文档。

   创建时检测的生成，默认情况下，数据收集完成非线程安全模式，其速度更快但可能不精确。 通过使用**EXACT**自变量 **/GENPROFILE**或 **/FASTGENPROFILE**，可以指定数据收集在线程安全模式，这是更精确，但速度较慢。 此选项也是可用设置已弃用[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)环境变量，或已弃用 **/POGOSAFEMODE**时创建检测的生成链接器选项。

- 使用链接 **/LTCG**并 **/USEPROFILE**。

   同时使用这两者 **/LTCG**并[/USEPROFILE](reference/useprofile.md)链接器选项来创建优化的映像。 此步骤将作为输入`.pgd`文件。 当指定 **/USEPROFILE**，你可以选择添加**PGD =**_filename_参数来指定非默认名称或位置`.pgd`文件。 此外可以指定此名称使用已弃用 **/PGD**链接器选项。 组合 **/LTCG**并 **/USEPROFILE**替换弃用 **/ltcg: pgoptimize**并 **/LTCG:PGUPDATE**链接器选项。

它是甚至可以创建优化的可执行文件和更高版本确定其他分析可以用来创建更为优化的映像。 如果已检测的映像并将其`.pgd`文件是可用，则可以执行其他测试运行并重新生成优化的映像与较新`.pgd`文件，同一 **/LTCG**和 **/USEPROFILE**链接器选项。

## <a name="optimizations-performed-by-pgo"></a>执行 PGO 优化

按配置优化包括这些检查和改进：

- **内联**-例如，如果函数 A 频繁调用函数 B，而函数 B 相对较小，则按配置优化函数 B 内联在函数 a。

- **虚调用推理**-如果某个虚调用或其他通过函数指针调用频繁将目标为特定函数，配置文件优化可以将插入到常见的目标函数中，有条件地执行直接调用和直接调用可以进行内联。

- **寄存器分配**-优化基于配置文件数据更好的寄存器分配。

- **基本块优化**-基本块优化，可以暂时在给定的框架，放置在一组相同的页面 （区域） 内执行的常见的执行基本块。 它最小化使用页数，这样就会减少内存开销。

- **大小/速度优化**-耗费的函数，该程序执行时间最多可以优化速度。

- **函数布局**-根据调用关系图和分析调用方/被调用方行为倾向于沿相同路径执行的函数放在同一部分。

- **条件分支优化**-使用值探测，按配置文件优化可以确定 switch 语句中的给定的值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以使用实现相同`if`...`else`说明，优化器可以订购其中`if`...`else`因此，或者`if`或`else`块放在第一次，具体取决于哪个块的详细信息通常是 true。

- **死代码分隔**-不分析过程中调用的代码移动到一个特殊部分，其中追加到末尾的一节。 它可以有效地将本部分中的通常使用页。

- **EH 代码分隔**-仅特别执行因为 EH 代码时，它通常可以移到一个单独的段。 移动时按配置优化可以确定仅在异常情况会发生异常。

- **内存内部函数**-是否要展开内部函数或不依赖于它是否频繁调用。 也可根据移动或复制的块大小对内部函数进行优化。

## <a name="next-steps"></a>后续步骤

有关这些环境变量、 函数和工具，可在按配置优化读取的详细信息：

[按配置优化的环境变量](environment-variables-for-profile-guided-optimizations.md)<br/>
这些变量用于指定运行时行为的测试方案。 它们现在是已弃用，并替换为新链接器选项。 本文档演示如何将从环境变量移到链接器选项。

[PgoAutoSweep](pgoautosweep.md)<br/>
函数可以添加到应用以提供细粒度`.pgc`文件数据捕获控件。

[pgosweep](pgosweep.md)<br/>
写入到的所有配置文件数据的命令行实用工具`.pgc`文件，关闭`.pgc`文件，并打开一个新`.pgc`文件。

[pgomgr](pgomgr.md)<br/>
将配置文件数据从一个或多个添加的命令行实用工具`.pgc`文件到`.pgd`文件。

[如何：将多个 PGO 配置文件合并到单个配置文件](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
示例**pgomgr**使用情况。

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](reference/c-cpp-build-tools.md)
