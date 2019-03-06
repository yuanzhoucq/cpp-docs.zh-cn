---
title: /Z7、/Zi、/ZI（调试信息格式）
ms.date: 02/22/2018
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
ms.openlocfilehash: d8aadca14f52432e3fccb168c213ae566b1baae2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421432"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）

指定为您的程序并已将此信息保存在对象文件或程序数据库 (PDB) 文件中创建的调试信息的类型。

## <a name="syntax"></a>语法

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>备注

当代码编译和生成在调试模式下时，编译器将生成函数和变量、 类型信息和行号位置以供调试程序符号的名称。 此符号化调试信息可以包含由编译器生成的对象文件 （.obj 文件） 或可执行文件的独立 PDB 文件 （.pdb 文件） 中。  以下各节所述的调试信息格式选项。

### <a name="none"></a>无

默认情况下，如果未不指定任何调试信息格式选项，编译器会生成任何调试信息，因此编译较快。

### <a name="z7"></a>/Z7

**/Z7**选项将生成对象文件还包含用于调试器的完整符号调试的信息。 这些对象文件，并生成可执行文件可能会显著大于没有调试信息的文件。 符号化调试信息包含变量的名称和类型以及函数和行号。 会不生成任何 PDB 文件。

对于第三方库的调试版本的分发服务器，没有到没有 PDB 文件的一个优点。 但是，任何预编译标头的对象文件是必需的库链接阶段，以及用于调试。 如果仅键入.pch 对象文件中的信息 （和无代码），还必须使用[/Yl （为调试库插入 PCH 引用）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)选项，在生成库时，默认情况下，启用该选项。

[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)选项不可用 **/z7**指定。

### <a name="zi"></a>/ZI

**/Zi**选项将生成单独的 PDB 文件包含所有的符号调试信息使用调试程序。 调试信息不包括在对象文件或可执行文件，使其更小得多。

利用 **/Zi**不会影响优化。 但是， **/Zi**意味着 **/debug**; 请参阅[/DEBUG （生成调试信息）](../../build/reference/debug-generate-debug-info.md)有关详细信息。

同时指定当 **/Zi**并 **/clr**，则<xref:System.Diagnostics.DebuggableAttribute>属性不会放入程序集元数据。 如果您希望它，必须指定它的源代码中。 该特性可影响应用程序的运行时性能。 详细了解如何**Debuggable**属性会影响性能以及如何可以修改性能的影响，请参阅[令映像更易于调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

编译器命名的 PDB 文件*项目*.pdb。 如果编译在项目外部文件，编译器将创建一个名为 VC 的 PDB 文件*x*.pdb，其中*x*是串联中使用的编译器版本的主版本号和次版本号。 编译器将使用此选项，调试器指向符号和行号信息的位置创建的每个对象文件中嵌入 PDB 和标识的时间戳签名的名称。 名称和 PDB 文件中的签名必须匹配要在调试器中加载符号的可执行文件。 WinDBG 调试器可通过使用负载不匹配的符号`.symopt+0x40`命令。 Visual Studio 没有加载不匹配的符号有类似选项。

如果从使用已编译的对象创建一个库 **/Zi**，库链接到程序关联的.pdb 文件必须可用。 因此，如果分发此库，则还必须分发 PDB 文件。 若要创建的库，而无需使用 PDB 文件包含调试信息，必须选择 **/z7**选项。 如果你使用预编译标头选项，预编译标头和源代码的其余部分调试信息放置在 PDB 文件中。

### <a name="zi"></a>/ZI

**/ZI**选项是类似于 **/Zi**，它将生成的 PDB 文件中支持的格式，但[编辑并继续](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 若要使用编辑并继续调试功能，必须使用此选项。 编辑并继续功能可用于开发人员工作效率，但可能会导致代码大小、 性能和编译器符合性问题。 由于大多数优化与编辑并继续不兼容，使用 **/ZI**禁用任何`#pragma optimize`在代码中的语句。 **/ZI**选项也是与使用的不兼容[ &#95;&#95;行&#95;&#95;预定义的宏](../../preprocessor/predefined-macros.md); 使用代码编译 **/ZI** ，不能使用 **&#95;&#95;行&#95;&#95;** 作为非类型模板参数，尽管 **&#95;&#95;行&#95;&#95;** 可在宏扩展。

**/ZI**选项将强制同时[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)并[/FC （完整的源代码文件路径中诊断）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)在编译中使用的选项。

**/ZI**与不兼容[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**选项才可用面向 x86 和 x64 处理器的编译器中; 此编译器选项不是面向 ARM 处理器的编译器中可用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 打开**配置属性** > **C/c + +** > **常规**属性页。

1. 修改**调试信息格式**属性。 选择“确定”以保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
