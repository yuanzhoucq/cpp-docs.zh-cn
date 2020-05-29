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

按配置优化 (PGO) 可以优化整个可执行文件，其中优化程序使用的数据是通过对 .exe 或 .dll 文件进行测试运行得到的。 这些数据表示程序在生产环境中的可能性能。

按配置优化仅可用于 x86 或 x64 本机目标。 对于在公共语言运行时上运行的可执行文件，按配置优化不可用。 即使生成包含混合本机代码和托管代码的程序集（使用 /clr  编译器选项），也无法仅对本机代码使用按配置优化。 如果尝试使用 IDE 中设置的这些选项生成项目，会导致生成错误。

> [!NOTE]
> 如果指定 /Ob  、/Os  或 /Ot  ，则通过分析测试运行收集的信息会重写本应生效的优化。 有关详细信息，请参阅 [/Ob（内联函数扩展）](reference/ob-inline-function-expansion.md)和 [/Os、/Ot（代码大小优先、代码速度优先）](reference/os-ot-favor-small-code-favor-fast-code.md)。

## <a name="steps-to-optimize-your-app"></a>优化应用的步骤

若要使用按配置优化，请按照以下步骤优化应用：

- 使用 [/GL](reference/gl-whole-program-optimization.md) 编译一个或多个源代码文件。

   对于每个使用 /GL  生成的模块，都可以在按配置优化测试运行过程中对其进行检查，以捕获运行时行为。 按配置优化生成中的每个模块都不需要使用 /GL  进行编译。 但是，只会检测使用 /GL  进行编译的模块，且只有这些模块才能在以后用于按配置优化。

- 使用 [/LTCG](reference/ltcg-link-time-code-generation.md) 和 [/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 进行链接。

   使用 /LTCG  和 /GENPROFILE  或 /FASTGENPROFILE  会在运行检测的应用时创建 `.pgd` 文件。 将测试运行数据添加到该 `.pgd` 文件后，该文件可以用作下一个链接步骤（创建优化映像）的输入。 指定 /GENPROFILE  时，可以选择添加 PGD=  filename  参数以指定 `.pgd` 文件的非默认名称或位置。 /LTCG  和 /GENPROFILE  或 /FASTGENPROFILE  链接器选项的组合替换了已弃用的 /LTCG:PGINSTRUMENT  链接器选项。

- 分析应用程序。

   每次结束经过分析的 EXE 会话或卸载经过分析的 DLL 时，都会创建一个 `appname!N.pgc` 文件。 `.pgc` 文件包含特定应用程序测试运行的相关信息。 appname  是应用的名称，而 N  是从 1 开始的数字，它基于目录中的其他 `appname!N.pgc` 文件的个数递增。 如果测试运行表示的不是你想要优化的方案，则可以删除对应的 `.pgc` 文件。

   在测试运行过程中，你可以使用 [pgosweep](pgosweep.md) 实用工具强制关闭当前打开的 `.pgc` 文件，并创建一个新的 `.pgc` 文件（例如，当测试方案的结束与应用程序的关闭不一致时）。

   应用程序还可以直接调用 PGO 函数 [PgoAutoSweep](pgoautosweep.md)，以将调用时的配置文件数据作为 `.pgc` 文件进行捕获。 它可以使你更好地控制 `.pgc` 文件中的捕获数据所涵盖的代码。 有关如何使用此函数的示例，请参阅 [PgoAutoSweep](pgoautosweep.md) 文档。

   创建检测生成时，默认情况下，数据收集在非线程安全模式下进行，该模式速度更快，但可能不精确。 通过对 /GENPROFILE  或 /FASTGENPROFILE  使用 EXACT  参数，可以指定在线程安全模式下进行数据收集，该模式更精确，但速度更慢。 如果在创建检测生成时，设置了已弃用的 [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) 环境变量或已弃用的 /POGOSAFEMODE  链接器选项，也可使用此选项。

- 使用 /LTCG  和 /USEPROFILE  进行链接。

   同时使用 /LTCG  和 [/USEPROFILE](reference/useprofile.md) 链接器选项可创建优化映像。 此步骤使用 `.pgd` 文件作为输入。 指定 /USEPROFILE  时，可以选择添加 PGD=  filename  参数以指定 `.pgd` 文件的非默认名称或位置。 还可以使用已弃用的 /PGD  链接器选项指定此名称。 /LTCG  和 /USEPROFILE  的组合替换了已弃用的 /LTCG:PGOPTIMIZE  和 /LTCG:PGUPDATE  链接器选项。

甚至可能会在创建了优化可执行文件之后，才发现可以进行附加分析以创建更为优化的映像。 如果检测到的映像及其 `.pgd` 文件可用，则可以执行附加测试运行，并使用较新的 `.pgd` 文件重新生成优化映像（使用相同的 /LTCG  和 /USEPROFILE  链接器选项）。

## <a name="optimizations-performed-by-pgo"></a>PGO 执行的优化

按配置优化包括以下检查和改进：

- 内联  - 例如，如果函数 A 频繁调用函数 B，且函数 B 相对较小，则按配置优化会将函数 B 内联到函数 A 中。

- 虚调用推理  - 如果某个虚调用或其他通过函数指针的调用频繁将目标设定为特定函数，则按配置优化可以将一个按条件执行的直接调用插入这个被频繁设定为目标的函数，并且可以内联该直接调用。

- 寄存器分配  - 使用配置文件数据进行优化，可以实现更好的寄存器分配。

- 基本块优化  - 使用基本块优化，可以将暂时在给定框架内执行的经常执行的基本块放在同一组页面（区域）中。 它可以让使用的页数减至最少，从而使内存开销最少。

- 大小/速度优化  - 对于耗费程序大多数执行时间的函数，可以对其进行优化以加快速度。

- 函数布局  - 根据调用关系图和经过分析的调用方/被调用方行为，将倾向于沿相同路径执行的函数放在同一段中。

- 条件分支优化  - 使用值探测，按配置优化可以确定 switch 语句中的给定值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以对 `if`...`else` 指令执行相同操作，这时，优化程序可以对 `if`...`else` 进行排序，以便根据哪个块为 true 的频率更高，将 `if` 块或 `else` 块放在最前面。

- 死代码分隔  - 将分析过程中没有调用的代码移到一个特殊的段中，该段附加在一组段的末尾。 它可以有效地将该段排除在常用页面之外。

- EH 代码分隔  - 由于 EH 代码仅在异常情况下执行，因此通常可以将它移动到单独的部分。 当按配置优化可以确定异常仅在异常条件下发生时，便会移动它。

- 内存内部函数  - 是否要展开内部函数取决于是否经常调用它。 也可根据移动或复制的块大小对内部函数进行优化。

## <a name="next-steps"></a>后续步骤

详细了解可在按配置优化中使用的环境变量、函数和工具：

[用于按配置优化的环境变量](environment-variables-for-profile-guided-optimizations.md)<br/>
这些变量用于指定测试方案的运行时行为。 它们现在已弃用，替换为新链接器选项。 本文档演示如何从环境变量转向链接器选项。

[PgoAutoSweep](pgoautosweep.md)<br/>
一个函数，可以添加到应用以提供细化 `.pgc` 文件数据捕获控制。

[pgosweep](pgosweep.md)<br/>
一个命令行实用工具，可将所有配置文件数据写入 `.pgc` 文件，关闭 `.pgc` 文件，然后打开新的 `.pgc` 文件。

[pgomgr](pgomgr.md)<br/>
一个命令行实用工具，可将一个或多个 `.pgc` 文件中的配置文件数据添加到 `.pgd` 文件。

[如何：将多个 PGO 配置文件合并成一个配置文件](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
pgomgr  用法的示例。

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](reference/c-cpp-build-tools.md)
