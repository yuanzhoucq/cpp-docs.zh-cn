---
title: /Qspectre |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bef66e8b3c326f205b6399538a811bcc83c9f9d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070395"
---
# <a name="qspectre"></a>/Qspectre

指定编译器生成的指令以缓解特定 Spectre 变体 1 安全漏洞。

## <a name="syntax"></a>语法

> **/Qspectre**

## <a name="remarks"></a>备注

**/Qspectre**选项是推出 Visual Studio 2017 15.5.5 版和更高版本，并通过 Visual Studio 2015 Update 3 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre)。 它会导致编译器插入以缓解特定的说明[Spectre 安全漏洞](https://spectreattack.com/spectre.pdf)。 调用这些漏洞*推理执行旁道攻击*、 会影响许多操作系统和现代处理器中，包括来自 Intel、 AMD 处理器和 ARM。

**/Qspectre**选项默认情况下处于关闭状态。

在其初始版本中， **/Qspectre**选项仅处理优化的代码。 在 Visual Studio 2017 版本 15.7 及更高版本， **/Qspectre**选项支持所有优化级别。

Microsoft Visual c + + 库中也会提供与 Spectre 缓解版本。 可以在 Visual Studio 安装程序下载用于 Visual Studio 2017 的 Spectre 缓解库。 在中找到**各个组件**选项卡上的**编译器、 生成工具和运行时**，并且在名称中具有"Libs 有关 Spectre"。 DLL 和静态运行时库与已启用的缓解是适用于 Visual c + + 运行时的子集： VC + + 启动代码、 vcruntime140、 msvcp140、 concrt140 和 vcamp140。 应用程序本地的部署; 仅支持 Dll尚未修改的 Visual c + + 2017年运行时库可再发行的内容。 也可为 MFC 和 ATL 中, 找到安装 Spectre 缓解库**各个组件**选项卡上的**Sdk、 库和框架**。

### <a name="applicability"></a>适用性

如果你的代码对跨信任边界的数据进行操作，则我们建议你使用 **/Qspectre**选项以重新生成并重新部署你的代码来尽可能快地缓解此问题。 对跨信任边界的数据进行操作的代码的示例包括用于加载不受信任的输入可能会影响执行的代码，例如，代码都会发出远程过程调用、 分析不受信任的输入或文件，或使用其他本地进程间通信 (IPC) 的接口。 标准的沙盒技术可能不足。 在确定您的代码不会跨越信任边界之前，应仔细调查您的沙盒。

### <a name="availability"></a>可用性

**/Qspectre**选项可在 Visual Studio 2017 版本 15.5.5 以及在或者 2018 年 1 月 23 日在 Microsoft Visual c + + 编译器 （msvc） 编写的所有更新。 使用 Visual Studio 安装程序来更新编译器，并作为单独的组件安装的 Spectre 缓解库。 **/Qspectre**选项也是可在 Visual Studio 2015 Update 3 中通过一个修补程序。 有关详细信息，请参阅[KB 4338871](https://support.microsoft.com/help/4338871)。

所有版本的 Visual Studio 2017 版本 15.5 和所有预览版的 Visual Studio 2017 版本 15.6 包含一个未记录的选项， **/d2guardspecload**，，等效于的初始行为 **/Qspectre**. 可以使用 **/d2guardspecload**将相同的缓解措施应用于这些版本的编译器中的代码。 请更新您的生成以使用 **/Qspectre**中的支持选项; 编译器 **/Qspectre**选项也可能在更高版本的编译器支持新的缓解措施。

### <a name="effect"></a>效果

**/Qspectre**选项将输出代码以缓解低变体 1，边界检查绕过[CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)。 它可通过插入充当推理代码执行屏障的说明。 用来缓解处理器推理的具体说明取决于处理器和其微型体系结构，并在将来版本的编译器可能会更改。

当 **/Qspectre**启用选项，编译器将尝试标识在其中推理执行可能会绕过边界检查和插入的屏障说明实例。 请务必注意是有限的编译器可以执行来标识实例的变体 1 的分析。 在这种情况下，则变体 1 的所有可能的实例检测下不能保证 **/Qspectre**。

### <a name="performance-impact"></a>对性能的影响

性能影响 **/Qspectre**达到过要在多个非常大代码库，可以忽略不计，但没有保证代码的性能的 **/Qspectre**不会受到影响。 应制定基准代码以确定对性能的选项的效果。 如果您知道缓解措施不需要在性能关键的块或循环中，缓解措施可以有选择地禁用通过使用[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指令。 此指令只支持的编译器中不可 **/d2guardspecload**选项。

### <a name="required-libraries"></a>所需的库

**/Qspectre**编译器选项生成的隐式链接的已生成提供 Spectre 缓解措施的运行时库版本的代码。 这些库都必须通过使用 Visual Studio 安装程序安装的可选组件：

- VC + + 2017年版本*version_numbers*面向 Spectre 的 Libs \[（x86 和 x64） |(ARM) |(ARM64)]
- Visual c + + ATL for \[(x86/x64) |ARM |ARM64] 带有 Spectre 缓解措施
- Visual c + + MFC for \[x86/x64 |ARM |ARM64] 带有 Spectre 缓解措施

如果使用生成你的代码 **/Qspectre**和这些库并不安装，生成系统报告**警告 MSB8038： 已启用 Spectre 缓解措施，但找不到 Spectre 缓解库**。 如果在 MFC 或 ATL 代码生成失败，并且链接器报表错误，例如**错误 LNK1104： 无法打开文件 oldnames.lib**，这些缺少的库可能就是原因。

### <a name="additional-information"></a>其他信息

有关更多详细信息，请参阅官方[Microsoft 安全公告 ADV180002，指南，以缓解推理执行旁道漏洞](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 指南也是可从 Intel[推理执行端通道缓解措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)，和 ARM，[缓存推理端通道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)。 有关 Spectre 和 Meltdown 缓解措施的特定于 Windows 的概述，请参阅[了解 Windows 系统上的 Spectre 和 Meltdown 缓解措施的性能影响](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)Microsoft 安全博客上。 MSVC 缓解措施针对 Spectre 漏洞的概述，请参阅[Spectre 缓解措施在 MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) Visual c + + 团队博客上。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入 **/Qspectre**中的编译器选项**其他选项**框。 选择**确定**以应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
