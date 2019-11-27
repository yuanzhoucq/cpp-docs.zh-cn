---
title: /GX（启用异常处理）
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245091"
---
# <a name="gx-enable-exception-handling"></a>/GX（启用异常处理）

已弃用。 使用假设使用 `extern "C"` 声明的函数不会引发异常，实现同步异常处理。

## <a name="syntax"></a>语法

```
/GX
```

## <a name="remarks"></a>备注

**/Gx**已弃用。 改为使用等效的[/ehsc](eh-exception-handling-model.md)选项。 有关弃用的编译器选项的列表，请参阅[按类别列出的编译器选项](compiler-options-listed-by-category.md)中的 "**弃用和删除编译器选项**" 部分。

默认情况下，当您使用 Visual Studio 开发环境进行编译时， **/ehsc**（等效于 **/gx**）生效。 使用命令行工具时，不指定异常处理。 这等效于 **/GX-** 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 在导航窗格中，依次选择 "**配置属性**"、" **CC++/** " 和 "**命令行**"。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/EH（异常处理模型）](eh-exception-handling-model.md)
