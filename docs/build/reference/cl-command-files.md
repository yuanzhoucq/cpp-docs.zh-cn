---
title: CL 命令文件
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440263"
---
# <a name="cl-command-files"></a>CL 命令文件

命令文件是一个文本文件，其中包含你要在[命令行](compiler-command-line-syntax.md)上键入或使用[CL 环境变量](cl-environment-variables.md)指定的选项和文件名。 CL 接受编译器命令文件作为 CL 环境变量或命令行中的参数。 与命令行或 CL 环境变量不同，命令文件允许使用多行选项和文件名。

命令文件中的选项和文件名根据 CL 环境变量或命令行中命令文件名的位置进行处理。 但是，如果在命令文件中出现/link 选项，则行的其余部分上的所有选项将传递到链接器。 命令文件中后续行中的选项以及命令文件调用后的命令行上的选项仍作为编译器选项接受。 有关选项顺序如何影响其解释的详细信息，请参阅[CL 选项的顺序](order-of-cl-options.md)。

命令文件不能包含 CL 命令。 每个选项必须在同一行中开始和结束;不能使用反斜杠（ **\\** ）来跨两行合并选项。

命令文件由 at 符号（ **\@** ）后跟文件名指定;文件名可以指定绝对路径或相对路径。

例如，如果以下命令位于名为 RESP 的文件中：

```
/Og /link LIBC.LIB
```

并指定以下 CL 命令：

```
CL /Ob2 @RESP MYAPP.C
```

CL 的命令如下所示：

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

请注意，命令行和命令文件命令实际上是组合在一起的。

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[MSVC 编译器选项](compiler-options.md)
