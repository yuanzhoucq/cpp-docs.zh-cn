---
title: /Qpar-report（自动并行化程序报告等级）
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 4f3f496deb9f87d4f33f5e36832bd46405a482b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550028"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report（自动并行化程序报告等级）

启用报表功能的编译器[自动并行化程序](../../parallel/auto-parallelization-and-auto-vectorization.md)，并在编译期间指定的输出信息性消息的级别。

## <a name="syntax"></a>语法

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>备注

**/Qpar-报告： 1**<br/>
为并行化的循环输出提供相关信息的消息。

**/Qpar-报表： 2**<br/>
为并行化的循环和未并行化的循环输出提供相关信息的消息以及原因代码。

消息报告为 stdout。 如果未报告任何提供相关信息的消息，则该代码不包含任何循环，或者报告级别未设置为报告未并行化的循环。 有关原因代码和消息的详细信息，请参阅[矢量化程序和并行化程序消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Qpar-report 编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在中**属性页**对话框中的**C/c + +**，选择**命令行**。

1. 在中**其他选项**框中，输入`/Qpar-report:1`或`/Qpar-report:2`。

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>以编程方式设置 /Qpar-report 编译器选项

- 使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[本机代码中的并行编程](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)