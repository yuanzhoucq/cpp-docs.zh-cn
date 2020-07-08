---
title: /Z7、/Zi、/ZI（调试信息格式）
ms.date: 07/06/2020
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
ms.openlocfilehash: bc3fd9c065219a128e29290084b1e1fb51fc773e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058589"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）

**`/Z7`**、 **`/Zi`** 和 **`/ZI`** 编译器选项指定为程序创建的调试信息的类型，以及此信息是保存在对象文件中，还是保存在程序数据库（PDB）文件中。

## <a name="syntax"></a>语法

> **`/Z7`**\
> **`/Zi`**\
> **`/ZI`**

## <a name="remarks"></a>备注

指定调试选项时，编译器将生成用于调试器所使用的函数和变量、类型信息和行位置的符号名称。 此符号调试信息可以包含在编译器生成的对象文件（ *`.obj`* 文件）中，也可以包含在可执行文件的单独 PDB 文件（ *`.pdb`* 文件）中。 以下部分介绍了 "调试信息格式" 选项。

### <a name="none"></a>None

默认情况下，如果未指定 "调试信息格式" 选项，则编译器不会生成任何调试信息，因此编译速度会更快。

### <a name="z7"></a>/Z7

**`/Z7`** 选项生成对象文件，这些对象还包含用于调试器的完整符号调试信息。 这些对象文件和从这些文件中构建的任何库可能会大大大于没有调试信息的文件。 符号调试信息包括变量的名称和类型、函数和行号。 编译器不生成任何 PDB 文件。 但是，如果链接器是通过选项传递的，则仍可以从这些对象文件或库生成 PDB 文件 **`/DEBUG`** 。

对于第三方库的调试版本的分发服务器，不包含 PDB 文件有一个优点。 但是，在库链接阶段和调试期间，任何预编译标头的对象文件都是必需的。 如果对象文件中仅有类型信息（而不包含代码） *`.pch`* ，则在生成库时，还必须使用默认情况下启用的[ `/Yl` （"为调试库插入 PCH 引用](yl-inject-pch-reference-for-debug-library.md)" 选项）。

指定时，"已弃用[ `/Gm` （启用最小重新生成）](gm-enable-minimal-rebuild.md) " 选项不可用 **`/Z7`** 。

### <a name="zi"></a>/ZI

**`/Zi`** 选项将生成一个单独的 PDB 文件，其中包含用于调试器的所有符号调试信息。 调试信息不包含在对象文件或可执行文件中，这会使它们变得更小。

使用 **`/Zi`** 不会影响优化。 不过， **`/Zi`** 确实表示 **`/debug`** 。 有关详细信息，请参阅[ `/DEBUG` （生成调试信息）](debug-generate-debug-info.md)。

如果同时指定 **`/Zi`** 了和 **`/clr`** ，则不会将该 <xref:System.Diagnostics.DebuggableAttribute> 特性置于程序集元数据中。 如果需要，必须在源代码中指定。 该特性可影响应用程序的运行时性能。 有关 `Debuggable` 属性如何影响性能的详细信息，以及如何修改性能影响的详细信息，请参阅[使映像更易于调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

编译器命名 PDB 文件 *`<project>.pdb`* ，其中 *`<project>`* 是项目的名称。 如果编译项目外的文件，编译器会创建一个名为的 PDB 文件 *`VC<x>.pdb`* ，其中， *`<x>`* 是所用编译器版本的主版本号和次版本号的串联。 编译器在使用此选项创建的每个对象文件中嵌入 PDB 的名称和标识带时间戳的签名。 此名称和签名将调试器指向符号和行号信息的位置。 PDB 文件中的名称和签名必须与要在调试器中加载的符号的可执行文件匹配。 WinDBG 调试器可以使用命令加载不匹配的符号 **`.symopt+0x40`** 。 Visual Studio 没有用于加载不匹配符号的类似选项。

如果通过使用编译的对象创建库，则在 **`/Zi`** 库链接到程序时，关联的 PDB 文件必须可用。 这意味着，如果分发库，还必须分发 PDB 文件。 若要在不使用 PDB 文件的情况下创建包含调试信息的库，必须选择 **`/Z7`** 选项。 如果使用预编译标头选项，则预编译标头和其他源代码的调试信息都放在 PDB 文件中。

### <a name="zi"></a>/Zi

**`/ZI`** 选项类似于 **`/Zi`** ，但它采用支持 "[编辑并继续](/visualstudio/debugger/edit-and-continue-visual-cpp)" 功能的格式生成 PDB 文件。 若要使用 "编辑并继续" 调试功能，必须使用此选项。 "编辑并继续" 功能对于开发人员的工作效率非常有用，但可能会导致代码大小、性能和编译器一致性问题。 由于大多数优化与 "编辑并继续" 不兼容，因此使用会 **`/ZI`** 禁用 `#pragma optimize` 代码中的任何语句。 **`/ZI`** 选项与使用[ `__LINE__` 预定义的宏](../../preprocessor/predefined-macros.md)也不兼容; 使用 " **`/ZI`** 不能 `__LINE__` 用作非类型模板" 参数编译的代码，但 `__LINE__` 可在宏扩展中使用。

**`/ZI`** 选项将强制在编译中使用[ `/Gy` （启用函数级链接）](gy-enable-function-level-linking.md)和[ `/FC` （诊断中源代码文件的完整路径）](fc-full-path-of-source-code-file-in-diagnostics.md)选项。

**`/ZI`** 与[ `/clr` （公共语言运行时编译）](clr-common-language-runtime-compilation.md)不兼容。

> [!NOTE]
> 此 **`/ZI`** 选项仅在面向 x86 和 x64 处理器的编译器中可用。 此编译器选项在面向 ARM 处理器的编译器中不可用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开 "**配置属性**" "  >  **c/c + +**  >  **常规**" 属性页。

1. 修改 "**调试信息格式**" 属性。 选择“确定”以保存更改  。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
