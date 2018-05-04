---
title: / Qspectre |Microsoft 文档
ms.custom: ''
ms.date: 1/23/2018
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
ms.openlocfilehash: 3d87850ae5413ccf876eb4d4b44b34e34527ef9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="qspectre"></a>/ Qspectre

指定编译器生成的说明进行操作以缓解特定 Spectre 变体 1 安全漏洞。

## <a name="syntax"></a>语法

> **/Qspectre**

## <a name="remarks"></a>备注

**/Qspectre**选项会使编译器将插入说明以缓解某些[Spectre 安全漏洞](https://spectreattack.com/spectre.pdf)。 调用这些漏洞*推测执行边信道攻击*、 会影响许多操作系统和现代处理器，包括从 Intel、 AMD 处理器和 ARM。

**/Qspectre**选项默认处于关闭状态。

在其初始版本中， **/Qspectre**选项仅适用于优化的代码。 你应确保你使用编译代码的任何优化选项 (例如， [/O2 或 /O1](o1-o2-minimize-size-maximize-speed.md)但不是[/Od](od-disable-debug.md)) 来确保应用缓解措施。 同样，检查使用的任何代码[#pragma 优化 ("stg"，off)](../../preprocessor/optimize.md)。

### <a name="applicability"></a>适用性

如果你的代码对跨信任边界的数据进行操作，则我们建议你使用 **/Qspectre**选项以重新构建并重新部署你的代码以尽可能快地缓解此问题。 跨信任边界的数据进行操作的代码示例包括用于加载不受信任的输入，可能会影响执行的代码，例如，代码使远程过程调用、 分析不受信任的输入或文件，或使用其他本地间进程通信 (IPC) 接口。 标准沙盒处理技术可能不足。 决定你的代码不会跨越信任边界之前，应仔细调查你沙盒。

### <a name="availability"></a>可用性

**/Qspectre**选项可用于 Visual Studio 2017 版本 15.5.5 和所有更新到 Microsoft Visual c + + 编译器 (MSVC) 或之后 2018 年 1 月 23，做。

所有版本的 Visual Studio 2017 版本 15.5 和全部预览版的 Visual Studio 版本 15.6 已包含一个未记录的选项， **/d2guardspecload**，即相当于的初始行为 **/Qspectre**. 你可以使用 **/d2guardspecload**到这些版本的编译器中的代码应用相同的缓解措施。 请更新您的生成以使用 **/Qspectre**在编译器中支持的选项; **/Qspectre**选项可能还支持更高版本的编译器中的新的缓解措施。

### <a name="effect"></a>效果

**/Qspectre**选项将输出代码以缓解产出变体 1，边界检查绕过[CVE 2017 5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)。 它通过充当推理代码执行屏障的指令的插入适用。 用于缓解处理器推理的特定说明取决于处理器和其微体系结构，并在将来版本的编译器可能会更改。

当 **/Qspectre**选项启用时，编译器将尝试标识的实例推测执行其中可能会绕过边界检查和插入的屏障说明进行操作。 请务必注意，有一些编译器可以执行以标识实例的变体 1 的分析的限制。 在这种情况下，就不能保证所有实例的变体 1 检测下 **/Qspectre**。

### <a name="performance-impact"></a>对性能的影响

对性能的影响 **/Qspectre**已出现非常可观中多个非常大型基本代码，但没有任何保证代码的性能 **/Qspectre**不受影响。 你应进行基准测试代码以确定对性能的选项的效果。 如果你知道缓解措施，不要求在性能关键的块或循环中，缓解措施可以有选择性地禁用通过使用[__declspec(spectre(nomitigation))](../../cpp/spectre.md)指令。 此指令不是在仅支持的编译器中可用 **/d2guardspecload**选项。

### <a name="additional-information"></a>其他信息

有关更多详细信息，请参阅官方[Microsoft 安全公告 ADV180002、 指南，以缓解推测执行端通道漏洞](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。 指南中也有来自 Intel，[推理执行端通道缓解措施](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)，和 ARM，[缓存推理端通道](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)。 Spectre 和垮台缓解措施的特定于 Windows 的概述，请参阅[了解在 Windows 系统上的 Spectre 和垮台缓解的性能影响](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)Microsoft 安全博客上。 由 MSVC 缓解措施的 Spectre 漏洞的概述，请参阅[中 MSVC Spectre 缓解](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./)Visual c + + 团队博客上。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入 **/Qspectre**中的编译器选项**其他选项**框。 选择**确定**以应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
