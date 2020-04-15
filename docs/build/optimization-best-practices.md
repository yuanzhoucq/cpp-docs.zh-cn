---
title: 优化最佳做法
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328443"
---
# <a name="optimization-best-practices"></a>优化最佳做法

本文档介绍了在 Visual Studio 中优化C++程序的一些最佳实践。

## <a name="compiler-and-linker-options"></a>编译器和链接器选项

### <a name="profile-guided-optimization"></a>配置文件导向优化

可视化工作室支持*配置文件导向优化*（PGO）。 此优化使用应用程序检测版本的训练执行中的配置文件数据来驱动应用程序以后的优化。 使用 PGO 可能非常耗时，因此可能不是每个开发人员都使用的内容，但我们确实建议在产品的最终版本生成中使用 PGO。 有关详细信息，请参阅[按配置优化](profile-guided-optimizations.md)。

此外，*整个程序优化*（也称为链接时间代码生成）和 **/O1**和 **/O2**优化也得到了改进。 通常，使用这些选项之一编译的应用程序将比使用早期编译器编译的同一应用程序更快。

有关详细信息，请参阅[/GL（整个程序优化）](reference/gl-whole-program-optimization.md)和[/O1、/O2（最小化大小、最大化速度）](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>要使用的优化级别

如果可能，最终版本版本应使用配置文件引导优化进行编译。 如果无法使用 PGO 进行构建，无论是由于运行检测生成的基础结构不足，还是无法访问方案，我们建议使用整个程序优化进行构建。

**/Gy**开关也非常有用。 它为每个函数生成单独的 COMDAT，在删除未引用的 COMDAT 和 COMDAT 折叠时，链路器具有更大的灵活性。 使用 **/Gy**的唯一缺点是，在调试时可能会导致问题。 因此，通常建议使用它。 有关详细信息，请参阅 [/Gy （启用函数级链接）](reference/gy-enable-function-level-linking.md)。

对于在 64 位环境中的链接，建议使用 **/OPT：REF、ICF**链接器选项，并在 32 位环境中建议**使用 /OPT：REF。** 有关详细信息，请参阅[/OPT （优化）](reference/opt-optimizations.md)。

强烈建议生成调试符号，即使使用优化的发布版本也是如此。 它不会影响生成的代码，如果需要，它使调试应用程序变得更加容易。

### <a name="floating-point-switches"></a>浮点开关

已删除 **/Op**编译器选项，并添加了以下四个处理浮点优化的编译器选项：

|||
|-|-|
|**/fp：精确**|这是默认建议，在大多数情况下应使用。|
|**/fp：快速**|如果性能是最重要的，例如在游戏中，则建议使用。 这将导致最快的性能。|
|**/fp：严格**|如果需要精确的浮点异常和 IEEE 行为，则建议这样做。 这将导致性能最慢。|
|**/fp：除*-***|可与 **/fp：严格**或 **/fp：精确**，但不能与 **/fp：fast**结合使用。|

有关更多信息，请参见 [/fp (Specify Floating-Point Behavior)](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>优化分点

在本节中，我们将介绍两个可用于程序以帮助性能的分项：`__declspec(restrict)`和`__declspec(noalias)`。

`restrict`声明只能应用于返回指针的函数声明，例如`__declspec(restrict) void *malloc(size_t size);`

delspec`restrict`用于返回未别名指针的函数。 此关键字用于 C-Runtime 库的实现，`malloc`因为它永远不会返回当前程序中已在使用的指针值（除非您正在执行非法的事情，例如在释放内存后使用内存）。

delspec`restrict`为编译器提供了用于执行编译器优化的详细信息。 编译器最难确定的事情之一是哪些指针别名其他指针，使用此信息对编译器有很大帮助。

值得指出的是，这是编译器的承诺，而不是编译器将验证的内容。 如果程序不适当地使用此`restrict`declspec，则程序可能有不正确的行为。

有关详细信息，请参阅[限制](../cpp/restrict.md)。

`noalias` delspec 也仅适用于函数，并指示函数是半纯函数。 半纯函数是仅引用或修改局部变量、参数和参数的第一级方向函数。 此 delspec 是编译器的承诺，如果函数引用全局或指针参数的二级方向，则编译器可能会生成破坏应用程序的代码。

有关详细信息，请参阅 [noalias](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>优化杂注

还有一些有用的实用主义者来帮助优化代码。 我们将讨论的第一个是`#pragma optimize`：

```cpp
#pragma optimize("{opt-list}", on | off)
```

此杂注允许您在函数的基础上设置给定的优化级别。 这是应用程序在编译给定函数时通过优化编译时崩溃的罕见场合的理想选择。 您可以使用它关闭单个函数的优化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

有关详细信息，请参阅[优化](../preprocessor/optimize.md)。

内联是编译器执行的最重要优化之一，在这里，我们讨论几个有助于修改此行为的杂注。

`#pragma inline_recursion`用于指定是否希望应用程序能够内联递归调用。 默认情况下，它处于关闭状态。 对于小函数的浅递归，您可以打开此功能。 有关详细信息，请参阅[inline_recursion](../preprocessor/inline-recursion.md)。

另一个有用的杂注，以限制内联的深度是`#pragma inline_depth`。 这在尝试限制程序或函数大小的情况下通常很有用。 有关详细信息，请参阅[inline_depth](../preprocessor/inline-depth.md)。

## <a name="__restrict-and-__assume"></a>__restrict和\__assume

Visual Studio 中有几个关键字可以帮助性能[：__restrict](../cpp/extension-restrict.md)和[__assume。](../intrinsics/assume.md)

首先，应该指出，`__restrict`这是`__declspec(restrict)`两码事。 虽然它们有些相关，但它们的语义是不同的。 `__restrict`是类型限定符，如`const``volatile`或 ，但仅限于指针类型。

修改的`__restrict`指针称为 *__restrict指针*。 __restrict指针是只能通过\__restrict指针访问的指针。 换句话说，另一个指针不能用于访问\__restrict指针指向的数据。

`__restrict`对于 Microsoft C++优化器来说，它可以是一个强大的工具，但使用时要非常小心。 如果使用不当，优化器可能会执行一个优化，这将破坏您的应用程序。

关键字`__restrict`将替换以前版本的 **/Oa**开关。

使用`__assume`，开发人员可以告诉编译器对某个变量的值做出假设。

例如`__assume(a < 5);`，告诉优化器，在代码行中，变量`a`小于 5。 这也是对编译器的承诺。 如果`a`程序此时实际为 6，则编译器优化后程序的行为可能不是您所期望的。 `__assume`在切换语句和/或条件表达式之前最有用。

对 有一些`__assume`限制。 首先，就像`__restrict`，它只是一个建议，所以编译器可以自由地忽略它。 此外，`__assume`目前仅适用于针对常量的可变不等式。 它不传播符号不等式，例如，假设（a<b）。

## <a name="intrinsic-support"></a>内在支持

内部函数是函数调用，其中编译器对调用有内在知识，而不是在库中调用函数，而是为该函数发出代码。 标头文件\<intrin.h>包含每个受支持的硬件平台的所有可用内部函数。

内部函数使程序员能够深入代码，而无需使用程序集。 使用内在功能有几个好处：

- 您的代码更加便携。 多个内部函数可用于多个 CPU 体系结构。

- 代码更易于阅读，因为代码仍以 C/C++编写。

- 您的代码受益于编译器优化。 随着编译器的更好，内部函数的代码生成也会得到改善。

有关详细信息，请参阅[编译器内部函数](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>例外

使用异常会受到性能影响。 使用禁止编译器执行某些优化的 try 块时，会引入一些限制。 在 x86 平台上，由于在代码执行期间必须生成的其他状态信息，try 块的性能会进一步下降。 在 64 位平台上，try 块不会降低性能，但一旦引发异常，查找处理程序和展开堆栈的过程可能非常昂贵。

因此，建议避免在并不真正需要的代码中引入 try/catch 块。 如果必须使用异常，请使用同步异常（如果可能）。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最后，仅针对例外情况引发异常。 对常规控制流使用异常可能会使性能受到影响。

## <a name="see-also"></a>另请参阅

- [优化代码](optimizing-your-code.md)
