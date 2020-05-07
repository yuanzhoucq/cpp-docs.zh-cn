---
title: /Za、/Ze（禁用语言扩展）
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825870"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze（禁用语言扩展）

**/Za**编译器选项禁用与 ANSI C89/ISO C90 不兼容的 Microsoft 扩展到 C 的错误和发出错误。 弃用的 **/ze**编译器选项启用 Microsoft 扩展。 默认情况下将启用 Microsoft 扩展。

## <a name="syntax"></a>语法

> **/Za**\
> **/Ze**

## <a name="remarks"></a>备注

> [!NOTE]
> 不建议在将代码编译为 c + + 时使用 **/za** 。 已弃用 **/ze**选项，因为默认情况下其行为处于启用状态。 有关弃用的编译器选项的列表，请参阅[已弃用和已删除的编译器选项](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)。

Microsoft C/c + + 编译器支持通过两种方式编译 C 代码：

- 默认情况下，当源文件具有 *.c*扩展名或指定了[/tc](tc-tp-tc-tp-specify-source-file-type.md)或[/tc](tc-tp-tc-tp-specify-source-file-type.md)选项时，编译器将默认使用 c 编译模式。 C 编译器是 C89/C90 编译器，默认情况下，它会启用 Microsoft 对 C 语言的扩展。 有关特定扩展的详细信息，请参阅[Microsoft c 和 c + + 扩展](microsoft-extensions-to-c-and-cpp.md)。 如果同时指定了 C 编译和 **/za**选项，则 c 编译器严格符合 C89/C90 标准。 编译器将 Microsoft 扩展关键字视为简单标识符，禁用其他 Microsoft 扩展，并自动定义 C 程序的[ \_ \_STDC\_ ](../../preprocessor/predefined-macros.md)预定义宏。

- 编译器可在 c + + 编译模式下编译 C 代码。 此行为是没有 *.c*扩展名的源文件的默认行为，并在指定了[/tp](tc-tp-tc-tp-specify-source-file-type.md)或[/tp](tc-tp-tc-tp-specify-source-file-type.md)选项时使用。 在 c + + 编译模式下，编译器支持已合并到 c + + 标准中的 ISO C99 和 C11 标准的这些部分。 几乎所有 C 代码都是有效的 c + + 代码。 少量 C 关键字和代码构造不是有效的 c + + 代码，或在 c + + 中以不同的方式解释。 在这些情况下，编译器将根据 c + + 标准行为。 在 c + + 编译模式下， **/za**选项可能导致意外的行为，因此不建议使用。

其他编译器选项可能会影响编译器确保标准一致性的方式。 有关指定特定标准 C 和 c + + 行为设置的方法，请参阅[/zc](zc-conformance.md)编译器选项。 有关其他 c + + 标准一致性设置，请参阅[/permissive-](permissive-standards-conformance.md)和[/std](std-specify-language-standard-version.md)编译器选项。

有关 Visual C++ 的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 在导航窗格中，选择 "**配置属性** > " "**c/c + +** > **语言**"。

1. 修改 "**禁用语言扩展**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A> 。

## <a name="see-also"></a>另请参阅

[编译器选项](compiler-options.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
[/permissive-（标准符合性）](permissive-standards-conformance.md)<br/>
[/std （指定语言标准版本）](std-specify-language-standard-version.md)<br/>
