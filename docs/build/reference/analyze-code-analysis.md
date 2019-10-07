---
title: /analyze（代码分析）
ms.date: 10/01/2019
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
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816323"
---
# <a name="analyze-code-analysis"></a>/analyze（代码分析）

启用代码分析和控制选项。

## <a name="syntax"></a>语法

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>参数

/analyze 在默认模式下启用分析。 分析输出会转到**输出**窗口，如其他错误消息。 使用 **/analyze-** 显式关闭分析。

/analyze： WX-指定 **/analyze： WX-** 表示在使用 **/wx**编译时不会将代码分析警告视为错误。 有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](compiler-option-warning-level.md)。

/analyze： log `filename` 详细分析器结果将以 XML 形式写入 @no__t 指定的文件。

/analyze： quiet 关闭分析器输出到 "**输出**" 窗口。

/analyze： stacksize `number` @no__t 用于此选项的参数指定为其生成警告[C6262](/visualstudio/code-quality/c6262)的堆栈帧的大小（以字节为单位）。 @No__t-0 之前的空格是可选的。 如果未指定此参数，则默认情况下堆栈帧的大小为 16KB。

/analyze： max_paths `number` @no__t 用于此选项的参数指定要分析的代码路径的最大数目。 如果未指定此参数，则默认情况下此数目为 256。 值越大，执行的检查越彻底，但分析时间可能会更长。

/analyze：通常情况下，编译器将生成代码，并在运行分析器后进行更多语法检查。 **/Analyze： only**选项关闭此代码生成过程;这可以加快分析速度，但不会发出编译器的代码生成过程中可能发现的编译错误和警告。 如果程序存在代码生成错误，则分析结果可能不可靠；因此，建议你只有在代码已传递代码生成语法检查且没有错误时才使用此选项。

/analyze：规则集 `<file_path>.ruleset` 使你能够指定要分析的规则集，包括你可以自行创建的自定义规则集。 设置此开关后，规则引擎将更有效，因为它在运行前排除指定规则集的非成员。 如果未设置交换机，引擎将检查所有规则。

在 **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule 集中**找到了随 Visual Studio 一起提供的规则集。

下面的示例自定义规则集通知规则引擎检查 C6001 和 C26494。 可以将此文件放置在任何位置，只要该文件具有 @no__t 的扩展，就可以在参数中提供完整路径。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/analyze：插件启用指定的 PREfast 插件作为代码分析的一部分。
LocalEspC 是在 C261XX 警告范围内实现与并发相关的代码分析检查的插件。 例如， [C26100](/visualstudio/code-quality/c26100)， [C26101](/visualstudio/code-quality/c26101)，...， [C26167](/visualstudio/code-quality/c26167)。

若要运行 LocalEspC，请使用此编译器选项： **/analyze：插件 LocalEspC**

若要运行 CppCoreCheck，请首先从开发人员命令提示符处运行以下命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然后使用此编译器选项： **/analyze：插件 EspXEngine**。

## <a name="remarks"></a>备注

有关详细信息，请参阅 c [/C++概述的代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[c/C++警告的代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开 "**代码分析**" 节点。

1. 选择 **“常规”** 属性页。

1. 修改一个或多个**代码分析**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 编译器选项](compiler-options.md)
- [MSVC 编译器命令行语法](compiler-command-line-syntax.md)
