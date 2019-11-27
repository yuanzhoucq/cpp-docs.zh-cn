---
title: /analyze（代码分析）
ms.date: 10/15/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: f537fdea2703805c7ab1c57ba0d4429f6b683ae4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444896"
---
# <a name="analyze-code-analysis"></a>/analyze（代码分析）

启用代码分析和控制选项。

## <a name="syntax"></a>语法

> **/analyze**[-] [ **： WX-** ] [ **：日志***文件名*] [ **： quiet**] [ **： stacksize** *number*] [ **： max_paths** *number*] [ **： only**] [ **：规则***集规则集*] [ **:p lugin** *插件-dll*]

## <a name="arguments"></a>参数

**/analyze**\
在默认模式下打开分析。 分析输出会转到**输出**窗口，如其他错误消息。 使用 **/analyze-** 显式关闭分析。

**/analyze： WX-** \
使用 **/wx**进行编译时，不会将代码分析警告视为错误。 有关详细信息，请参阅[/wx （警告等级）](compiler-option-warning-level.md)。

**/analyze：日志***文件名*\
详细分析器结果将以 XML 形式写入*filename*指定的文件。

**/analyze： quiet**\
关闭分析器输出到 "**输出**" 窗口。

**/analyze： stacksize** *number*\
与此选项一起使用的*number*参数指定为其生成警告[C6262](/visualstudio/code-quality/c6262)的堆栈帧的大小（以字节为单位）。 *Number*之前的空格是可选的。 如果未指定此参数，则默认情况下，堆栈帧大小为16KB。

**/analyze： max_paths** *号*\
与此选项一起使用的*number*参数指定要分析的代码路径的最大数目。 如果未指定此参数，则默认情况下，该数字为256。 较大的值会导致更彻底的检查，但分析可能需要更长的时间。

**/analyze：仅**\
通常，编译器在运行分析器后会生成代码并执行更多语法检查。 **/Analyze： only**选项关闭此代码生成过程。 它提高了分析速度，但编译了编译器代码生成过程中可能找不到的错误和警告。 如果程序未出现代码生成错误，则分析结果可能不可靠。 建议仅在代码已通过代码生成语法检查且没有错误的情况下才使用此选项。

**/analyze：规则集** *file_path*\
允许您指定要分析的规则集，包括您自己可以创建的自定义规则集。 设置此开关后，规则引擎将更有效，因为它在运行前排除指定规则集的非成员。 否则，引擎将检查所有规则。

在 *%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule 集中*找到了随 Visual Studio 一起提供的规则集。

下面的示例自定义规则集通知规则引擎检查 C6001 和 C26494。 可以将此文件放置在任何位置，只要该文件具有 `.ruleset` 扩展名，就可以在参数中提供完整路径。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

**/analyze：插件***插件-dll*\
在运行代码分析过程中启用指定的 PREfast 插件。

::: moniker range="<=vs-2017"

LocalEspC 是在 C261XX 警告范围内实现与并发相关的代码分析检查的插件。 例如， [C26100](/visualstudio/code-quality/c26100)， [C26101](/visualstudio/code-quality/c26101)，...， [C26167](/visualstudio/code-quality/c26167)。

若要运行 LocalEspC，请使用此编译器选项： **/analyze：插件 LocalEspC**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck 在 C261XX 警告范围内实现与并发相关的代码分析检查。 例如， [C26100](/visualstudio/code-quality/c26100)， [C26101](/visualstudio/code-quality/c26101)，...， [C26167](/visualstudio/code-quality/c26167)。

若要运行 ConcurrencyCheck，请首先从开发人员命令提示符处运行以下命令：

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

然后使用此编译器选项： **/analyze：插件 EspXEngine**。

::: moniker-end

若要运行 CppCoreCheck，请首先从开发人员命令提示符处运行以下命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然后使用此编译器选项： **/analyze：插件 EspXEngine**。

## <a name="remarks"></a>备注

有关详细信息，请参阅 c [/C++概述的代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[c/C++警告的代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1.  > **常规**属性页中选择 "**配置属性**" > "**代码分析**"。

1. 修改一个或多个**代码分析**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
