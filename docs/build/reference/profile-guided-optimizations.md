---
title: "按配置文件优化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "优化, 按配置文件 [C++]"
  - "按配置文件优化"
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# 按配置文件优化
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

按配置文件优化可以优化输出文件，其中优化程序使用的数据是通过对 .exe 或 .dll 文件进行测试运行得到的。  这些数据表示程序在生产环境中可能采用的执行方式。  
  
 按配置优化仅可用于 x86 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 本机目标。  对于将在公共语言运行时上运行的输出文件，按配置文件优化不可用。  即使生成包含混合本机代码和托管代码的程序集（使用 **\/clr** 进行编译），也无法仅对本机代码使用按配置文件优化。  如果尝试使用 IDE 中设置的这些选项生成项目，将导致生成错误。  
  
> [!NOTE]
>  如果指定 **\/Ob**、**\/Os** 或 **\/Ot**，则通过分析测试运行收集的信息会替代本可以生效的优化。  有关详细信息，请参阅 [\/Ob（内联函数展开）](../../build/reference/ob-inline-function-expansion.md)和 [\/Os、\/Ot（代码大小优先、代码速度优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  
  
 你可以使用性能和诊断中心中的适用于 Visual C\+\+ 的按配置文件优化自动插件，以简化 Visual Studio 中的优化过程，你也可以在 Visual Studio 或命令行中手动执行优化步骤。  我们推荐此插件的原因在于它易于使用。  有关如何获取该插件并使用它来优化应用的信息，请参阅[按配置优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)。  
  
 按配置文件优化插件和手动按配置文件优化均按照以下步骤优化你的应用：  
  
-   使用 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译一个或多个源代码文件。  
  
     对于每个使用 \/GL 生成的模块，都可以在按配置文件优化测试运行过程中对其进行检查，以捕获运行时行为。  按配置文件优化生成中的每个模块都不需要使用 \/GL 进行编译。  但是，只会检测使用 \/GL 进行编译的模块，且只有这些模块才能在以后用于按配置文件优化。  
  
-   使用 [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) 进行链接。  
  
     \/LTCG:PGINSTRUMENT 会创建一个空的 .pgd 文件。  将测试运行数据添加到该 .pgd 文件后，该文件可以用作下一个链接步骤（创建优化映像）的输入。  指定 \/LTCG:PGINSTRUMENT 时，可以选择使用 .pgd 文件的非默认名称或位置来指定 [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)。  
  
-   分析应用程序。  
  
     每次结束经过分析的 EXE 会话或卸载经过分析的 DLL 时，都会创建一个 *appname*\!\#.pgc 文件。  .pgc 文件包含特定应用程序测试运行的相关信息。  \# 是从 1 开始的数字，它基于目录中的其他 *appname*\!\#.pgc 文件的个数递增。  如果测试运行表示的不是你想要优化的方案，则可以删除对应的 .pgc 文件。  
  
     在测试运行过程中，你可以使用 [pgosweep](../../build/reference/pgosweep.md) 实用工具强制关闭当前打开的 .pgc 文件，并创建一个新的 .pgc 文件（例如，当测试方案的结束与应用程序的关闭不一致时）。  
  
     在分析应用程序时，可以使用 `PogoSafeMode` 选项。  使用此选项可以指定是以安全模式还是以快速模式对应用程序进行分析。  有关这两种模式的详细信息，请参阅 [PogoSafeMode](../../build/reference/pogosafemode.md)。  
  
-   使用 \/LTCG:PGOPTIMIZE 进行链接。  
  
     \/LTCG:PGOPTIMIZE 创建优化映像。  此步骤使用 .pgd 文件作为输入。  有关详细信息，请参阅 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 甚至可能会在创建了优化输出文件之后，才发现可以进行附加分析以创建更为优化的映像。  如果检测到的映像及其 .pgd 文件可用，则可以执行附加测试运行，并使用较新的 .pgd 文件重新生成优化映像。  
  
 以下是按配置文件优化的列表：  
  
-   **内联**：例如，如果存在频繁调用函数 B 的函数 A，且函数 B 相对较小，则按配置文件优化会将函数 B 内联到函数 A 中。  
  
-   **虚调用推理**：如果某个虚调用或其他通过函数指针的调用频繁将目标设定为特定函数，则按配置文件优化可以将一个按条件执行的直接调用插入这个被频繁设定为目标的函数，并且可以内联该直接调用。  
  
-   **寄存器分配**：使用配置文件数据进行优化，可以实现更好的寄存器分配。  
  
-   **基本块优化**：使用基本块优化，可以将暂时在给定框架内执行的经常执行的基本块放在同一组页面（区域）中。  这样可以让使用的页数减至最少，从而使内存开销最少。  
  
-   **大小\/速度优化**：对于耗费程序大量时间的函数，可以对其进行优化以加快速度。  
  
-   **函数布局**：根据调用关系图和经过分析的调用方\/被调用方行为，将倾向于沿相同路径执行的函数放在同一段中。  
  
-   **条件分支优化**：使用值探测，按配置文件优化可以确定 switch 语句中的给定值是否比其他值更常用。  然后，可以从 switch 语句中取出此值。  可以对 if\/else 指令执行相同操作，这时，优化程序可以对 if\/else 进行排序，以便根据哪个块为 true 的频率更高，将 if 块或 else 块放在最前面。  
  
-   **死代码分隔**：将分析过程中没有调用的代码移到一个特殊的段中，该段附加在一组段的末尾。  这可以有效地将该段排除在常用页面之外。  
  
-   **EH 代码分隔**：EH 代码在发生异常时执行；如果按配置条件优化可以确定仅在异常条件下才会发生异常，则通常可以将这些代码移到一个单独的段中。  
  
-   **内存内部函数**：如果能够确定是否频繁调用了某个内部函数，就可以更好地确定内部函数的扩展。  也可根据移动或复制的块大小对内部函数进行优化。  
  
 有关在 IDE 或命令行中执行手动优化的详细信息，请参阅[演练：使用按配置文件优化](http://msdn.microsoft.com/zh-cn/6e36421b-ec8c-4626-9c29-fa5ffb6f27f8)。  
  
## 本节内容  
 [按配置优化插件](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [用于按配置文件优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [如何：将多个 PGO 配置文件合并成一个配置文件](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## 请参阅  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)