---
title: /Qpar-report（自动并行化程序报告等级）
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: ea3e430dec61d35b8540792773b5519e64cedaef
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373783"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report（自动并行化程序报告等级）

启用编译器[自动并行](../../parallel/auto-parallelization-and-auto-vectorization.md)的报告功能，并指定编译过程中输出的信息性消息的级别。

## <a name="syntax"></a>语法

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>备注

**/Qpar-report：1**<br/>
为并行化的循环输出提供相关信息的消息。

**/Qpar-report：2**<br/>
为并行化的循环和未并行化的循环输出提供相关信息的消息以及原因代码。

消息报告为 stdout。 如果未报告任何提供相关信息的消息，则该代码不包含任何循环，或者报告级别未设置为报告未并行化的循环。 有关原因代码和消息的详细信息，请参阅[向量化和并行消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Qpar-report 编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在 "**属性页**" 对话框中的 " **c/c + +**" 下，选择 "**命令行**"。

1. 在 "**附加选项**" 框中，输入 `/Qpar-report:1` 或 `/Qpar-report:2` 。

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>以编程方式设置 /Qpar-report 编译器选项

- 使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。

## <a name="see-also"></a>另请参阅

[/Q 选项（低级别操作）](q-options-low-level-operations.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[Visual Studio 中的本机代码矢量化](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
