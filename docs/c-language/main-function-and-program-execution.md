---
title: main 函数和程序执行
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: 28b0d826dc02376f952d3522f2f037eacd298b8e
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123937"
---
# <a name="main-function-and-program-execution"></a>main 函数和程序执行

每个 C 程序都有必须命名为 main  的主函数。 如果你的代码遵循 Unicode 编程模型，则可以使用 main  的宽字符版本 wmain  。 main  函数充当程序执行的起点。 它通常通过将调用定向到程序中的其他函数来控制程序执行。 尽管程序可以因为各种原因在程序的其他点上终止，但它通常在 main  的结尾处停止执行。 有时，当检测到某一错误时，您可能希望强制终止程序。 为此，请使用 exit  函数。 有关使用 [exit](../c-runtime-library/reference/exit-exit-exit.md) 函数的信息和示例，请参阅《运行时库参考》  。

## <a name="syntax"></a>语法

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>备注

源程序中的函数执行一个或多个特定任务。 main  函数可调用这些函数来执行其各自的任务。 当 main  调用另一函数时，它会将执行控制权交给该函数，以便执行在该函数中的第一个语句处开始。 当执行 `return` 语句或到达某个函数的末尾时，该函数会将控制权返回给 main  。

可以声明任何函数（包括 main  ）以包含参数。 术语“参数”或“形参”指的是接收传递到函数的值的标识符。 有关将实参传递到形参的信息，请参阅[参数](../c-language/parameters.md)。 当一个函数调用另一个函数时，被调用的函数将从实施调用的函数接收其参数的值。 这些值称为“自变量”。 可以将形参声明为 main  ，以便让它使用以下格式从命令行接收实参：

在将信息传递给 main  函数时，尽管 C 编译器不需要这些名称，但上述参数在传统上命名为 `argc` 和 `argv`。 `argc` 和 `argv` 的类型由 C 语言定义。 传统上，如果将第三个参数传递给 main  ，该参数将命名为 `envp`。 本节后面的示例演示如何使用这三个参数访问命令行自变量。 以下各节说明了这些参数。

有关 main  的宽字符版本的说明，请参阅[使用 wmain](../c-language/using-wmain.md)。

## <a name="see-also"></a>请参阅

[main 函数和命令行参数 (C++)](../cpp/main-function-command-line-args.md)\
[分析 C 命令行参数](../c-language/parsing-c-command-line-arguments.md)
