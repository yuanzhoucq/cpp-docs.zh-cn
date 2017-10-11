---
title: "如何使用 Visual C++ 工具集报告问题 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ec24a49c-411d-47ce-aa4b-8398b6d3e8f6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5c6fbfc8699d7d66c40b0458972d8b6ef0dcc705
ms.openlocfilehash: 2ea129ac94cb1ddc7486ba69280dc0390896e088
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>如何使用 Visual C++ 工具集报告问题
使用 Visual C++ 编译器、链接器或其他工具时如果遇到问题，请告知我们。  
  
 最好是向我们发送报告，在报告中说明你所遇到的问题、如何生成程序的详细信息，以及相关代码（以便我们在自己的计算机上重现该问题）。 通过这些信息，我们可以快速验证问题是否存在于本地环境，判断它是否会影响其他版本的编译器，并诊断其原因。  
  
 在本文档中，你将了解到  
  
-   [如何准备报告](#prepare)，以及一篇优秀报告应包含哪些内容。  
  
-   [发送报告的方式](#send)，以及如何让其与众不同。  
  
-   [如何生成重现](#generate)，以及不同类型的重现。  
  
 无论对我们，还是对和你一样的其他开发者而言，你的报告都十分重要。 谢谢你帮助我们改进 Visual C++！  
  
##  <a name="prepare"></a>如何准备报告  
 创建高质量报告至关重要，因为一旦缺少完整信息，我们将难以在计算机上重现你所遇到的问题。 报告的质量越高，我们重新创建和诊断问题的效率就越高。  
  
 报告中应至少包括  
  
-   正在使用的工具集的完整版本信息。  
  
-   用于生成代码的完整 cl.exe 命令行。  
  
-   对所遇到问题的详细描述。  
  
-   一份“重现” - 用于演示问题的源代码。  
  
 阅读以继续了解更多关于我们所需的特定信息，以及在何处可以找到它们的详细信息。  
  
### <a name="the-toolset-version"></a>工具集版本  
 需要你正在使用的工具集的完整版本信息，以便在我们的计算机上针对相同工具集测试你的重现。 如果我们可以重现此问题，我们还可以将此信息作为起点，调查哪些版本的工具集存在同样的问题。  
  
##### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>报告你正在使用的编译器的完整版本  
  
1.  在键盘上按 Windows 徽标键，然后开始键入 `Developer Command Prompt`。  
  
2.  在匹配列表中，选择“开发人员命令提示符”版本，该版本与你正使用的 Visual Studio 版本相匹配。  
  
3.  在“开发人员命令提示”控制台中，输入命令 `cl /Bv /CLR`。  
  
 该输出应与以下类似：  
  
```  
C:\Compiler>cl /Bv /CLR  
Microsoft (R) C/C++ Optimizing Compiler Version 18.00.40209  
for Microsoft (R) .NET Framework version 4.00.30319.34014  
Copyright (C) Microsoft Corporation.  All rights reserved.  
  
Compiler Passes:  
 C:\WinCComp\binaries.x86chk\bin\i386\cl.exe:        Version 18.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\c1.dll:        Version 18.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\c1xx.dll:      Version 18.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\c2.dll:        Version 18.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\link.exe:      Version 12.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\mspdb120.dll:  Version 12.00.40209.0  
 C:\WinCComp\binaries.x86chk\bin\i386\1033\clui.dll: Version 18.00.40209.0  
 Common Language Runtime:                            Version  4.00.30319.34014  
  
cl : Command line error D8003 : missing source filename   
```  
  
 将整个输出复制并粘贴到报告。  
  
### <a name="the-command-line"></a>命令行  
 需要用于生成代码的完整命令行（cl.exe 和其参数），以便我们以完全相同的方式在计算机上生成它。 这一点很重要，因为你所遇到的问题可能仅在使用某一特定参数或参数组合生成时才存在。  
  
 此信息位于遇到问题后立即出现的生成日志中，建议在该位置查找。 这可确保命令行包含完全相同的参数，从而有可能帮助解决问题。  
  
##### <a name="to-report-the-contents-of-the-command-line"></a>报告命令行的内容  
  
1.  找到并打开 **CL.command.1.tlog** 文件。 默认情况下，此文件位于 \\...\Visual Studio Version\Projects\SolutionName\ProjectName\Config\ProjectName.tlog\CL.command.1.tlog。  
  
     可在此文件中找到源代码文件的名称，其后是用于编译它们的命令行参数（每个分占一行）。  
  
2.  找到包含源代码文件名称的行（问题发生之处）；其下方的行包含相应的 cl.exe 命令及其参数。  
  
 将整个命令行复制并粘贴到报告。  
  
### <a name="a-description-of-the-problem"></a>问题说明  
 我们需要一份有关你所遇到问题的详细说明，以验证是否可以在我们的计算机上观察到相同的效果；有时，它还有助于使我们了解你所尝试完成的内容，以及你希望看到的结果。  
  
 请提供由工具集提供的精确错误消息，并简短说明你所尝试完成的内容，以帮助我们了解你的重现代码，并提供任何其他可能有助于诊断你所遇到的问题的详细信息（例如你可能已经发现的任何解决方法）。 避免在报表的其他部分出现重复信息。  
  
### <a name="the-repro"></a>重现  
 我们需要一份重现 - 一个演示你所遇到问题的自包含源代码示例 - 以便在我们的计算机上重现该错误。 所遇问题的类型决定了应在报告中添加的重现类型。 如果无法正确重新，我们将无法进行调查。  
  
 简短的自包含重现可以直接包含在报告文本中，但较大的源代码重现应附加到报告中。 对于无法缩小到单个源代码文件的重现，应将包含所有文件的目录以压缩为 .zip 文件或类似文件的方式打包，并附加到报告。 任何其他特定方案的详细信息也应包含在报告文本中，而非源代码中。  
  
 你所能提供的最佳重现是最小重现。 这是一种单独的自包含源代码文件（缺少对用户标头的引用），仅包含演示问题所需的代码。 如果你能提供这种形式的重现，请将源代码文件直接附加到报告；这就是我们所需要的。  
  
 如果无法在缺少依赖项的情况下将问题压缩为最小重现，请参阅下列部分，判断应在报告中添加何种类型的重现。  
  
#### <a name="frontend-parser-crash"></a>前端（分析程序）故障  
 前端故障发生在编译器的分析阶段。 通常情况下，编译器会发出[错误 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，并引用错误发生处的源代码文件和行号；它还会常常提及文件 msc1.cpp，你可忽略此详细信息。  
  
 对于这种类型的故障，请提供[预处理过的重现](#preprocessed_repro)。  
  
 下面是此种故障类型的示例编译器输出：  
  
```  
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
  
####  <a name="backend_crash"></a>后端（代码生成）故障  
 后端故障发生在编译器的代码生成阶段。 通常情况下，编译器会发出[错误 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)，并可能不会引用与问题相关的源代码文件和行号；它通常会提及文件 compiler\utc\src\p2\main.c，你可忽略此详细信息。  
  
 对于这种类型的故障，如果使用的是链接时间代码生成 (LTCG)，请提供[链接重现](#link_repro)，如果不是，请提供[预处理过的重现](#preprocessed_repro)。 LTCG 由 cl.exe 的 `/GL` 命令行参数启用。  
  
 下面是此种故障类型的示例编译器输出，其中**未**使用 LTCG。 如果编译器输出与此类似，请提供[预处理过的重现](#preprocessed_repro)。  
  
```  
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
  
 如果以**内部编译器错误**开头的行提及 link.exe，而不是 cl.exe 并且已启用 LTCG，请提供[链接重现](#link_repro)。 如果不清楚是否因编译器错误消息而启用了 LTCG，可能需要检查你在 `/GL` 命令行参数的上一步中，从生成日志复制的命令行参数。  
  
#### <a name="linker-crash"></a>链接器故障  
 链接器故障发生在链接阶段，在编译器已运行之后。 通常情况下，链接器将发出[链接器工具错误 LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md)。  
  
> [!NOTE]
>  如果输出提及 C1001 或涉及链接时间代码生成，请参阅[后端（代码生成）故障](#backend_crash)，了解更多信息。  
  
 对于这种类型的故障，请提供[链接重现](#link_repro)。  
  
 下面是此种故障类型的示例编译器输出。  
  
```  
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
  
 如果启用增量链接，且仅在进行初始链接之后才发生故障（也就是说，仅在第一个完整链接之后才发生，随后的增量链接都基于该完整链接），请提供对象 (.obj) 和库 (.lib) 文件的副本，它们对应于初始链接完成后被修改的源文件。  
  
#### <a name="bad-code-generation"></a>错误代码生成  
 错误代码生成很少发生，但当编译器错误地生成不正确的代码时，它将发生，并造成应用程序在运行时（而非在编译时检测此问题时）出现故障。 如果你认为所遇到的问题会导致错误代码生成，请将报告同样视为[后端（代码生成）故障](#backend_crash)。  
  
 对于这种类型的故障，如果使用的是链接时间代码生成 (LTCG)，请提供[链接重现](#link_repro)，如果不是，请提供[预处理过的重现](#preprocessed_repro)。 LTCG 由 cl.exe 的 `/GL` 命令行参数启用。  
  
##  <a name="send"></a>发送报告的方式  
 向我们提交报告的方式有多种。 你可以通过 Microsoft Connect 提交 Bug、向我们发送电子邮件，或使用 Visual Studio 的内置报告问题工具。 提交报告的最佳方式取决于你遇到的问题类型、希望与调查报告的工程师互动的方式、以及是要跟踪其进度还是与社区共享报告。  
  
> [!NOTE]
>  无论以何种方式提交报告，Microsoft 都尊重你的隐私。 有关我们如何处理你发送给我们的数据的信息，请参阅 [Microsoft Visual Studio 产品系列隐私声明](https://www.visualstudio.com/dn948229)。  
  
### <a name="file-a-bug-on-microsoft-connect"></a>通过 Microsoft Connect 提交 Bug  
 Microsoft Connect ([connect.microsoft.com](http://connect.microsoft.com)) 是我们的用户社区直接连接到生成 Microsoft 产品的团队的一种方式。 使用 Connect，你可以提交新 Bug、提出功能请求、查看社区所提出的其他 Bug 和请求，并可用语音指出哪一个对你最重要。  
  
 当你想与 Visual Studio 社区共享报告，并公开地跟踪其进度时，通过 Connect 报告问题是最佳之选；通过共享报告，有时可以借助其他人提供的解决方法或其他信息帮助我们诊断问题。 如果想要保证报告的私密性，也可以使用 Connect（例如无法在报告中共享代码时），只需在提交表单前，将报告可见性设置为“私密”即可。  
  
-   [Microsoft Connect：报告 Visual Studio 2015 Update 3 中的问题](https://connect.microsoft.com/VisualStudio/Feedback/LoadSubmitFeedbackForm?FormID=6493)  
  
-   [Microsoft Connect：报告 Visual Studio 2015 Update 2 中的问题](https://connect.microsoft.com/VisualStudio/Feedback/LoadSubmitFeedbackForm?FormID=6406)  
  
-   [Microsoft Connect：报告 Visual Studio 2015 Update 1 中的问题](https://connect.microsoft.com/VisualStudio/Feedback/LoadSubmitFeedbackForm?FormID=6326)  
  
-   [Microsoft Connect：报告 Visual Studio 2015 中的问题](https://connect.microsoft.com/VisualStudio/Feedback/LoadSubmitFeedbackForm?FormID=6240)  
  
 可以在[Visual Studio 与 .NET Framework 反馈](https://connect.microsoft.com/VisualStudio/feedback/LoadSubmitFeedbackForm)“连接”页面的下拉框中找到其他 Visual Studio 与 .NET Framework 产品，并报告它们的问题。  
  
### <a name="send-an-email"></a>发送电子邮件  
 发送电子邮件是将报告直接发送到 Visual C++ 团队的另一种方式；可以通过 [compilercrash@microsoft.com](mailto:compilercrash@microsoft.com) 与我们联系。  
  
 通过电子邮件报告问题缺少丰富的 Microsoft Connect 社区，但有时，它却更适合大型重现。 如果工作环境未连接到 Internet，或无法使用 Microsoft Connect，使用电子邮件就成为了你的最佳或唯一选择。  
  
 如果选择通过电子邮件发送报告，可采用以下模板作为电子邮件的正文。 如果电子邮件正文中未包括源代码或其他文件，请不要忘记将其附加在电子邮件中。  
  
```  
To: compilercrash@microsoft.com  
Subject: Visual C++ Error Report  
-----  
  
Compiler version:  
  
CL.EXE command line:  
  
Problem description:  
  
Source code and repro steps:  
  
```  
  
### <a name="use-the-report-a-problem-tool"></a>使用“报告问题”工具  
 Visual Studio 用户可以使用 Visual Studio 中的“报告问题”工具报告各种问题，操作简单，只需几次单击即可完成。 该工具提供了一个简单的表单，你可以使用它来指定所遇问题的详细信息，然后在不离开 IED 的情况下提交报告。  
  
 对于本文中所讨论的工具集问题而言，通过“报告问题”工具提交报告并不常见，然而，如果它适合你，那么也不失为一个选择。  
  
> [!TIP]
>  对于可能在 Visual Studio 中遇到的、与工具集无关的问题（例如 UI 问题、损坏的 IDE 功能或常规故障），“报告问题”工具可能是最佳之选，因为它具有屏幕截图功能，可以记录导致问题的 UI 操作。 对于报告其他类型的错误而言，Microsoft Connect 也是一个不错的选择，但它缺少“报告问题”工具的其他功能。 请勿以发送电子邮件至 compilercrash@microsoft.com 的方式报告其他类型的错误。  
  
##  <a name="generate"></a>生成重现  
 重现是一个完整的自包含代码示例，用于演示所报告的问题。 重现**并非**一个代码片段 - 它必须是生成和运行的完整示例（你所报告的问题产生的错误除外）。 它应包含全部必需的 #include 指令，即使对标准标头亦是如此。  
  
 此外，好的重新应是  
  
-   **最小的。** 重现应尽可能最小，但仍能准确演示所遇到的问题。 重现无需复杂或真实 - 以简单扼要的重现为佳。 它们无需包含可运行的计数器示例代码，但在用于说明时亦可包含；只有导致问题的示例代码才是必需的。  
  
-   **自包含。** 重现应避免不需要的依赖项。 如果无需第三方库就可重现，请直接重现。 如果无需任何库代码就可重现（可使用 `std::out` 和`printf()`），请直接重现。 尽可能减少我们需要考虑的有利于解决问题的代码量，这对我们而言极为有用。  
  
-   **针对最新版本的编译器。** 重现应尽可能使用最新版本的工具集。 在旧版本的工具集中可能仍会遇到的问题，很有可能已在新版本中得到修复。  
  
-   如果相关，请**在其他编译器中进行检查**。 在可能的情况下，涉及可移植 C++ 代码的重现，应在其他编译器中验证行为。  
  
     此步骤有助于判断代码是正确的（MSVC 否定 Clang 和 GCC 时）还是错误的（MSVC、Clang 和 GCC 一致认为代码产生了错误时）。  
  
 以下是生成用于报告不同类型问题的各种重现的说明。  
  
###  <a name="preprocessed_repro"></a>预处理过的重现  
 预处理过的重现是用于说明问题的单个源文件，它从 C 预处理器的输出中通过处理原始源文件而生成。 此进程内联包含标头，以删除其他源和头文件中的依赖项、宏、#ifdefs 以及其他可能依赖本地化环境的预处理器命令。  
  
> [!NOTE]
>  请注意，对于在标准库实现中可能导致 Bug 的问题而言，预处理过的重现可能是最不方便的，因为我们会经常替换最新、正在进行中的实现，以确定我们是否已修复问题。 在这种情况下请勿预处理重现，此外，如果无法将问题减少到单个源文件，请将代码打包为 .zip 文件或其他类似文件，或考虑使用 IDE 项目重现（请参阅下方的[其他重现](#other_repros)）。  
  
##### <a name="to-preprocess-a-source-code-file"></a>预处理源代码文件  
  
1.  在键盘上按 Windows 徽标键，然后开始键入 `Developer Command Prompt`。  
  
2.  在匹配列表中，选择“开发人员命令提示符”版本，该版本与你正使用的 Visual Studio 版本相匹配。  
  
3.  在“开发人员命令提示”控制台窗口中，输入命令 `cl /P argumentsfilename.cpp`。  
  
 如果已有预处理过的文件（这里是指 filename.i），使用预处理过的文件来确保问题仍然可被重现，是一个很不错的办法。 可使用 `/TP` 命令行参数告知 cl.exe 跳过预处理器步骤，并尝试像往常一样编译。  
  
##### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>确认仍可以通过预处理过的文件来重现错误  
  
1.  在键盘上按 Windows 徽标键，然后开始键入 `Developer Command Prompt`。  
  
2.  在匹配列表中，选择“开发人员命令提示符”版本，该版本与你正使用的 Visual Studio 版本相匹配。  
  
3.  在“开发人员命令提示”控制台窗口中，输入命令 `cl arguments /TP filename.i`。  
  
4.  确认该问题可被重现。  
  
 最后，将此重现附加到报告。  
  
###  <a name="link_repro"></a>链接重现  
 链接重现是一个包含生成项目（它们共同说明发生在链接时间的问题）的单独目录，例如涉及链接时间代码生成 (LTCG) 的后端故障，或链接器故障；所包含的生成项目是链接器输入所需的生成项目，因此可以重现问题。 使用链接器提供的设备可以轻松创建链接重现。  
  
##### <a name="to-generate-a-link-repro"></a>生成链接重现：  
  
1.  打开命令提示符，然后输入命令 `mkdir directory`，创建链接重现的目录。  
  
2.  将 link_repro 环境变量设置为刚刚创建的目录；输入命令 `set link_repro=directory`。  
  
3.  如果要从 Visual Studio 内部执行生成，请通过输入命令 `devenv` 从命令提示符处启动它。 这可确保 link_repro 环境变量的值对 Visual Studio 可见。  
  
4.  生成应用程序，并确认预期问题已发生。  
  
5.  如果已在步骤 3 中启动 Visual Studio，现在请将其关闭。  
  
6.  清除 link_repro 环境变量；输入命令 `set link_repro=`  
  
 最后，通过将整个目录压缩为 .zip 文件或相似文件来打包重现，并将其附加到报告中。  
  
###  <a name="other_repros"></a>其他重现  
 如果无法将问题减少到单个源文件或预处理过的重现，且此问题无需链接重现，我们可以调查 IDE 项目。 项目内的代码应仍保持最小，本文档中的所有指导仍然适用。  
  
 将重现创建为一个最小的 IDE 项目，再将整个目录结构压缩成 .zip 文件或其他相似文件，并将其附加到报告。
