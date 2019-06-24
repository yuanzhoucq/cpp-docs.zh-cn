---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e0d3af50015b77af297cbee22f439cd17d803de9
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344150"
---
# <a name="qspectre"></a>/Qspectre

指定编译器生成指令以缓解某些 Spectre 变体 1 安全漏洞。

## <a name="syntax"></a>语法

> **/Qspectre**

## <a name="remarks"></a>备注

Visual Studio 2017 版本 15.5.5 及更高版本和 Visual Studio 2015 Update 3 中已提供“/Qspectre”选项，请参阅 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre)  。 它可使编译器插入说明以缓解某些 [Spectre 安全漏洞](https://spectreattack.com/spectre.pdf)。 调用这些漏洞*推理执行旁道攻击*。 它们会影响许多操作系统和现代处理器中，包括来自 Intel、 AMD 和 ARM 处理器。

默认情况下，/Qspectre 选项处于禁用状态  。

在其初始版本中，/Qspectre 选项仅处理优化的代码  。 在 Visual Studio 2017 版本 15.7 及更高版本中，所有优化级别均支持 /Qspectre 选项  。

Microsoft Visual C++ 库也可在具有 Spectre 缓解功能的版本中使用。 可以在 Visual Studio 安装程序中下载适用于 Visual Studio 2017 及更高版本的 Spectre 缓解库。 在中发现**各个组件**选项卡上的**编译器、 生成工具和运行时**，并且在名称中具有"Libs 有关 Spectre"。 启用了缓解功能的 DLL 和静态运行时库都适用于 Visual C++ 运行时的子集：VC + + 启动代码、vcruntime140、msvcp140、concrt140 和 vcamp140。 应用程序本地部署仅支持 Dll。 视觉对象的内容C++2017年及更高版本运行时库可再发行组件尚未被修改。

您还可以通过以下方式安装 Spectre 缓解库用于 MFC 和 atl。 在中发现**各个组件**选项卡上的**Sdk、 库和框架**。

### <a name="applicability"></a>适用性

如果你的代码对数据跨信任边界，则我们建议你使用 **/Qspectre**选项以重新生成并重新部署你的代码来尽可能快地缓解此问题。 此类代码的一个示例是将不受信任的输入可能会影响执行加载的代码。 例如，进行远程过程的代码调用，解析不受信任的输入或文件，或使用其他本地进程间通信 (IPC) 接口。 标准沙盒技术可能还不足以彻底解决问题。 在确定您的代码不会跨信任边界之前仔细调查您的沙盒。

### <a name="availability"></a>可用性

**/Qspectre**选项可在 Visual Studio 2017 版本 15.5.5，以及在 Microsoft 的所有更新C++编译器 (MSVC) 或者在 2018 年 1 月 23 日。 使用 Visual Studio 安装程序更新编译器并安装 Spectre 缓解库作为单独组件。 /Qspectre 选项也可通过修补程序在 Visual Studio 2015 Update 3 中使用  。 有关详细信息，请参阅 [KB 4338871](https://support.microsoft.com/help/4338871)。

所有版本的 Visual Studio 2017 版本 15.5 中和所有预览版的 Visual Studio 2017 版本 15.6 中。 包含一个未记录的选项， **/d2guardspecload**。 它相当于的初始行为 **/Qspectre**。 可以使用 /d2guardspecload 将相同的缓解功能应用于这些版本的编译器中的代码  。 我们建议您更新您的生成以使用 **/Qspectre**在编译器中支持的选项。 **/Qspectre**选项也可能在更高版本的编译器支持新的缓解措施。

### <a name="effect"></a>效果

/Qspectre 选项输出代码以缓解 Specter 变体 1、绕过边界检查 [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)  。 它通过插入充当推理性代码执行屏障的指令进行运作。 用于减轻处理器推理的特定指令取决于处理器及其微体系结构，并且可能在编译器的未来版本中发生变化。

如果你启用 **/Qspectre**选项，编译器将尝试标识其中推理执行可能会绕过边界检查的实例。 这就是它可以将插入的屏障说明进行操作。 务必要注意的限制与编译器可以执行操作来标识实例变体 1 的分析。 在这种情况下，则变体 1 的所有可能的实例检测下不能保证 **/Qspectre**。

### <a name="performance-impact"></a>性能影响

性能影响 **/Qspectre**看上去会在几个基本可调整大小的代码中可以忽略不计。 但是，没有保证代码的性能 **/Qspectre**不会受到影响。 应对代码进行基准测试，以确定该选项对性能的影响。 如果您知道缓解措施不需要在性能关键的块或循环中，可以通过使用有选择性地禁用缓解[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指令。 此指令只支持的编译器中没有 **/d2guardspecload**选项。

### <a name="required-libraries"></a>必需库

**/Qspectre**编译器选项生成的隐式链接版本构建，以便提供 Spectre 缓解措施的运行时库的代码。 以下库是可选组件，必须使用 Visual Studio 安装程序进行安装：

- 面向 Spectre \[(x86 和 x64) | (ARM) | (ARM64)] 的 MSVC 版本 version_numbers 库 
- 带有 Spectre 缓解功能的 Visual C++ ATL for \[(x86/x64) | ARM | ARM64]
- 带有 Spectre 缓解功能的 Visual C++ MFC for \[x86/x64 | ARM | ARM64]

如果使用生成你的代码 **/Qspectre**并且这些库不安装，生成系统报告**警告 MSB8038:已启用 Spectre 缓解功能，但未找到 Spectre 缓解库**。 如果在 MFC 或 ATL 代码未能生成，并且链接器报表错误，例如**错误 LNK1104： 无法打开文件 oldnames.lib**，这些缺少的库可能就是原因。

### <a name="additional-information"></a>其他信息

有关详细信息，请参阅官方[Microsoft 安全公告 ADV180002，指南，以缓解推理执行旁道漏洞](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 也可从 Intel [推理性执行旁道缓解措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 和 ARM [缓存推理旁道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)获取指南。 有关 Spectre 和 Meltdown 缓解措施的特定于 Windows 的概述，请参阅[了解 Windows 系统上的 Spectre 和 Meltdown 缓解措施的性能影响](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)。 有关解决的 MSVC 缓解 Spectre 漏洞的概述，请参阅[Spectre 缓解措施在 MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./)在C++团队博客。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页    。

1. 在**其他选项**框中输入 **/Qspectre** 编译器选项。 选择**确定**以应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
