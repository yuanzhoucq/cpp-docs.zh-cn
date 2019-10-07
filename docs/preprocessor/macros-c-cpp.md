---
title: 宏 (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: ba2c0f012974a528876219d00c61c0f31a6cd820
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218857"
---
# <a name="macros-cc"></a>宏 (C/C++)

预处理器扩展了除*预处理器指令*之外的所有行中的宏 **#** , 并扩展了具有作为第一个非空白字符的行。 它将宏展开为某些指令的部分, 这些指令不会作为条件编译的一部分被跳过。 *条件编译指令*允许您禁止编译源文件的部分。 它们测试常量表达式或标识符, 以确定要传递给编译器的文本块, 以及在预处理期间要从源文件中删除哪些文本块。

`#define` 指令通常用于将有用标识符与常量、关键字和常用语句或表达式关联。 表示常量的标识符有时称为*符号常量*或*清单常量*。 表示语句或表达式的标识符称为 "*宏*"。 在该预处理器文档中，仅使用术语“宏”。

在程序源文本或某些其他预处理器命令的参数中识别宏的名称时, 将被视为对该宏的调用。 宏名称将替换为宏主体的副本。 如果宏接受自变量，则宏名称后面的实际自变量将替换为宏主体内的形式参数。 将宏调用替换为所处理的正文的副本的过程称为 "*扩展*" 宏调用。

实际上，有两种类型的宏。 *类似对象的*宏不采用任何参数。 可以将*类似于函数的*宏定义为接受参数, 使其外观和行为类似于函数调用。 由于宏不生成实际的函数调用, 因此您有时可以通过将函数调用替换为宏来使程序运行得更快。 （在 C++ 中，内联函数通常是首选方法。）但是, 如果您不小心定义和使用宏, 宏可能会产生问题。 必须在带有自变量的宏定义中使用括号，以便在表达式中保持适当的优先级。 此外，宏无法正确处理具有副作用的表达式。 有关详细信息, 请参阅`getrandom` [#define 指令](../preprocessor/hash-define-directive-c-cpp.md)中的示例。

一旦定义了宏, 就无法将其重新定义为不同的值, 而无需先删除原始定义。 但是，您可以使用完全相同的定义来重定义宏。 因此, 同一定义可能在程序中出现多次。

`#undef`指令删除宏的定义。 删除定义后, 可以将宏重新定义为其他值。 [#Define 指令](../preprocessor/hash-define-directive-c-cpp.md)和[#undef 指令](../preprocessor/hash-undef-directive-c-cpp.md)分别讨论`#define`和`#undef`指令。

有关详细信息，请参阅

- [宏和 C++](../preprocessor/macros-and-cpp.md)

- [Variadic 宏](../preprocessor/variadic-macros.md)

- [预定义宏](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>请参阅

[C/C++预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)
