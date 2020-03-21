---
title: /Z7、/Zi、/ZI（调试信息格式）
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078268"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）

指定为程序创建的调试信息的类型，以及是将此信息保存在对象文件中还是保存在程序数据库（PDB）文件中。

## <a name="syntax"></a>语法

> **/Z**{**7**|**我**|**i**}

## <a name="remarks"></a>备注

当在调试模式下编译和生成代码时，编译器将生成用于调试器所使用的函数和变量、类型信息和行号位置的符号名称。 此符号调试信息可以包含在编译器生成的对象文件（.obj 文件）中，也可以包含在可执行文件的单独 PDB 文件（.pdb 文件）中。  以下部分介绍了 "调试信息格式" 选项。

### <a name="none"></a>无

默认情况下，如果未指定 "调试信息格式" 选项，则编译器不会生成任何调试信息，因此编译速度会更快。

### <a name="z7"></a>/Z7

**/Z7**选项生成对象文件，这些对象文件还包含用于调试器的完整符号调试信息。 这些对象文件和生成的可执行文件可能比没有调试信息的文件大得多。 符号化调试信息包含变量的名称和类型以及函数和行号。 不生成 PDB 文件。

对于第三方库的调试版本的分发服务器，无需具有 PDB 文件的优点。 但是，在库链接阶段和调试期间，任何预编译标头的对象文件都是必需的。 如果 .pch 对象文件中仅有类型信息（而不包含代码），则在生成库时，还必须使用默认情况下启用的 " [/Yl （为调试库插入 Pch 引用）](yl-inject-pch-reference-for-debug-library.md) " 选项。

指定 **/Z7**时，不推荐使用的[/Gm （启用最小重新生成）](gm-enable-minimal-rebuild.md)选项。

### <a name="zi"></a>/ZI

**/Zi**选项将生成一个单独的 PDB 文件，其中包含用于调试器的所有符号调试信息。 调试信息不包含在对象文件或可执行文件中，这会使它们变得更小。

使用 **/zi**不会影响优化。 但 **/zi**确实表示 **/debug**;有关详细信息，请参阅[/debug （生成调试信息）](debug-generate-debug-info.md) 。

同时指定 **/zi**和 **/clr**时，不会将 <xref:System.Diagnostics.DebuggableAttribute> 特性置于程序集元数据中。 如果需要，必须在源代码中指定。 该特性可影响应用程序的运行时性能。 有关可**调试**属性如何影响性能以及如何修改性能影响的详细信息，请参阅[使映像更易于调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

编译器将 PDB 文件命名为 *.pdb。* 如果编译项目外的文件，编译器会创建一个名为 VC*x*.PDB 的 pdb 文件，其中*x*是使用中编译器版本的主版本号和次版本号的串联。 编译器将 PDB 名称和标识带时间戳的签名嵌入到使用此选项创建的每个对象文件中，这会将调试器指向符号和行号信息的位置。 PDB 文件中的名称和签名必须与要在调试器中加载的符号的可执行文件匹配。 WinDBG 调试器可以使用 `.symopt+0x40` 命令加载不匹配的符号。 Visual Studio 没有用于加载不匹配符号的类似选项。

如果从使用 **/zi**编译的对象创建库，则在库链接到程序时，关联的 .pdb 文件必须可用。 因此，如果分发库，还必须分发 PDB 文件。 若要在不使用 PDB 文件的情况下创建包含调试信息的库，则必须选择 **/Z7**选项。 如果使用预编译标头选项，则预编译标头和其他源代码的调试信息都放在 PDB 文件中。

### <a name="zi"></a>/ZI

**/Zi**选项类似于 **/zi**，但它以支持 "[编辑并继续](/visualstudio/debugger/edit-and-continue-visual-cpp)" 功能的格式生成 PDB 文件。 若要使用 "编辑并继续" 调试功能，必须使用此选项。 "编辑并继续" 功能对于开发人员的工作效率非常有用，但可能会导致代码大小、性能和编译器一致性问题。 由于大多数优化与 "编辑并继续" 不兼容，因此使用 **/zi**会禁用代码中的任何 `#pragma optimize` 语句。 **/Zi**选项与使用[ &#95; &#95;行&#95; &#95;预定义宏](../../preprocessor/predefined-macros.md)也不兼容;使用 **/zi**编译的代码不能使用 **&#95; &#95;line&#95;** 作为非类型模板参数 **&#95; &#95;&#95; ，但可以**在宏扩展中使用 line。

**/Zi**选项强制在编译中使用[/Gy （启用函数级链接）](gy-enable-function-level-linking.md)和[/FC （诊断中源代码文件的完整路径）](fc-full-path-of-source-code-file-in-diagnostics.md)选项。

**/Zi**与[/Clr （公共语言运行时编译）](clr-common-language-runtime-compilation.md)不兼容。

> [!NOTE]
> **/Zi**选项仅适用于面向 x86 和 x64 处理器的编译器;此编译器选项在面向 ARM 处理器的编译器中不可用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开 "**配置属性**" > **CC++ /**  > **常规**属性页。

1. 修改 "**调试信息格式**" 属性。 选择“确定”以保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
