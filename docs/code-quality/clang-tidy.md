---
title: 在视觉工作室中使用 Clang-Tidy
description: 如何在可视化工作室中使用Clang-Tidy进行微软C++代码分析。
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355149"
---
# <a name="using-clang-tidy-in-visual-studio"></a>在视觉工作室中使用 Clang-Tidy

::: moniker range="<=vs-2017"

支持 Clang-Tidy 需要 Visual Studio 2019 版本 16.4 或更高版本。 要查看此版本的文档，请将本文的可视化工作室**版本**选择器控件设置为 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end

::: moniker range=">=vs-2019"

代码分析本机支持用于 MSBuild 和 CMake 项目的[Clang-Tidy，](https://clang.llvm.org/extra/clang-tidy/)无论是使用 Clang 还是 MSVC 工具集。 Clang-Tidy 检查可以作为背景代码分析的一部分运行。 它们显示为编辑器内警告（摆动），并显示在错误列表中。

Clang-Tidy 支持可从 Visual Studio 2019 版本 16.4 中开始提供。 当您在可视化工作室安装程序中选择C++工作负载时，它会自动包括在内。

Clang-Tidy 是使用 LLVM/clang-cl 工具集时的默认分析工具，在 MSBuild 和 CMake 中都可用。 您可以使用 MSVC 工具集与标准代码分析体验一起运行或替换它。 如果使用 clang-cl 工具集，则 Microsoft 代码分析不可用。

Clang-Tidy 在成功编译后运行。 您可能需要解决源代码错误，以获得 Clang-Tidy 结果。

## <a name="msbuild"></a>MSBuild

您可以将 Clang-Tidy 配置为作为代码分析的一部分运行，并在"项目属性"窗口中的代码**分析** > **常规**页下生成。 配置工具的选项可以在 Clang-Tidy 子菜单下找到。

有关详细信息，请参阅[如何：为 C/C++项目设置代码分析属性](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)。

## <a name="cmake"></a>CMake

在"制作"项目中，可以在 中`CMakeSettings.json`配置 Clang-Tidy 检查。 打开后，单击"完成项目设置编辑器"右上角的"编辑 JSON"。 识别以下键：

- `enableMicrosoftCodeAnalysis`： 启用微软代码分析
- `enableClangTidyCodeAnalysis`： 启用 Clang-Tidy 分析
- `clangTidyChecks`：Clang-Tidy 配置，指定为逗号分隔列表，即要启用或禁用的检查

如果未指定两个"启用"选项，Visual Studio 将选择与所使用的平台工具集匹配的分析工具。

## <a name="warning-display"></a>警告显示

Clang-Tidy 运行会导致错误列表中显示的警告，并且作为编辑器中的代码相关部分下方的摆动。 使用错误列表中的"类别"列对 Clang-Tidy 警告进行排序和组织。 您可以通过切换"禁用代码分析摆动"设置在 **"工具** > **选项**"下配置编辑器内警告。

## <a name="clang-tidy-configuration"></a>Clang-Tidy 配置

您可以通过**Clang-Tidy 检查**选项配置在 Visual Studio 中运行的支票。 此输入提供给工具的 **--检查**参数。 任何进一步的配置都可以包含在自定义*`.clang-tidy`* 文件中。 有关详细信息，请参阅[有关 LLVM.org 的 Clang-Tidy 文档](https://clang.llvm.org/extra/clang-tidy/)。

## <a name="see-also"></a>另请参阅

- [Clang/LLVM 支持 MS 建设项目](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Clang/LLVM 支持 CMake 项目](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
