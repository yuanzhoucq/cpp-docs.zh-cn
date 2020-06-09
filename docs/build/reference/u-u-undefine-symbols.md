---
title: /U、/u（未定义符号）
ms.date: 06/08/2020
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
ms.openlocfilehash: 4d7a2b3d5df2b22dc53eb7b58bfb78cdb1824b26
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616664"
---
# <a name="u-u-undefine-symbols"></a>/U、/u（未定义符号）

**`/U`** 编译器选项将取消指定指定的预处理器符号。 **`/u`** 编译器选项将取消定义编译器定义的特定于 Microsoft 的符号。

## <a name="syntax"></a>语法

> **`/U`**\[]*符号*\
> **`/u`**

## <a name="arguments"></a>自变量

*代号*<br/>
要取消定义的预处理器符号。

## <a name="remarks"></a>备注

**`/U`** 和选项都不 **`/u`** 能取消定义使用指令创建的符号 **`#define`** 。

**`/U`** 选项可以取消定义先前通过使用选项定义的符号 **`/D`** 。

默认情况下，编译器可能会定义大量 Microsoft 特定的符号。 下面是一些常见的：

| 符号 | 函数 |
|--|--|
| `_CHAR_UNSIGNED` | 默认 char 类型为无符号。 在 [**`/J`**](j-default-char-type-is-unsigned.md) 指定选项时定义。 |
| `_CPPRTTI` | 为用选项编译的代码定义 [**`/GR`**](gr-enable-run-time-type-information.md) 。 |
| `_CPPUNWIND` | 为用选项编译的代码定义 [**`/EHsc`**](eh-exception-handling-model.md) 。 |
| `_DLL` | 在 [**`/MD`**](md-mt-ld-use-run-time-library.md) 指定选项时定义。 |
| `_M_IX86` | 默认情况下，对于 x86 目标，定义为600。 |
| `_MSC_VER` | 定义为每个编译器版本的唯一整数值。 有关详细信息，请参阅[预定义的宏](../../preprocessor/predefined-macros.md)。 |
| `_WIN32` | 为 WIN32 应用程序定义。 始终定义。 |
| `_MT` | 指定[ **`/MD`** 或 **`/MT`** ](md-mt-ld-use-run-time-library.md)选项时定义。 |

有关特定于 Microsoft 的预定义宏的完整列表，请参阅[预定义的宏](../../preprocessor/predefined-macros.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **高级**" 属性页。

1. 修改取消**定义预处理器定义**或取消**定义所有预处理器定义**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[**`/J`**（默认 char 类型是无符号的）](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`**（启用运行时类型信息）](gr-enable-run-time-type-information.md)<br/>
[**`/EH`**（异常处理模型）](eh-exception-handling-model.md)<br/>
[**`/MD`**、 **`/MT`** 、 **`/LD`** （使用运行时库）](md-mt-ld-use-run-time-library.md)
