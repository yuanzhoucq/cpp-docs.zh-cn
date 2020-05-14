---
title: 优化最佳做法
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328443"
---
# <a name="optimization-best-practices"></a>优化最佳做法

本文档介绍了在 Visual Studio 优化 C++ 程序的一些最佳做法。

## <a name="compiler-and-linker-options"></a>编译器和链接器选项

### <a name="profile-guided-optimization"></a>按配置优化

Visual Studio 支持“按配置优化”(PGO)  。 此优化使用应用程序检测版本的训练执行的配置文件数据，以驱动应用程序的后续优化。 使用 PGO 可能很耗时，因此它可能不是每个开发人员都会使用的内容，但是我们建议在产品的最终发布版本中使用 PGO。 有关详细信息，请参阅[按配置优化](profile-guided-optimizations.md)。

此外，全程序优化（也称为链接时间代码生成）和“/O1”和“/O2”优化也得到了改进    。 通常，使用这些选项之一编译的应用程序将比使用早期编译器编译的同一应用程序更快。

有关详细信息，请参阅 [/GL（全程序优化）](reference/gl-whole-program-optimization.md)和[/O1、/O2（最小化大小、最大化速度）](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>要使用的优化级别

如果可能的话，最终发布版本应使用按配置优化进行编译。 如果无法使用 PGO 生成，无论是由于运行检测生成的基础结构不足，还是无法访问方案，我们建议使用全程序优化进行生成。

“/Gy”开关也非常有用  。 它为每个函数生成单独的 COMDAT，在删除未引用的 COMDAT 和 COMDAT 折叠时，这为链接器提供了更大的灵活性。 使用“/Gy”的唯一缺点是：调试时可能会导致问题  。 因此，通常建议使用此开关。 有关详细信息，请参阅 [/Gy （启用函数级链接）](reference/gy-enable-function-level-linking.md)。

对于 64 位环境中的链接，建议使用“/OPT:REF,ICF”链接器选项，而在 32 位环境中，建议使用“/OPT:REF”   。 有关详细信息，请参阅 [/OPT（优化）](reference/opt-optimizations.md)。

强烈建议生成调试符号，即使使用优化的发布版本。 它不会影响生成的代码，而且如果需要的话，它使调试应用程序变得更加容易。

### <a name="floating-point-switches"></a>浮点开关

已删除“/Op”编译器选项，并添加了以下四个处理浮点优化的编译器选项  ：

|||
|-|-|
|**/fp:precise**|这是默认的建议，应在大多数情况下使用。|
|**/fp:fast**|如果性能是最重要的，则推荐使用，例如在游戏中。 这将产生最快的性能。|
|**/fp:strict**|如果需要精确的浮点异常和 IEEE 行为，建议使用。 这将产生最慢的性能。|
|**/fp:except[-]**|可与“/fp:strict”或“/fp:precise”一起使用，但不能与“/fp:fast”一起使用    。|

有关详细信息，请参阅 [/fp（指定浮点行为）](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>优化 declspec

在本部分中，我们将介绍两个可以在程序中用于优化性能的 declspec：`__declspec(restrict)` 和 `__declspec(noalias)`。

`restrict` declspec 只能应用于返回指针的函数声明，例如 `__declspec(restrict) void *malloc(size_t size);`

`restrict` declspec 用于返回未关联指针的函数。 此关键字用于 `malloc` 的 C 运行时库实现，因为它永不会返回当前程序中已在使用的指针值（除非你正在执行非法操作，例如在释放内存后使用内存）。

`restrict` declspec 为编译器提供了执行编译器优化的更多信息。 对于编译器来说，最难确定的事情之一是哪些指针为其他指针提供别名，而使用这些信息可以极大地帮助编译器。

值得指出的是，这是对编译器的承诺，而不是编译器将验证的内容。 如果你的程序不恰当地使用了此 `restrict` declspec，则程序可能会产生错误的行为。

有关更多信息，请参阅[限制](../cpp/restrict.md)。

`noalias` declspec 也只应用于函数，并指示该函数是半纯函数。 半纯函数只引用或修改局部变量、参数和第一级间接寻址的参数。 此 declspec 是对编译器的承诺，如果函数引用全局或第二级间接寻址的指针参数，那么编译器可能生成中断应用程序的代码。

有关详细信息，请参阅 [noalias](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>优化杂注

还提供了一些有用的杂注来帮助优化代码。 我们要讨论的第一个杂注是 `#pragma optimize`：

```cpp
#pragma optimize("{opt-list}", on | off)
```

通过此杂注，你可以对每个函数设置一个给定优化级别。 对于使用优化编译给定函数时出现应用程序崩溃的罕见情况，建议使用此杂注。 可以使用此杂注关闭对单个函数的优化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

有关详细信息，请参阅 [优化](../preprocessor/optimize.md)。

内联是编译器执行的最重要的优化之一，在这里我们将讨论一些有助于修改此行为的几个杂注。

`#pragma inline_recursion` 用于指定是否希望应用程序能够内联递归调用。 默认情况下，它处于关闭状态。 对于小函数的浅表递归，可以启用此选项。 有关详细信息，请参阅 [inline_recursion](../preprocessor/inline-recursion.md)。

限制内联深度的另一个有用杂注是 `#pragma inline_depth`。 这在试图限制程序或函数大小的情况下通常很有用。 有关更多信息，请参阅 [inline_depth](../preprocessor/inline-depth.md)。

## <a name="__restrict-and-__assume"></a>__restrict 和 \__assume

Visual Studio 中有几个关键字可帮助提高性能：[__restrict](../cpp/extension-restrict.md) 和 [__assume](../intrinsics/assume.md)。

首先，应注意 `__restrict` 和 `__declspec(restrict)` 是两种不同的事物。 虽然它们有点关联，但它们的语义是不同的。 `__restrict` 是类型限定符，如 `const` 或 `volatile`，但仅限于指针类型。

使用 `__restrict` 修改的指针称为“__restrict 指针”  。 __restrict 指针只能通过 \___restrict 指针访问。 换句话说，不能使用另一个指针访问由 \__restrict 指针指向的数据。

对于 Microsoft C++ 优化器而言，`__restrict` 可能是一种强大的工具，但使用时应非常小心。 如果使用不当，优化器可能会执行优化，从而破坏应用程序。

`__restrict` 关键字替换以前版本的“/Oa”开关  。

在 `__assume` 中，开发人员可以指示编译器对某个变量的值作出假设。

例如 `__assume(a < 5);` 指示优化器，在代码的那一行，变量 `a` 小于 5。 同样，这是对编译器的承诺。 如果 `a` 在程序的这一点上实际上是 6，则编译器优化后程序的行为可能不是你所期望的那样。 `__assume` 在切换语句和/或条件表达式之前最有用。

`__assume` 存在一些限制。 首先，和 `__restrict` 一样，它只是一个建议，所以编译器可以随意忽略它。 此外，`__assume` 目前只适用于常量的变量不等式。 它并不传播不相等符号，例如，assume(a < b)。

## <a name="intrinsic-support"></a>内部支持

对于内部函数调用，由于编译器内在了解这种函数调用，因此它是从这种函数发出代码，而不是调用库中的函数。 头文件 \<intrin.h> 包含每个受支持硬件平台的所有可用内部函数。

通过内部函数，程序员无需使用程序集便可深入了解代码。 使用内部函数有以下几个好处：

- 你的代码更易移植。 可以在多种 CPU 体系结构中使用多个内部函数。

- 你的代码更易于阅读，因为代码仍然是用 C/C++ 编写的。

- 你的代码将具有编译器优化的优点。 随着编译器的改进，内部函数的代码生成也会改进。

有关详细信息，请参阅[编译器内部函数](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>异常

存在与使用异常相关联的性能问题。 使用 try 块时会引入一些限制，这些限制会阻止编译器执行某些优化。 在 x86 平台上，由于在代码执行期间必须生成其他状态信息，try 块的性能会进一步降低。 在 64 位平台上，try 块不会降低性能，但一旦引发异常，查找处理程序和展开堆栈的过程可能会很昂贵。

因此，建议避免在不需要 try/catch 块的代码中引入 try/catch 块。 如果必须使用异常，请尽可能使用同步异常。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最后，只对特殊情况引发异常。 对常规控制流使用异常可能会降低性能。

## <a name="see-also"></a>请参阅

- [优化代码](optimizing-your-code.md)
