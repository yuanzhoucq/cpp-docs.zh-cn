---
title: "优化按配置文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2d72ddda460a88830f7f7692f4c9707fa3101a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimizations"></a>按配置文件优化
按配置文件优化可以优化输出文件，其中优化程序使用的数据是通过对 .exe 或 .dll 文件进行测试运行得到的。 这些数据表示程序在生产环境中可能采用的执行方式。  
  
 按配置优化仅可用于 x86 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 本机目标。 对于将在公共语言运行时上运行的输出文件，按配置文件优化不可用。 即使生成包含混合本机和托管代码的程序集 (使用编译**/clr**)，也无法仅对本机代码使用按配置文件优化。 如果尝试使用 IDE 中设置的这些选项生成项目，将导致生成错误。  
  
> [!NOTE]
>  通过分析测试运行收集的信息会替代本可以生效如果指定的优化**/Ob**， **/Os**，或**/Ot**。 有关详细信息，请参阅[/Ob （内联函数扩展）](../../build/reference/ob-inline-function-expansion.md)和[/Os、 /Ot （代码大小优先、 代码速度优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  
  
 你可以使用性能和诊断中心中的适用于 Visual C++ 的按配置文件优化自动插件，以简化 Visual Studio 中的优化过程，你也可以在 Visual Studio 或命令行中手动执行优化步骤。 我们推荐此插件的原因在于它易于使用。 有关如何获取该插件并使用它来优化您的应用程序的信息，请参阅[按配置文件的优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
 按配置文件优化插件和手动按配置文件优化均按照以下步骤优化你的应用：  
  
-   编译一个或多个源代码文件与[/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
     对于每个使用 /GL 生成的模块，都可以在按配置文件优化测试运行过程中对其进行检查，以捕获运行时行为。 按配置文件优化生成中的每个模块都不需要使用 /GL 进行编译。 但是，只会检测使用 /GL 进行编译的模块，且只有这些模块才能在以后用于按配置文件优化。  
  
-   使用链接[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)和[/GENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。  
  
     使用 /LTCG 和 /GENPROFILE 创建一个空的.pgd 文件。 将测试运行数据添加到该 .pgd 文件后，该文件可以用作下一个链接步骤（创建优化映像）的输入。 在指定 /GENPROFILE 时，你可以选择添加： PGD =`filename`来指定非默认名称或使用.pgd 文件的位置。  
  
-   分析应用程序。  
  
     每次进行事件探查的 EXE 会话结束或经过分析的 DLL 被卸载， *appname*！ #.pgc 文件创建。 .pgc 文件包含特定应用程序测试运行的相关信息。 # 是从即会递增基于其他数目的 1 开始的数字*appname*！ #.pgc 文件的目录中。 如果测试运行表示的不是你想要优化的方案，则可以删除对应的 .pgc 文件。  
  
     在测试期间运行，你可以强制关闭当前打开的.pgc 文件，并创建新的.pgc 文件与[pgosweep](../../build/reference/pgosweep.md)实用程序 （例如，当测试方案的结束与应用程序的关闭不同时）。  
  
     在分析应用程序时，可以使用 `PogoSafeMode` 选项。 使用此选项可以指定是以安全模式还是以快速模式对应用程序进行分析。 有关这些模式的详细信息，请参阅[PogoSafeMode](../../build/reference/pogosafemode.md)。  
  
-   使用 /LTCG 和 /USEPROFILE 进行链接。  
  
     使用 /LTCG 和 /USEPROFILE 创建优化的映像。 此步骤使用 .pgd 文件作为输入。 在指定 /USEPROFILE 时，你可以选择添加： PGD =`filename`来指定非默认名称或使用.pgd 文件的位置。 有关详细信息，请参阅[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 甚至可能会在创建了优化输出文件之后，才发现可以进行附加分析以创建更为优化的映像。 如果检测到的映像及其 .pgd 文件可用，则可以执行附加测试运行，并使用较新的 .pgd 文件重新生成优化映像。  
  
 以下是按配置文件优化的列表：  
  
-   **内联**-例如，如果存在函数 A 频繁调用函数 B，并且函数 B 相对较小，则按配置优化将将函数 B 内联在函数 a。  
  
-   **虚调用推理**-如果某个虚调用或其他通过函数指针的调用频繁将目标为特定函数，配置文件优化可以将插入频繁设定为目标的函数，有条件地执行的直接调用并且可以内联该直接调用。  
  
-   **寄存器分配**-优化与配置文件数据会导致更好的寄存器分配。  
  
-   **基本块优化**-基本块优化，可以暂时在给定框架放入同一组页面 （区域） 内执行的经常执行基本块。 这样可以让使用的页数减至最少，从而使内存开销最少。  
  
-   **大小/速度优化**-耗费大量时间程序的函数可以优化以加快速度。  
  
-   **函数布局**-根据调用关系图和分析调用方/被调用方行为，将倾向于沿相同路径执行的函数放在相同的部分。  
  
-   **条件分支优化**-使用值探测，按配置文件优化可以确定 switch 语句中的给定的值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以对 if/else 指令执行相同操作，这时，优化程序可以对 if/else 进行排序，以便根据哪个块为 true 的频率更高，将 if 块或 else 块放在最前面。  
  
-   **死代码分隔**-分析过程中没有调用的代码移到到一组段的末尾追加一个特殊的段。 这可以有效地将该段排除在常用页面之外。  
  
-   **EH 代码分隔**-通常将这些代码执行，可以移到一个单独的段中，按配置优化可以确定仅在异常条件会发生异常时。  
  
-   **内存内部函数**-内部函数的扩展可以更好地决定，如果它可以确定是否被频繁调用内部函数。 也可根据移动或复制的块大小对内部函数进行优化。  
  
 执行手动优化在 IDE 中或在命令行上的详细信息，请参阅[按配置文件的优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [按配置优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [用于按配置文件手动优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [如何：将多个 PGO 配置文件合并成一个配置文件](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)