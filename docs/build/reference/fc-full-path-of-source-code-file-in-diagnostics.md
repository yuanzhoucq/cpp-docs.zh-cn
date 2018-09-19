---
title: -FC （诊断中源代码文件的完整路径） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d34fe85354d218d2499dbece70964c2e55e2592
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702702"
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

- compiler_option_FC.cpp(5)： 错误 C2143： 语法错误： 缺少; 之前}

与 **/FC**，诊断文本将类似于以下诊断文本：

- c:\test\compiler_option_fc.cpp(5)： 错误 C2143： 语法错误： 缺少; 之前}

**/FC**如果你想要查看的文件名称的完整路径，使用时也需要&#95;&#95;文件&#95;&#95;宏。 请参阅[预定义的宏](../../preprocessor/predefined-macros.md)有关详细信息&#95;&#95;文件&#95;&#95;。

**/FC**选项也将暗示 **/ZI**。 有关详细信息 **/ZI**，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

**/FC**输出采用小写格式的完整路径。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **高级**属性页。

1. 修改**使用完全路径**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
