---
title: /FC（所诊断源代码文件的完整路径）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 190174e1e2ac4d160140ddc54f9cc1c3a1b31709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271289"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC（所诊断源代码文件的完整路径）

会导致编译器显示传递到编译器诊断中源代码文件的完整路径。

## <a name="syntax"></a>语法

> /FC

## <a name="remarks"></a>备注

请考虑下面的代码示例：

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

无需 **/FC**，诊断文本将类似于以下诊断文本：

- compiler_option_FC.cpp(5) : error C2143: syntax error : missing ';' before '}'

与 **/FC**，诊断文本将类似于以下诊断文本：

- c:\test\compiler_option_fc.cpp(5) : error C2143: syntax error : missing ';' before '}'

**/FC**如果你想要查看的文件名称的完整路径，使用时也需要&#95;&#95;文件&#95;&#95;宏。 请参阅[预定义的宏](../../preprocessor/predefined-macros.md)有关详细信息&#95;&#95;文件&#95;&#95;。

**/FC**选项也将暗示 **/ZI**。 有关详细信息 **/ZI**，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](z7-zi-zi-debug-information-format.md)。

**/FC**输出采用小写格式的完整路径。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **高级**属性页。

1. 修改**使用完全路径**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
