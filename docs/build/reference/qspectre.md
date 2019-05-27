---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e44416a44a9f772c17bc734d26c62ff87be775c8
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837422"
---
# <a name="qspectre"></a>/Qspectre

指定编译器生成指令以缓解某些 Spectre 变体 1 安全漏洞。

## <a name="syntax"></a>语法

> **/Qspectre**

## <a name="remarks"></a>备注

Visual Studio 2017 版本 15.5.5 及更高版本和 Visual Studio 2015 Update 3 中已提供“/Qspectre”选项，请参阅 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre)。 它可使编译器插入说明以缓解某些 [Spectre 安全漏洞](https://spectreattack.com/spectre.pdf)。 这些漏洞称为“推理性执行旁道攻击”，会影响许多操作系统和现代处理器，包括 Intel、AMD 和 ARM 处理器。

默认情况下，/Qspectre 选项处于禁用状态。

在其初始版本中，/Qspectre 选项仅处理优化的代码。 在 Visual Studio 2017 版本 15.7 及更高版本中，所有优化级别均支持 /Qspectre 选项。

Microsoft Visual C++ 库也可在具有 Spectre 缓解功能的版本中使用。 可以在 Visual Studio 安装程序中下载适用于 Visual Studio 2017 及更高版本的 Spectre 缓解库。 可在“单个组件”选项卡下的“编译器、生成工具和运行时”中找到它们，并且它们的名称中含“面向 Spectre 的库”。 启用了缓解功能的 DLL 和静态运行时库都适用于 Visual C++ 运行时的子集：VC + + 启动代码、vcruntime140、msvcp140、concrt140 和 vcamp140。 仅本地部署的应用程序支持 DLL；尚未修改 Visual C++ 2017 和更高版本的 Runtime Libraries Redistributable 的内容。 还可在“单个组件”下的“SDK、库和框架”中找到适用于 MFC 和 ATL 的 Spectre 缓解库，并进行安装。

### <a name="applicability"></a>适用性

如果代码对跨信任边界的数据进行操作，建议使用 /Qspectre 选项来重新生成和重新部署代码，以尽快解决此问题。 对跨信任边界的数据进行操作的代码示例包括加载可能影响执行的不受信任输入的代码，例如，进行远程过程调用、解析不受信任的输入或文件，或使用其他本地内部进程通信 (IPC) 接口的代码。 标准沙盒技术可能还不足以彻底解决问题。 在确定你的代码不跨信任边界之前，应仔细调查沙盒。

### <a name="availability"></a>可用性

/Qspectre 选项在 Visual Studio 2017 版本 15.5.5 以及在 2018 年 1 月 23 日及之后对 Microsoft MSVC 编译器 (MSVC) 做出的所有更新中均可用。 使用 Visual Studio 安装程序更新编译器并安装 Spectre 缓解库作为单独组件。 /Qspectre 选项也可通过修补程序在 Visual Studio 2015 Update 3 中使用。 有关详细信息，请参阅 [KB 4338871](https://support.microsoft.com/help/4338871)。

所有版本的 Visual Studio 2017 版本 15.5 和所有预览版的 Visual Studio 2017 版本 15.6 都包括一个未记录的选项 /d2guardspecload，该选项等效于 /Qspectre 的初始行为。 可以使用 /d2guardspecload 将相同的缓解功能应用于这些版本的编译器中的代码。 请更新版本，以在支持该选项的编译器中使用 /Qspectre；/Qspectre 选项可能也支持较新版本的编译器中的新缓解功能。

### <a name="effect"></a>效果

/Qspectre 选项输出代码以缓解 Specter 变体 1、绕过边界检查 [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)。 它通过插入充当推理性代码执行屏障的指令进行运作。 用于减轻处理器推理的特定指令取决于处理器及其微体系结构，并且可能在编译器的未来版本中发生变化。

启用 /Qspectre 选项时，编译器会尝试标识其中推理性执行可能绕过边界检查并插入屏障指令的实例。 请务必注意，编译器为标识变体 1 的实例而可执行的分析是有限制的。 在这种情况下，不能保证检测到 /Qspectre 下变体 1 的所有可能的实例。

### <a name="performance-impact"></a>性能影响

在少数非常大型的基本代码中，已忽略 /Qspectre 的性能影响，但是无法保证 /Qspectre 下的代码性能不受影响。 应对代码进行基准测试，以确定该选项对性能的影响。 如果你知道性能关键型块或循环中不需要缓解功能，则可以使用 [__declspec(spectre(nomitigation))](../../cpp/spectre.md) 指令选择性禁用缓解功能。 该指令不适用于仅支持 /d2guardspecload 选项的编译器。

### <a name="required-libraries"></a>必需库

/Qspectre 编译器选项生成代码，此代码隐式链接已构建为提供 Spectre 缓解功能的运行时库版本。 以下库是可选组件，必须使用 Visual Studio 安装程序进行安装：

- 面向 Spectre \[(x86 和 x64) | (ARM) | (ARM64)] 的 MSVC 版本 version_numbers 库
- 带有 Spectre 缓解功能的 Visual C++ ATL for \[(x86/x64) | ARM | ARM64]
- 带有 Spectre 缓解功能的 Visual C++ MFC for \[x86/x64 | ARM | ARM64]

如果使用 /Qspectre 生成代码，并且未安装这些库，生成系统会报告**警告 MSB8038：已启用 Spectre 缓解功能，但未找到 Spectre 缓解库**。 如果 MFC 或 ATL 代码生成失败，并且链接器报告错误（例如，错误 LNK1104：无法打开文件“oldnames.lib”），原因可能是缺少这些库。

### <a name="additional-information"></a>其他信息

有关详细信息，请参阅官方的 [Microsoft Security Advisory ADV180002，用于缓解推理执行边信道漏洞的指南](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 也可从 Intel [推理性执行旁道缓解措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 和 ARM [缓存推理旁道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)获取指南。 有关 Spectre 和 Meltdown 缓解功能的特定于 Windows 概述，请参阅 Microsoft 安全博客上的[了解 Windows 系统上的 Spectre 和 Meltdown 缓解功能的性能影响](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)。 有关 MSVC 缓解功能解决的 Spectre 漏洞的概述，请参阅 Visual C++ 团队博客上的 [MSVC 中的 Spectre 缓解功能](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 在“其他选项”框中输入“/Qspectre”编译器选项。 选择“确定”应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
