---
title: 互操作的性能注意事项 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: c6b4456d9c75061c9a8c93f37f98b58f92adc899
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384746"
---
# <a name="performance-considerations-for-interop-c"></a>互操作的性能注意事项 (C++)

本主题提供有关减少托管/非托管互操作转换对运行时性能的影响的指南。

VisualC++支持相同的互操作性机制作为其他.NET 语言，如 Visual Basic 和C#(P/Invoke)，但它还提供互操作支持特定于视觉对象的C++(C++互操作)。 对于性能关键型应用程序，务必了解每个互操作技术的性能影响。

无论使用的互操作技术，特殊的转换序列，称为形式转换，都是所需每次托管的函数调用非托管的函数，反之亦然。 通过视觉对象自动插入这些 thunkC++编译器，但它是务必记住，累积，这些转换可能会消耗大量的性能。

## <a name="reducing-transitions"></a>减少转换

若要避免或减少的互操作的 thunk 的成本的一种方法是重构最大程度减少托管/非托管转换所涉及的接口。 可以通过定向聊天式界面，是指那些涉及频繁调用跨托管/非托管边界进行大大改进了性能。 在紧密循环中，调用非托管的函数的托管的函数，如重构是的良好候选项。 如果循环本身移动到未托管一侧，或者如果托管替代方法创建非托管的调用 （也许是在托管端的队列数据，然后封送到非托管 API 次循环后），可以是转换的次数减少登录ificantly。

## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs。C++ 互操作

对于.NET 语言，如 Visual Basic 和 C# 中，与本机组件进行互操作的规定的方法是 P/Invoke。 由于 P/Invoke 支持.NET Framework 中，视觉对象的C++支持它，但视觉对象C++还提供了其自己的互操作性的支持，这被称为C++互操作。 C++互操作通过 P/Invoke 中都是首选的因为 P/Invoke 不是类型安全。 因此，错误主要报告在运行时，但C++互操作还具有通过 P/Invoke 的性能优势。

这两种技术要求每当托管的函数调用非托管的函数的几个功能：

- 函数调用自变量是从 CLR 封送到本机类型。

- 执行托管到非托管的转换 （thunk）。

- 非托管的函数调用 （使用本机版本的自变量）。

- 执行非托管到托管的转换 （thunk）。

- 返回类型和任何"out"或"中，out"参数从 CLR 类型的本机代码封送。

托管/非托管形式转换所需的互操作正常工作所，但所需的数据封送处理取决于所涉及的数据类型、 函数签名，以及如何使用数据。

由执行数据封送处理C++互操作是最简单的可能形式： 跨托管/非托管边界按位的方式; 只需复制参数在所有不执行任何转换。 有关 P/Invoke，这是仅当所有参数都是简单的则为 true 可直接复制类型。 否则，P/Invoke 执行非常可靠的步骤，以便将每个托管的参数转换为相应的本机类型，反之亦然如果参数标记为"out"或"中，out"。

换而言之，C++互操作使用的封送处理数据，最快的可能的方法，而 P/Invoke 使用的最可靠方法。 这意味着，C++互操作 (在典型的方式C++) 提供了默认情况下，获得最佳性能和程序员负责解决此行为不安全或不适宜的情况。

C++因此 interop 要求必须显式提供数据封送处理，但好处是编程人员可以自由地决定哪种情况适宜，给定的数据的性质以及它的方式使用。 此外，尽管的 P/Invoke 数据封送处理行为可以修改在自定义在某种程度上，C++互操作允许数据封送处理在调用由调用的基础上进行自定义。 这是不可能使用 P/Invoke。

有关详细信息C++互操作性，请参阅[UsingC++互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="see-also"></a>请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
