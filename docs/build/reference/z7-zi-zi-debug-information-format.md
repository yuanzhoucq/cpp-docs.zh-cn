---
title: -Z7，-Zi，-ZI （调试信息格式） |Microsoft 文档
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86605b8fd47c0febedfc9ab022dfc2c2728822a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379076"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）

指定为你的程序将此信息保存在对象文件或程序数据库 (PDB) 文件中创建的调试信息的类型。

## <a name="syntax"></a>语法

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>备注

当代码在编译和生成在调试模式下时，编译器将生成函数和变量、 类型信息和行号位置供调试器使用的符号的名称。 此符号化调试信息可以包含在编译器中，生成的对象文件 （.obj 文件） 或者的可执行文件的单独 PDB 文件 （.pdb 文件） 中。  以下各节所述的调试信息格式选项。  
  
### <a name="none"></a>无

默认情况下，如果未不指定任何调试信息格式选项，则编译器将产生任何调试信息，因此编译较快。  
  
### <a name="z7"></a>/Z7

**/Z7**选项生成对象文件，其中还包含完整符号调试信息使用的调试器。 这些对象文件和生成的可执行文件可以是实质上更大比没有调试信息的文件。 符号化调试信息包含变量的名称和类型以及函数和行号。 生成没有 PDB 文件。

对于第三方库的调试版本的分发服务器，没有与未 PDB 文件的一个优点。 但是，任何预编译标头的对象文件则需要在库链接阶段期间以及调试。 如果仅在.pch 对象文件中键入信息 （和任何代码），还必须使用[/Yl （为调试库插入 PCH 引用）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)选项，在构建库时，默认情况下，启用该选项。

[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)选项不可用 **/Z7**指定。

### <a name="zi"></a>/ZI

**/Zi**选项生成单独的 PDB 文件包含所有符号调试信息使用的调试器。 调试信息不包含在对象文件或可执行文件，这使得它们小得多。

利用 **/Zi**不会影响优化。 但是， **/Zi**未表示 **/调试**; 请参阅[/DEBUG （生成调试信息）](../../build/reference/debug-generate-debug-info.md)有关详细信息。


当您同时指定 **/Zi**和 **/clr**、<xref:System.Diagnostics.DebuggableAttribute>特性不被放置在程序集元数据。 如果你希望，必须在源代码中对它进行指定。 该特性可影响应用程序的运行时性能。 有关详细信息，如何**Debuggable**属性会影响性能，以及如何可以修改对性能的影响，请参阅[简化映像到调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

编译器命名的 PDB 文件*项目*.pdb。 如果编译在项目外部文件时，编译器将创建一个名为 VC 的 PDB 文件*x*.pdb，其中*x*中使用的编译器版本的主版本号和次版本号的串联。 编译器中使用此选项，调试器指向符号和行号信息的位置创建每个对象文件中嵌入的 PDB 和一个标识加盖时间戳签名的名称。 名称和 PDB 文件中的签名必须匹配要在调试器中加载的符号的可执行文件。 WinDBG 调试器可通过使用负载不匹配的符号`.symopt+0x40`命令。 Visual Studio 没有类似的选项，以加载不匹配的符号。

如果你从使用编译的对象创建库 **/Zi**，库链接到程序关联的.pdb 文件必须可用。 因此，如果分发此库，则还必须分配 PDB 文件。 若要创建无需使用 PDB 文件包含调试信息的库，您必须选择 **/Z7**选项。 如果你使用预编译标头选项，预编译标头和源代码的其余部分调试信息都放在 PDB 文件中。

### <a name="zi"></a>/ZI

**/ZI**选项是类似于 **/Zi**，但它会生成 PDB 文件中支持的格式[编辑并继续](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 若要使用编辑并继续调试功能，必须使用此选项。 编辑并继续功能开发人员工作效率，对于非常有用，但可能会导致在代码大小、 性能和编译器一致性问题。 因为大多数优化不使用编辑并继续兼容，所以使用 **/ZI**禁用任何`#pragma optimize`在代码中的语句。 **/ZI**选项也是使用不兼容[ &#95;&#95;行&#95;&#95;预定的义宏](../../preprocessor/predefined-macros.md); 使用代码编译 **/ZI**不能使用 **&#95;&#95;行&#95;&#95;** 作为非类型模板自变量，尽管 **&#95;&#95;行&#95;&#95;** 可以在宏扩展中使用。

**/ZI**选项强制同时[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路径的源代码文件中诊断）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)选项用于你编译。

**/ZI**与不兼容[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**选项才可用面向 x86 和 x64 处理器的编译器中; 此编译器选项不是面向 ARM 处理器的编译器中可用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 打开**配置属性** > **C/c + +** > **常规**属性页。

1. 修改**调试信息格式**属性。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  

