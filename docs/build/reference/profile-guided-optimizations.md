---
title: 优化按配置文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4914b809e8e88ca07cf97af2f4d5405087cf549
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417405"
---
# <a name="profile-guided-optimizations"></a>按配置文件优化

按配置文件优化可以优化输出文件，其中优化程序使用的数据是通过对 .exe 或 .dll 文件进行测试运行得到的。 这些数据表示程序在生产环境中可能采用的执行方式。

按配置优化在内仅适用于 x86 或 x64 本机目标。 按配置优化不是适用于在公共语言运行时运行的输出文件。 即使生成包含混合本机和托管代码程序集 (通过使用 **/clr**编译器选项)，不能仅对本机代码中使用的按配置优化。 如果你尝试通过在 IDE 中设置这些选项生成一个项目，会生成错误。

> [!NOTE]
> 通过分析测试运行收集的信息将覆盖本应有效如果指定的优化 **/Ob**， **/Os**，或 **/Ot**。 有关详细信息，请参阅[/Ob （内联函数展开）](../../build/reference/ob-inline-function-expansion.md)并[/Os、 /Ot （代码大小优先、 代码速度优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>优化您的应用程序的步骤

若要使用的按配置优化，请执行以下步骤优化你的应用：

- 编译一个或多个源代码文件与[/GL](../../build/reference/gl-whole-program-optimization.md)。

   使用生成的每个模块 **/GL**期间的按配置优化测试运行，以捕获运行时行为可检查。 配置文件优化生成中的每个模块无需使用编译 **/GL**。 但是，只有这些模块编译 **/GL**是检测和更高版本可用于按配置优化。

- 使用链接[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)并[/GENPROFILE 或 /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。

   同时使用这二者 **/LTCG**并 **/GENPROFILE**或 **/FASTGENPROFILE**运行所检测的应用时创建一个.pgd 文件。 将测试运行数据添加到该 .pgd 文件后，该文件可以用作下一个链接步骤（创建优化映像）的输入。 指定时 **/GENPROFILE**，你可以选择添加**PGD =**_文件名_参数，以指定非默认名称或.pgd 文件的位置。 组合 **/LTCG**并 **/GENPROFILE**或 **/FASTGENPROFILE**链接器选项将替换不推荐使用 **/ltcg: pginstrument**链接器选项。

- 分析应用程序。

   每次进行事件探查的 EXE 会话结束或经过分析的 DLL 已被卸载， *appname*！ #.pgc 文件创建。 .pgc 文件包含特定应用程序测试运行的相关信息。 # 是一个基于其他数都将递增 1 开始的数字*appname*！ #.pgc 文件的目录中。 如果测试运行表示的不是你想要优化的方案，则可以删除对应的 .pgc 文件。

   测试运行期间，您可以强制关闭当前打开的.pgc 文件并创建新的.pgc 文件与[pgosweep](../../build/reference/pgosweep.md)实用程序 （例如，当与应用程序关闭不同时测试方案的末尾）。

   你的应用程序可以直接调用 PGO 函数时， [PgoAutoSweep](pgoautosweep.md)、 捕获为.pgc 文件进行调用的配置文件数据。 这可以提供更好地控制涵盖的.pgc 文件中捕获的数据的代码。 有关如何使用此函数的示例，请参阅[PgoAutoSweep](pgoautosweep.md)文档。

   创建时检测的生成，默认情况下，数据收集完成非线程安全模式，其速度更快但可能不完全准确。 通过使用**EXACT**自变量 **/GENPROFILE**或 **/FASTGENPROFILE**，可以指定在线程安全模式，这是速度较慢但更准确的数据收集。 此选项也是可用设置已弃用[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)环境变量，或已弃用 **/POGOSAFEMODE**时创建检测的生成链接器选项。

- 使用链接 **/LTCG**并 **/USEPROFILE**。

   同时使用这两者 **/LTCG**并[/USEPROFILE](useprofile.md)链接器选项来创建优化的映像。 此步骤使用 .pgd 文件作为输入。 当指定 **/USEPROFILE**，你可以选择添加**PGD =**_文件名_参数，以指定非默认名称或.pgd 文件的位置。 此外可以指定此名称使用已弃用 **/PGD**链接器选项。 组合 **/LTCG**并 **/USEPROFILE**替换弃用 **/ltcg: pgoptimize**并 **/LTCG:PGUPDATE**链接器选项。

甚至可能会在创建了优化输出文件之后，才发现可以进行附加分析以创建更为优化的映像。 如果已检测的映像和及其.pgd 文件，则可以执行其他测试运行并使用更新的.pgd 文件重新生成优化的映像，使用相同的 **/LTCG**并 **/USEPROFILE**链接器选项.

## <a name="optimizations-performed-by-pgo"></a>执行 PGO 优化

以下是按配置文件优化的列表：

- **内联**-例如，如果存在频繁调用函数 B，并且函数 B 相对较小，则按配置优化将将函数 B 内联函数 A.中的一个函数

- **虚调用推理**-如果某个虚调用或其他通过函数指针调用频繁将目标为特定函数，配置文件优化可以将插入这个经常指向的函数，有条件地执行直接调用和直接调用可以进行内联。

- **寄存器分配**-使用配置文件数据会导致更好的寄存器分配优化。

- **基本块优化**-基本块优化，可以暂时在给定的框架，放置在一组相同的页面 （区域） 内执行的常见的执行基本块。 这样可以让使用的页数减至最少，从而使内存开销最少。

- **大小/速度优化**-耗费大量时间程序函数可以优化速度。

- **函数布局**-根据调用关系图和分析调用方/被调用方行为倾向于沿相同路径执行的函数放在同一部分。

- **条件分支优化**-使用值探测，按配置文件优化可以确定 switch 语句中的给定的值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以对 if/else 指令执行相同操作，这时，优化程序可以对 if/else 进行排序，以便根据哪个块为 true 的频率更高，将 if 块或 else 块放在最前面。

- **死代码分隔**-在分析期间不会对其进行调用的代码移动到到组段的末尾追加一个特殊部分。 这可以有效地将该段排除在常用页面之外。

- **EH 代码分隔**-通常将这些代码执行，可以移到一个单独的段中，按配置优化可以确定仅在异常情况会发生异常时。

- **内存内部函数**-如果它可以确定是否频繁调用内部函数，则可以更好地决定内部函数的扩展。 也可根据移动或复制的块大小对内部函数进行优化。

如果使用 Visual Studio 2013，则可以使用自动化[配置文件优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)Visual c + + 中的性能和诊断中心，以简化 Visual Studio 中的优化过程。 此插件不在更高版本的 Visual Studio 中可用。

## <a name="next-steps"></a>后续步骤

有关这些环境变量、 函数和工具，可在按配置优化读取的详细信息：

[用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
这些变量可用于指定运行时行为的测试方案。 它们已弃用新链接器选项;阅读本文来帮助你将从环境变量移动到链接器选项。

[PgoAutoSweep](pgoautosweep.md)<br/>
可以向应用提供细粒度的.pgc 文件数据捕获控件添加一个函数。

[pgosweep](../../build/reference/pgosweep.md)<br/>
将所有配置文件数据写入到的.pgc 文件，一个命令行实用程序关闭的.pgc 文件，并打开一个新的.pgc 文件。

[pgomgr](../../build/reference/pgomgr.md)<br/>
命令行实用工具，将配置文件数据从一个或多个.pgc 文件添加到该.pgd 文件的说明。

[如何：将多个 PGO 配置文件合并成一个配置文件](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
示例**pgomgr**使用情况。

## <a name="see-also"></a>请参阅

[C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)
