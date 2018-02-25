---
title: "-Z7，-Zi，-ZI （调试信息格式） |Microsoft 文档"
ms.custom: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6e3de89c5336cda98960b67b80932df8f67d183
ms.sourcegitcommit: 2cca90d965f76ebf1d741ab901693a15d5b8a4df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）

指定为你的程序将此信息保存在对象文件或程序数据库 (PDB) 文件中创建的调试信息的类型。

## <a name="syntax"></a>语法

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>备注

以下各节所述的调试信息格式选项。  
  
### <a name="none"></a>无

默认情况下，如果未不指定任何调试信息格式选项，则编译器将产生任何调试信息，因此编译较快。  
  
### <a name="z7"></a>/Z7

**/Z7**选项生成*对象文件*，具有包含使用调试程序时使用的完整符号调试信息的.obj 扩展的文件。 符号化调试信息包含变量的名称和类型以及函数和行号。 不*PDB 文件*，生成的文件扩展名为.pdb。

对于分发服务器的第三方库，没有与未 PDB 文件的一个优点。 但是，预编译标头的对象文件则需要在链接阶段和调试。 如果仅在.pch 对象文件中键入信息 （和任何代码），还必须使用[/Yl （为调试库插入 PCH 引用）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)选项，它默认处于启用状态。

### <a name="zi"></a>/ZI

**/Zi**选项生成包含类型信息和符号化调试信息使用调试器的 PDB 文件。 符号化调试信息包含变量的名称和类型以及函数和行号。

利用**/Zi**不会影响优化。 但是， **/Zi**未表示**/调试**; 请参阅[/DEBUG （生成调试信息）](../../build/reference/debug-generate-debug-info.md)有关详细信息。

当**/Zi**指定，则类型信息放置在 PDB 文件中，并且不在对象文件。

你可以使用[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)连同**/Zi**，但**/Gm**不可用时**/Z7**指定。

当您同时指定**/Zi**和**/clr**、<xref:System.Diagnostics.DebuggableAttribute>特性不被放置在程序集元数据。 如果你希望，必须将它指定源代码中。 该特性可影响应用程序的运行时性能。 有关详细信息，如何**Debuggable**属性会影响性能，以及如何可以修改对性能的影响，请参阅[简化映像到调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

### <a name="zi"></a>/ZI

**/ZI**选项生成 PDB 文件中支持的格式[编辑并继续](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 如果想使用“编辑并继续”调试，则必须使用此选项。 编辑并继续功能开发人员工作效率，对于非常有用，但可能会导致在编译器一致性、 代码大小和性能问题。 因为大多数优化不使用编辑并继续兼容，所以使用**/ZI**禁用任何`#pragma optimize`在代码中的语句。 **/ZI**选项也是使用不兼容[&#95; &#95;行 &#95; &#95;预定的义宏](../../preprocessor/predefined-macros.md)。 使用代码编译**/ZI**不能使用**&#95; &#95;行 &#95; &#95;**作为非类型模板自变量，尽管**&#95; &#95;行 &#95; &#95;**可以在宏扩展中使用。

**/ZI**选项强制同时[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路径的源代码文件中诊断）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)选项用于你编译。

**/ZI**与不兼容[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**选项才可用面向 x86 和 x64 处理器的编译器中; 此编译器选项不是面向 ARM 处理器的编译器中可用。

编译器命名的 PDB 文件*项目*.pdb。 如果编译在项目外部文件时，编译器将创建一个名为 VC 的 PDB 文件*x*0.pdb，其中*x*是正在使用的 Visual Studio 版本的主要版本号。 编译器将 PDB 的名称嵌入每个使用此选项创建的 .obj 文件中，从而使调试器了解符号和行号信息的位置。 当你使用此选项时，.obj 文件是较小，因为调试信息存储在.pdb 文件而不是.obj 文件中。

如果从使用此选项编译的对象创建库，则在将库链接到程序时，关联 .pdb 文件必须可用。 因此，如果分发此库，就必须分发 PDB。

若要创建不使用.pdb 文件包含调试信息的库，你必须选择编译器的 C 7.0 兼容 (**/Z7**) 选项。 如果你使用预编译标头选项，预编译标头和源代码的其余部分调试信息都放在 PDB 文件中。 **/Yd**时指定了程序数据库选项，将忽略选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 打开**配置属性** > **C/c + +** > **常规**属性页。

1. 修改**调试信息格式**属性。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  

