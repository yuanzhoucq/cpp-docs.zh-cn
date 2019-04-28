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
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315880"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze（禁用语言扩展）

**/Za**编译器选项禁用并发出错误与 ANSI C89/ISO C90 不兼容的 Microsoft 扩展到 C。 已弃用 **/Ze**编译器选项将启用 Microsoft 扩展。 默认情况下将启用 Microsoft 扩展。

## <a name="syntax"></a>语法

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>备注

> [!NOTE]
> 利用 **/Za**时代码编译为C++不建议。 **/Ze**选项已弃用，因为其行为是在默认情况下。 有关不推荐使用的编译器选项的列表，请参阅[已弃用并删除的编译器选项](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)。

Microsoft C /C++编译器支持的 C 代码编译两种方式：

- 编译器默认情况下使用 C 编译模式下，当源文件具有 *.c*扩展，或当[/Tc](tc-tp-tc-tp-specify-source-file-type.md)或[/TC](tc-tp-tc-tp-specify-source-file-type.md)指定选项。 C 编译器是 C89/C90 的编译器，默认情况下将启用 C + + 语言的 Microsoft 扩展。 有关特定扩展的详细信息，请参阅[到 C 的 Microsoft 扩展和C++ ](microsoft-extensions-to-c-and-cpp.md)。 当这两个 C 编译并 **/Za**指定选项，C 编译器严格符合 C89/C90 标准。 编译器将 Microsoft 扩展关键字作为简单标识符、 禁用的其他 Microsoft 扩展，并会自动定义[ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md)预定义C 程序的宏。

- 编译器可以在编译 C 代码中的C++编译模式。 此行为是不具有的源文件的默认值 *.c*扩展，以及何时[/Tp](tc-tp-tc-tp-specify-source-file-type.md)或[/TP](tc-tp-tc-tp-specify-source-file-type.md)指定选项。 在C++编译模式下，编译器支持的已合并到了 ISO C99 和 C11 标准那些部分C++标准。 几乎所有的 C 代码也是有效C++代码。 C 关键字和代码构造一小部分不是有效C++代码，或以不同的方式在解释C++。 编译器会根据C++在这些情况下标准。 在C++编译模式 **/Za**选项可能导致意外的行为，不推荐使用。

其他编译器选项会影响编译器确保标准符合性的方式。 有关如何指定特定的标准 C 和C++行为设置，请参阅[/Zc](zc-conformance.md)编译器选项。 有关其他C++标准符合性设置，请参阅[触发-](permissive-standards-conformance.md)并[/std](std-specify-language-standard-version.md)编译器选项。

有关使用视觉对象的一致性问题的详细信息C++，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 在导航窗格中，选择**配置属性** > **C /C++** > **语言**。

1. 修改**禁用语言扩展**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](compiler-options.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
[/permissive-（标准符合性）](permissive-standards-conformance.md)<br/>
[/std（指定语言标准版本）](std-specify-language-standard-version.md)<br/>
