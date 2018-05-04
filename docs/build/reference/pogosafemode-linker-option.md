---
title: / POGOSAFEMODE (在线程安全模式下的运行 PGO) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- POGOSAFEMODE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81392c67b47a0fa90c057ee4295667a054e34498
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (在线程安全模式下的运行 PGO)

**/POGOSAFEMODE 选项已弃用从 Visual Studio 2015 开始**。 使用[/GENPROFILE： 确切](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)和 **/GENPROFILE:NOEXACT**改为选项。 **/POGOSAFEMODE**链接器选项指定检测的生成创建要用于数据期间按配置优化 (PGO) 配置文件数据捕获定型运行的线程安全模式。

## <a name="syntax"></a>语法

> **/POGOSAFEMODE**

## <a name="remarks"></a>备注

按配置优化 (PGO) 的分析阶段有两种可能的模式：*快速模式*和*安全模式下*。 分析在快速模式下时，它使用的增量指令来增加数据计数器。 递增指令速度更快，但不是线程安全。 分析在安全模式下时，它使用互锁增量指令来增加数据计数器。 此指令具有相同的功能，如增量指令，并且初始屏幕是线程安全的但它会慢些。

**/POGOSAFEMODE**选项设置为使用安全模式下，检测的生成。 此选项只能时使用不推荐使用[/ltcg: pginstrument](ltcg-link-time-code-generation.md)期间 PGO 检测链接器阶段指定。

默认情况下，PGO 分析会在运行快速模式。 **/ POGOSAFEMODE**是仅需要你想要使用安全模式。

若要运行 PGO 分析在安全模式下，你必须使用 **/GENPROFILE： 确切**（首选），或使用环境变量[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md)或链接器开关 **/POGOSAFEMODE**，取决于系统。 如果你正在执行分析在 x64 计算机，你必须使用链接器开关。 如果你正在执行分析 x86 计算机，你可以使用链接器开关或开始 PGO 检测过程之前将环境变量定义为任何值。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 在**链接时间代码生成**属性，选择**按配置优化 – 检测 (/: pginstrument)**。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/POGOSAFEMODE**选项到**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[按配置文件优化](../../build/reference/profile-guided-optimizations.md)<br/>
[用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
