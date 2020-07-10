---
title: CL 命令文件
description: MSVC 编译器允许指定包含命令行选项的命令文件。
ms.date: 07/08/2020
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 6deab4b11dcc6c53beb5b4fa8b014a56020c3420
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180937"
---
# <a name="cl-command-files"></a>CL 命令文件

命令文件是一个文本文件，其中包含编译器选项和文件名。 它提供在[命令行](compiler-command-line-syntax.md)上键入的选项，或者使用[CL 环境变量](cl-environment-variables.md)指定。 CL 接受编译器命令文件作为参数（在 CL 环境变量中）或在命令行上接受。 与命令行或 CL 环境变量不同，可以在命令文件中使用多行选项和文件名。

当命令文件名出现在 CL 环境变量或命令行中时，将处理命令文件中的选项和文件名。 但是，如果 **`/link`** 命令文件中出现该选项，则行的其余部分上的所有选项将传递到链接器。 命令文件中后续行中的选项以及命令文件调用后命令行上的选项仍作为编译器选项接受。 有关选项顺序如何影响其解释的详细信息，请参阅[CL 选项的顺序](order-of-cl-options.md)。

命令文件不能包含 CL 命令。 每个选项必须在同一行中开始和结束;不能使用反斜杠 (**`\`**) 跨两行合并选项。

命令文件由 at 符号指定 (**`@`**) 后跟文件名。 文件名可以指定绝对路径或相对路径。

例如，如果以下命令位于名为 RESP 的文件中：

```cmd
/Ot /link LIBC.LIB
```

并指定以下 CL 命令：

```cmd
CL /Ob2 @RESP MYAPP.C
```

CL 的命令如下所示：

```cmd
CL /Ob2 /Ot MYAPP.C /link LIBC.LIB
```

在这里，你可以看到命令行和命令文件命令是如何有效组合的。

## <a name="see-also"></a>另请参阅

[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[MSVC 编译器选项](compiler-options.md)
