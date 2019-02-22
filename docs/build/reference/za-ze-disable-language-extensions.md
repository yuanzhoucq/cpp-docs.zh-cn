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
ms.openlocfilehash: d24affdf92222ac50ffe72b3a1606d3f7030de60
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676469"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze（禁用语言扩展）

**/Za**编译器选项禁用并发出错误与 ANSI C89/ISO C90 不兼容的 Microsoft 扩展到 C。 已弃用 **/Ze**编译器选项将启用 Microsoft 扩展。 默认情况下将启用 Microsoft 扩展。

## <a name="syntax"></a>语法

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>备注

> [!NOTE]
> 利用 **/Za**不建议 c + + 代码的编译时。 **/Ze**选项已弃用，因为其行为是在默认情况下。 有关不推荐使用的编译器选项的列表，请参阅[已弃用并删除的编译器选项](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)。

Microsoft C/c + + 编译器支持 C 代码的编译两种方式：

- 编译器默认情况下使用 C 编译模式下，当源文件具有 *.c*扩展，或当[/Tc](tc-tp-tc-tp-specify-source-file-type.md)或[/TC](tc-tp-tc-tp-specify-source-file-type.md)指定选项。 C 编译器是 C89/C90 的编译器，默认情况下将启用 C + + 语言的 Microsoft 扩展。 有关特定扩展的详细信息，请参阅[Microsoft C 和 c + + 扩展](microsoft-extensions-to-c-and-cpp.md)。 当这两个 C 编译并 **/Za**指定选项，C 编译器严格符合 C89/C90 标准。 编译器将 Microsoft 扩展关键字作为简单标识符、 禁用的其他 Microsoft 扩展，并会自动定义[ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md)预定义C 程序的宏。

- 编译器可以编译在 c + + 编译模式下的 C 代码。 此行为是不具有的源文件的默认值 *.c*扩展，以及何时[/Tp](tc-tp-tc-tp-specify-source-file-type.md)或[/TP](tc-tp-tc-tp-specify-source-file-type.md)指定选项。 在 c + + 编译模式下，编译器支持的 ISO C99 和 C11 标准的已合并到 c + + 标准的那些部分。 几乎所有的 C 代码也是有效的 c + + 代码。 C 关键字和代码构造一小部分不是有效的 c + + 代码，或 c + + 中以不同方式解释。 根据在这些情况下标准 c + + 的编译器行为。 在 c + + 编译模式下， **/Za**选项可能导致意外的行为，不推荐使用。

其他编译器选项会影响编译器确保标准符合性的方式。 若要指定特定的标准 C 和 c + + 行为设置的方式，请参阅[/Zc](zc-conformance.md)编译器选项。 有关其他 c + + 标准的符合性设置，请参阅[触发-](permissive-standards-conformance.md)并[/std](std-specify-language-standard-version.md)编译器选项。

使用 Visual c + + 的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 在导航窗格中，选择**配置属性** > **C/c + +** > **语言**。

1. 修改**禁用语言扩展**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](compiler-options.md)<br/>
[设置编译器选项](setting-compiler-options.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
[/permissive-（标准符合性）](permissive-standards-conformance.md)<br/>
[/std（指定语言标准版本）](std-specify-language-standard-version.md)<br/>
