---
title: -Qvec-report （自动矢量化程序报告等级） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c11beb3f8a5b9b189fff237012580765f8858fc0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717556"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report（自动矢量化程序报告等级）

启用报表功能的编译器[自动向量化](../../parallel/auto-parallelization-and-auto-vectorization.md)，并在编译期间指定的输出信息性消息的级别。

## <a name="syntax"></a>语法

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>备注

**/ Qvec-报告： 1**<br/>
输出已向量化的循环一条信息性消息。

**/ Qvec-报表： 2**<br/>
输出信息性消息已向量化的循环和 for 循环未向量化以及原因代码。

有关原因代码和消息的信息，请参阅[矢量化程序和并行化程序消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Qvec-report 编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在中**属性页**对话框中的**C/c + +**，选择**命令行**。

1. 在中**其他选项**框中，输入`/Qvec-report:1`或`/Qvec-report:2`。

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>若要以编程方式设置 /Qvec-report 编译器选项

- 使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。

## <a name="see-also"></a>请参阅

[/Q 选项 （低级别操作）](../../build/reference/q-options-low-level-operations.md)
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[本机代码中的并行编程](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)