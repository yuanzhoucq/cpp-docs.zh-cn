---
title: /Qvec-report（自动矢量化程序报告等级）
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 260cf89d50110f960eb6f320dccbb4a1d80f65bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373809"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report（自动矢量化程序报告等级）

启用编译器[自动向量化](../../parallel/auto-parallelization-and-auto-vectorization.md)的报告功能，并指定编译过程中输出的信息性消息的级别。

## <a name="syntax"></a>语法

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>备注

**/Qvec-report：1**<br/>
输出向量化的循环的信息性消息。

**/Qvec-report：2**<br/>
输出向量化的信息消息和未向量化的循环的信息性消息以及原因代码。

有关原因代码和消息的详细信息，请参阅[向量化和并行消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置/Qvec-report 编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在 "**属性页**" 对话框中的 " **c/c + +**" 下，选择 "**命令行**"。

1. 在 "**附加选项**" 框中，输入 `/Qvec-report:1` 或 `/Qvec-report:2` 。

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>以编程方式设置/Qvec-report 编译器选项

- 使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。

## <a name="see-also"></a>另请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[Visual Studio 中的本机代码矢量化](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
