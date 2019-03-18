---
title: /U、/u（未定义符号）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: bfc03ebd5c900bf8bf81b4a50eed02111baf85ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822479"
---
# <a name="u-u-undefine-symbols"></a>/U、/u（未定义符号）

**/U**编译器选项可取消指定的预处理器符号。 **/U**编译器选项取消定义编译器定义的特定于 Microsoft 的符号。

## <a name="syntax"></a>语法

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>自变量

*symbol*<br/>
若要取消定义预处理器符号。

## <a name="remarks"></a>备注

既不 **/U**或 **/u**选项可以取消定义符号通过创建 **#define**指令。

**/U**选项可以取消定义通过使用以前定义的符号 **/D**选项。

默认情况下，编译器会定义以下特定于 Microsoft 的符号。

|符号|函数|
|------------|--------------|
|_CHAR_UNSIGNED|默认 char 类型是无符号。 定义何时[/J](j-default-char-type-is-unsigned.md)指定选项。|
|_CPPRTTI|为使用编译的代码定义[/GR](gr-enable-run-time-type-information.md)选项。|
|_CPPUNWIND|为使用编译的代码定义[/EHsc](eh-exception-handling-model.md)选项。|
|_DLL|定义何时[/MD](md-mt-ld-use-run-time-library.md)指定选项。|
|_M_IX86|默认情况下，为适用于 x86 的 600 定义目标。|
|_MSC_VER|有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。|
|_WIN32|为 WIN32 应用程序定义。 始终定义。|
|_MT|定义何时[/MD 或 /MT](md-mt-ld-use-run-time-library.md)指定选项。|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**高级**属性页。

1. 修改**取消定义预处理器**或**取消定义所有预处理器定义**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/J（默认 char 类型是无符号的）](j-default-char-type-is-unsigned.md)<br/>
[/GR（启用运行时类型信息）](gr-enable-run-time-type-information.md)<br/>
[/EH（异常处理模型）](eh-exception-handling-model.md)<br/>
[/MD、/MT、/LD（使用运行时库）](md-mt-ld-use-run-time-library.md)
