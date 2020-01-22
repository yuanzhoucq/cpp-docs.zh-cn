---
title: /QIntel-jcc-erratum
description: 描述 Microsoft C/C++编译器（MSVC）/QIntel-jcc-erratum 选项。
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520917"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

Visual Studio 2019 版本16.5 及更高版本中提供了 **/QIntel-jcc-erratum**选项。

::: moniker-end

::: moniker range=">=vs-2019"

指定编译器将生成说明，以减少某些 Intel 处理器上由 Intel 跳转条件代码（JCC）错误微代码更新导致的性能影响。

## <a name="syntax"></a>语法

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>备注

在 **/QIntel-jcc-erratum**下，编译器会检测在32字节边界交叉或结束的跳转和以宏为 它将这些指令与边界对齐。 此更改减轻了在某些 Intel 处理器中阻止 JCC 错误的微码更新对性能的影响。 有关错误的详细信息，请参阅 Intel 网站上[的跳转条件代码错误的缓解措施](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf)。

Visual Studio 2019 版本16.5 及更高版本中提供了 **/QIntel-jcc-erratum**选项。 此选项仅适用于面向 x86 和 x64 的编译器。 此选项在面向 ARM 处理器的编译器中不可用。

默认情况下， **/QIntel-jcc-erratum**选项处于关闭状态，并且仅适用于优化的生成。 此选项可能会增加代码大小。

**/QIntel-jcc-erratum**与[/clr](clr-common-language-runtime-compilation.md)不兼容。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" > " **C/C++**  >**代码生成**" 属性页。

1. 为 "**启用 INTEL JCC 错误缓解**" 属性选择一个值。 选择“确定”应用更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)\
[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

::: moniker-end
