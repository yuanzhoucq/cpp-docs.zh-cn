---
title: / POGOSAFEMODE (在线程安全模式下运行 PGO)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: f210884d693ef0d778943580b9c5a7b2ec2ea336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544425"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (在线程安全模式下运行 PGO)

**/POGOSAFEMODE 选项已弃用从 Visual Studio 2015 开始**。 使用[/GENPROFILE： 确切](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)并 **/GENPROFILE:NOEXACT**改为选项。 **/POGOSAFEMODE**链接器选项指定在检测的生成创建要用于数据配置文件按配置优化 (PGO) 在配置文件数据捕获训练运行的线程安全模式。

## <a name="syntax"></a>语法

> **/POGOSAFEMODE**

## <a name="remarks"></a>备注

按配置优化 (PGO) 在分析阶段有两个可能的模式：*快速模式*并*安全模式下*。 分析在快速模式下时，它使用的增量指令来增加数据计数器。 增量指令速度更快，但不是线程安全的。 分析在安全模式下时，它使用互锁增量指令来增加数据计数器。 此指令具有相同的功能，如增量指令，并且是线程安全的但它是速度较慢。

**/POGOSAFEMODE**选项设置为使用安全模式下，检测的生成。 此选项仅可时使用已弃用[/ltcg: pginstrument](ltcg-link-time-code-generation.md)指定，则在 PGO 检测链接器阶段。

默认情况下，PGO 分析以快速模式操作。 **/ POGOSAFEMODE**是仅在需要你想要使用安全模式。

若要运行 PGO 分析在安全模式下，必须使用任一 **/GENPROFILE： 确切**（首选） 或使用环境变量[PogoSafeMode](environment-variables-for-profile-guided-optimizations.md)或链接器开关 **/POGOSAFEMODE**，取决于系统。 如果您正在执行分析在 x64 计算机，必须使用链接器开关。 如果您正在执行分析 x86 计算机，可以使用链接器开关或开始 PGO 检测过程之前将环境变量定义为任何值。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 在中**链接时间代码生成**属性中，选择**按配置优化-检测 (/: pginstrument)**。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/POGOSAFEMODE**到选项**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[按配置文件优化](../../build/reference/profile-guided-optimizations.md)<br/>
[用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
