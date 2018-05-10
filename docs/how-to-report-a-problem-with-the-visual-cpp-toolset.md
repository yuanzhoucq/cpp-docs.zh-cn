---
title: 如何使用 Visual C++ 工具集报告问题 | Microsoft Docs
ms.date: 1/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8be0a5e42caf12c4e1415cf88143b84a9971cd2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>如何使用 Visual C++ 工具集报告问题

使用 Microsoft Visual C++ 编译器、链接器或其他工具和库时如果遇到问题，请告知我们。

最好是向我们发送报告，在报告中说明你所遇到的问题、如何生成程序的详细信息，以及重现（我们可用于在自己的计算机上重现该问题的完整测试用例）。 通过这些信息，我们可以快速验证问题是存在于我们的代码中还是你的本地环境中，判断它是否会影响其他版本的编译器，并诊断其原因。

在本文档中，你将了解到

- [如何准备报告](#how-to-prepare-your-report)，以及一篇优秀报告应包含哪些内容。

- [如何生成重现](#how-to-generate-a-repro)，以及不同类型的重现。

- [发送报告的方式](#ways-to-send-your-report)，以及如何让其与众不同。

无论对我们，还是对和你一样的其他开发者而言，你的报告都十分重要。 谢谢你帮助我们改进 Visual C++！

## <a name="how-to-prepare-your-report"></a>如何准备报告

创建高质量报告非常重要，因为如果缺少完整信息，我们很难在自己的计算机上重现所遇到的问题。 报告的质量越高，我们重新创建和诊断问题的效率就越高。

报告中应至少包括

- 正在使用的工具集的完整版本信息。

- 用于生成代码的完整 cl.exe 命令行。

- 对所遇到问题的详细描述。

- 重现：简单完整的自包含源代码示例，用于演示问题。

继续阅读，详细了解我们需要的特定信息，在何处可以找到它们，以及如何创建高质量重现。

### <a name="the-toolset-version"></a>工具集版本

我们需要引发问题的工具集的完整版本信息和目标体系结构，以便在我们的计算机上针对相同工具集测试你的重现。 如果我们可以重现此问题，我们还可以将此信息作为起点，调查哪些版本的工具集存在同样的问题。

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>报告你正在使用的编译器的完整版本

1. 打开与用于生成项目的 Visual Studio 版本和配置体系结构匹配的“开发人员命令提示”。 例如，如果在 x64 上使用 Visual Studio 2017 生成面向 x64 的项目，请选择“适用于 VS 2017 的 x64 本机工具命令提示”。 有关详细信息，请参阅[开发人员命令提示快捷方式](build/building-on-the-command-line.md#developer-command-prompt-shortcuts)。

1. 在“开发人员命令提示”控制台窗口中，输入命令 cl。

该输出应与以下类似：

```Output
C:\Users\username\Source>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x64
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

将整个输出复制并粘贴到报告。

### <a name="the-command-line"></a>命令行

我们需要用于生成代码的确切命令行（cl.exe 及其全部参数），以便以完全相同的方式在自己的计算机上生成它。 这一点很重要，因为你所遇到的问题可能仅在使用某一特定参数或参数组合生成时才存在。

此信息位于遇到问题后立即出现的生成日志中，建议在该位置查找。 这可确保命令行包含完全相同的参数，从而有可能帮助解决问题。

#### <a name="to-report-the-contents-of-the-command-line"></a>报告命令行的内容

1. 找到并打开 **CL.command.1.tlog** 文件。 默认情况下，此文件位于“文档”文件夹下的 \\Visual Studio version\\Projects\\SolutionName\\ProjectName\\Configuration\\ProjectName.tlog\\CL.command.1.tlog 或“用户”文件夹下的 \\Source\\Repos\\SolutionName\\ProjectName\\Configuration\\ProjectName.tlog\\CL.command.1.tlog 中。 如果使用其他生成系统，或更改了项目的默认位置，则该文件可能位于其他位置。

   可在此文件中找到源代码文件的名称，其后是用于编译它们的命令行参数（每个分占一行）。

1. 找到包含源代码文件名称的行（问题发生之处）；其下方的行包含相应的 cl.exe 命令参数。

将整个命令行复制并粘贴到报告。

### <a name="a-description-of-the-problem"></a>问题说明

我们需要一份有关你所遇到问题的详细说明，以验证是否可以在我们的计算机上观察到相同的效果；有时，它还有助于使我们了解你所尝试完成的内容，以及你希望看到的结果。

请提供工具集给出的确切错误消息，或者看到的确切运行时行为。 我们需要此信息来验证是否已正确重现问题。 请提供所有编译器输出，而不仅仅是最后一个错误消息。 我们需要查看与所报告问题相关的所有信息。 如果可以使用命令行编译器来复制问题，则首选编译器输出；IDE 和其他生成系统可能会筛选你看到的错误消息，或者仅捕获错误消息的第一行。

如果问题是编译器接受无效的代码并且未生成诊断，请在报告中注明。

要报告运行时行为问题，请提供该程序输出内容的原样副本，和你想要看到的内容。 理想情况下，它嵌入在输出语句本身中，例如，`printf("This should be 5: %d\n", actual_result);`。 如果程序崩溃或挂起，也请提到这一点。

添加任何其他可能有助于我们诊断你遇到的问题的详细信息，例如，你可能已发现的任何变通方法。 避免在报表的其他部分出现重复信息。

### <a name="the-repro"></a>重现

重现是完整的自包含源代码示例，可重复演示你遇到的问题（这就是重现这个名字的由来）。 我们需要重现来在自己的计算机上重现错误。 代码本身应该足以创建可编译和运行的简单可执行文件，或者在没有出现发现的问题时可以编译和运行的简单可执行文件。 重现不是代码片段；它应具有完整的函数和类，并包含所有必要 #include 指令，即使对于标准标头也是如此。

#### <a name="what-makes-a-good-repro"></a>高质量重现的标准

高质量重现的标准为：

- **最小的。** 重现应尽可能最小，但仍能准确演示所遇到的问题。 重现无需复杂或真实；它们只需要显示符合标准或记录的编译器实现的代码，或者在缺少诊断的情况下显示不合规的代码。 重现应简明扼要，最好只包含刚好足够演示问题的代码。 如果删除或简化某些代码也能保持符合性，并且不改变问题，请进行删除或简化。 不需要提供有效代码的反例。

- **自包含。** 重现应避免不需要的依赖项。 如果无需第三方库就可重现，请直接重现。 如果无需任何库代码，只需简单的输出语句（例如，`puts("this shouldn't compile");`、`std::cout << value;` 和 `printf("%d\n", value);`）即可重现此问题，请使用简单的输出语句。 最理想的情况是，示例可以压缩为单个源代码文件，而不引用任何用户标头。 尽可能减少我们需要考虑的有利于解决问题的代码量，这对我们而言极为有用。

- **针对最新版本的编译器。** 重现应尽可能使用最新版本的工具集的最新更新，或者下一次更新或下一个主版本的最新预发布版本。 在旧版本工具集中可能会遇到的问题很可能已在新版本中得到修复。 只有在特殊情况下，才会将修复向后移植到旧版本。

- **针对其他编译器进行检查**（如果相关）。 在可能的情况下，涉及可移植 C++ 代码的重现，应在其他编译器中验证行为。 程序的正确性最终由标准来决定，没有完美的编译器，但如果 Clang 和 GCC 接受了代码并且没有诊断，而 MSVC 拒绝，那么我们的编译器可能存在 Bug。 （其他可能性包括 Unix 和 Windows 行为的差异，或者 C++ 标准实现的级别不同等。）另一方面，如果所有编译器都拒绝代码，则可能是代码不正确。 查看不同的错误消息可能有助于自行诊断问题。

   你可以在 ISO C++ 网站上的[在线C++编译器](https://isocpp.org/blog/2013/01/online-c-compilers)中找到在线编译器列表，或查看 GitHub 上的[在线C ++ 编译器列表](https://arnemertz.github.io/online-compilers/)，针对这些编译器来测试代码。 一些具体示例包括 [Wandbox](https://wandbox.org/)、[Compiler Explorer](https://godbolt.org/) 和 [Coliru](http://coliru.stacked-crooked.com/)。

   > [!NOTE]
   > 在线编译器网站不隶属于 Microsoft。 许多在线编译器网站都是作为个人项目运行的，在读到本文时，其中某些网站可能已失效，但通过搜索应该能找到其他可用网站。

编译器、链接器和库中的问题往往以特定的方式显示。 所遇问题的类型决定了应在报告中添加的重现类型。 如果无法正确重新，我们将无法进行调查。 以下是你可能会看到的一些类型的问题，以及生成用于报告各类问题的重现的说明。

#### <a name="frontend-parser-crash"></a>前端（分析程序）故障

前端故障发生在编译器的分析阶段。 通常情况下，编译器会发出[错误 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，并引用错误发生处的源代码文件和行号；它还会常常提及文件 msc1.cpp，你可忽略此详细信息。

对于这种类型的故障，请提供[预处理过的重现](#preprocessed-repros)。

下面是此种故障类型的示例编译器输出：

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>后端（代码生成）故障

后端故障发生在编译器的代码生成阶段。 通常情况下，编译器会发出[错误 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，并且可能不会引用与问题相关的源代码文件和行号；它通常会提及文件 compiler\\utc\\src\\p2\\main.c，你可以忽略此详细信息。

对于这种类型的故障，如果使用通过 cl.exe 的 /GL 命令行参数启用的链接时间代码生成 (LTCG)，请提供[链接重现](#link-repros)。 如果未使用，请提供[预处理过的重现](#preprocessed-repros)。

下面是后端故障的示例编译器输出，其中未使用 LTCG。 如果编译器输出与此类似，请提供[预处理过的重现](#preprocessed-repros)。

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

如果以**内部编译器错误**开头的行提及 link.exe，而不是 cl.exe 并且已启用 LTCG，请提供[链接重现](#link-repros)。 如果不清楚是否因编译器错误消息而启用了 LTCG，可能需要检查你在 /GL 命令行参数的上一步中，从生成日志复制的命令行参数。

#### <a name="linker-crash"></a>链接器故障

链接器故障发生在链接阶段，在编译器已运行之后。 通常情况下，链接器将发出[链接器工具错误 LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md)。

> [!NOTE]
> 如果输出提及 C1001 或涉及链接时间代码生成，请参阅[后端（代码生成）故障](#backend-code-generation-crash)，了解更多信息。

对于这种类型的故障，请提供[链接重现](#link-repros)。

下面是此种故障类型的示例编译器输出。

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

如果启用了增量链接，且仅在进行成功地初始链接之后才发生故障（也就是说，仅在第一个完整链接之后才发生，随后的增量链接都基于该完整链接），请提供对象 (.obj) 和库 (.lib) 文件的副本，它们对应于初始链接完成后经过修改的源文件。

#### <a name="bad-code-generation"></a>错误代码生成

错误代码生成很少发生，但当编译器错误地生成不正确的代码时，它将发生，并造成应用程序在运行时（而非在编译时检测此问题时）出现故障。 如果你认为所遇到的问题会导致错误代码生成，请将报告同样视为[后端（代码生成）故障](#backend-code-generation-crash)。

对于这种类型的故障，如果使用通过 cl.exe 的 /GL 命令行参数启用的链接时间代码生成 (LTCG)，请提供[链接重现](#link-repros)。 如果未使用，请提供[预处理过的重现](#preprocessed-repros)。

## <a name="how-to-generate-a-repro"></a>如何生成重现

[高质量重现](#what-makes-a-good-repro)对于帮助我们跟踪问题的根源至关重要。 在针对特定类型的重现执行以下任何步骤之前，请尝试尽可能减少用于说明问题的代码。 尝试删除或最大程度减少依赖项、所需的标头和库，并尽可能限制使用的编译器选项和预处理器定义。

以下是生成用于报告不同类型问题的各种重现的说明。

### <a name="preprocessed-repros"></a>预处理过的重现

预处理过的重现是用于说明问题的单个源文件，通过在原始重现源文件中使用 /P 编译器选项，基于 C 预处理器的输出生成。 此内联包含标头，以删除其他源和头文件中的依赖项、宏、#ifdefs 以及其他可能依赖本地化环境的预处理器命令。

> [!NOTE]
> 对于在标准库实现中可能导致 Bug 的问题，预处理过的重现可能不是很有用，因为我们经常会替换正在进行的最新实现，以确定我们是否已修复问题。 在这种情况下，请勿预处理重现，此外，如果无法将问题减少为单个源文件，请将代码打包为 .zip 文件或类似文件，或考虑使用 IDE 项目重现。 有关详细信息，请参阅[其他重现](#other-repros)。

#### <a name="to-preprocess-a-source-code-file"></a>预处理源代码文件

1. 捕获用于生成重现的命令行参数，如[报告命令行的内容](#to-report-the-contents-of-the-command-line)中所述。

1. 打开与用于生成项目的 Visual Studio 版本和配置体系结构匹配的“开发人员命令提示”。

1. 转到包含重现项目的目录。

1. 在开发人员命令提示控制台窗口中，输入命令 cl /P arguments filename.cpp，其中 arguments 是前面捕获的参数列表，filename.cpp 是重现源文件的名称。 此命令复制用于重现的命令行，但在预处理器传递后停止编译，并将预处理过的源代码输出到 filename.i。

如果已生成了预处理过的文件，最好确保仍可使用该预处理过的文件来重现问题。

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>确认仍可以通过预处理过的文件来重现错误

1. 在开发人员命令提示控制台窗口中，输入命令 cl arguments /TP filename***.i*，告知 cl.exe 将预处理过的文件编译为 C++ 源文件，其中 arguments 是前面捕获的参数列表，但删除了 /D 和 /I 参数（因为它们已包含在预处理过的文件中）；filename***.i* 是预处理过的文件的名称。

1. 确认该问题可被重现。

最后，将预处理过的重现 filename.i 附加到报告中。

### <a name="link-repros"></a>链接重现

*链接重现*是链接器生成的内容，该内容是 link\_repro 环境变量指定的目录的内容。 它包含一些生成项目，这些项目共同说明链接时出现的问题，例如涉及链接时间代码生成 (LTCG) 的后端故障或链接器故障。 需要将这些生成项目用作链接器输入，以便重现问题。 通过使用此环境变量实现链接器的内置重现生成功能，可以轻松创建链接重现。

#### <a name="to-generate-a-link-repro"></a>生成链接重现

1. 捕获用于生成重现的命令行参数，如[报告命令行的内容](#to-report-the-contents-of-the-command-line)中所述。

1. 打开与用于生成项目的 Visual Studio 版本和配置体系结构匹配的“开发人员命令提示”。

1. 在开发人员命令提示控制台窗口中，转到包含重现项目的目录。

1. 输入 mkdir linkrepro，创建链接重现的目录。

1. 输入命令 set link\_repro=linkrepro，将 link\_repro 环境变量设置为刚刚创建的目录。

1. 要在 Visual Studio 中生成重现项目，请在开发人员命令提示控制台窗口中输入命令 devenv。 这可确保 link\_repro 环境变量的值对 Visual Studio 可见。 要在命令行生成项目，请使用前面捕获的命令行参数来复制重现生成。

1. 生成重现项目，并确认预期问题已发生。

1. 如果使用了 Visual Studio 执行生成，请将其关闭。

1. 在开发人员命令提示控制台窗口中，输入命令 set link\_repro=，清除 link\_repro 环境变量。

最后，通过将整个 linkrepro 目录压缩为 .zip 文件或类似的文件来打包重现，并将其附加到报告中。

### <a name="other-repros"></a>其他重现

如果无法将问题减少为单个源文件或预处理过的重现，且此问题无需链接重现，我们可以调查 IDE 项目。 所有关于如何创建高质量重现的说明仍然适用；代码应最精简且自包含，问题应发生在我们最新的工具中，并且如果相关，该问题不应该在其他编译器中出现。

将重现创建为一个最小的 IDE 项目，再将整个目录结构压缩成 .zip 文件或其他相似文件，并将其附加到报告。

## <a name="ways-to-send-your-report"></a>发送报告的方式

向我们提交报告的方式有多种。 可使用 Visual Studio 的内置[“报告问题”工具](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)或 [Visual Studio 开发者社区](https://developercommunity.visualstudio.com/)页面。 还可随附电子邮件发送报告，但首选前两种方法。 所选方法取决于你希望与调查报告的工程师互动的方式，以及是要跟踪其进度还是与社区共享报告。

> [!NOTE]
> 无论以何种方式提交报告，Microsoft 都尊重你的隐私。 有关我们如何处理你发送给我们的数据的信息，请参阅 [Microsoft Visual Studio 产品系列隐私声明](https://www.visualstudio.com/dn948229)。

### <a name="use-the-report-a-problem-tool"></a>使用“报告问题”工具

Visual Studio 用户可使用 Visual Studio 中的“报告问题”工具报告各种问题，单击几下即可完成。 该工具提供了一个简单的表单，你可以使用它来指定所遇问题的详细信息，然后在不离开 IED 的情况下提交报告。

可在 IDE 中使用“报告问题”工具快速而轻松地报告问题。 可选择“快速启动”搜索框旁边的“发送反馈”图标，从标题栏中进行访问，也可通过“帮助” > “发送反馈” > “报告问题”在菜单栏上找到它。

选择报告问题时，请首先在开发者社区中搜索是否有类似的问题。 如果有人之前已报告过你的问题，可投票赞成该主题并添加其他细节评论。 如果找不到类似问题，请在“Visual Studio 反馈”对话框底部选择“报告新问题”按钮，再按照步骤报告你的问题。

### <a name="use-the-visual-studio-developer-community-pages"></a>使用“Visual Studio 开发者社区”页面

还可使用“Visual Studio 开发者社区”页面轻松报告问题并查找有关 Visual Studio 以及 C++ 编译器、工具和库的解决方案。 可使用 [Visual Studio 问题](https://developercommunity.visualstudio.com/spaces/8/index.html)页面报告有关 IDE 或安装的问题。 有关 C++ 编译器、链接器及其他工具和库的相关问题，请使用 [C++ 问题](https://developercommunity.visualstudio.com/spaces/62/index.html)页面。

在每页顶部附近的“开发者社区”横幅中有一个搜索框，可用于查找报告了与你问题相似的问题的帖子或主题。 你可能发现现有主题中已存在解决方案或与你问题相关的其他有用信息。 如果有人之前已报告过相同问题，请投票赞成该主题并进行评论，而不是创建新的问题报告。

如果之前无人报告你的问题，请选择“开发者社区”页面上搜索框附近的“报告问题”按钮。 系统可能要求你登录 Visual Studio 帐户并同意开发者社区应用访问你的个人资料。 登录后，将直接转到可报告问题的页面。 可附上重现代码和命令行、屏幕截图、相关讨论的链接，以及你认为相关和有用的任何其他信息。

### <a name="send-an-email"></a>发送电子邮件

还可使用电子邮件将报告直接发送给 Visual C++ 团队。 可通过 [compilercrash@microsoft.com](mailto:compilercrash@microsoft.com) 联系我们。仅在其他两种方法均不可用时才使用此方法，因为相对于使用“报告问题”工具或网页向开发者社区报告问题，并未如此紧密地跟踪电子邮件，且评论和解决方案对其他 Visual Studio 用户不可见。

如果选择通过电子邮件发送报告，可采用以下模板作为电子邮件的正文。 如果电子邮件正文中未包括源代码或其他文件，请不要忘记将其附加在电子邮件中。

```Example
To: compilercrash@microsoft.com
Subject: Visual C++ Error Report
-----

Compiler version:

CL.EXE command line:

Problem description:

Source code and repro steps:

```

> [!TIP]
> 对于可能在 Visual Studio 中遇到的、与工具集无关的问题（例如 UI 问题、损坏的 IDE 功能或常规故障），“报告问题”工具可能是最佳之选，因为它具有屏幕截图功能，可以记录导致问题的 UI 操作。 请勿以发送电子邮件至 compilercrash@microsoft.com 的方式报告其他类型的错误。
