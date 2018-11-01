---
title: /C（在预处理期间保留注释）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: b37e279af3995bd1d61c97dc88b49cdd95495c75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442596"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C（在预处理期间保留注释）

在预处理期间保留注释。

## <a name="syntax"></a>语法

```
/C
```

## <a name="remarks"></a>备注

此编译器选项需要 **/E**， **/P**，或 **/EP**选项。

下面的代码示例将显示源代码注释。

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

此示例将生成以下输出。

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**预处理器**属性页。

1. 修改**保留注释**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/E（预处理到 stdout）](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P（预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP（不使用 #line 指令预处理到 stdout）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)