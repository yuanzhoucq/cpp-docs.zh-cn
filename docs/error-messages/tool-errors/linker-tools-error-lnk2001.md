---
title: 链接器工具错误 LNK2001 |Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb8e560e46da06c4312ab4261016ccd5a5ddda68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017842"
---
# <a name="linker-tools-error-lnk2001"></a>链接器工具错误 LNK2001

无法解析的外部符号"*符号*"

已编译的代码可以引用或调用*符号*，但该符号并不定义中的任何库或链接器指定的对象文件。

此错误消息后跟错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 必须修复所有 LNK2001 和 LNK2019 错误，若要修复错误 LNK1120。

## <a name="possible-causes"></a>可能的原因

有许多方法来获取此错误，但所有这些涉及对函数或变量的链接器不能引用*解决*，或查找的定义。 编译器可标识时某个符号未*声明*，但不是时它不是*定义*，因为可以在不同的源代码文件或库中的定义。 如果符号引用，但永远不会定义，链接器将生成错误。

### <a name="coding-issues"></a>编码问题

此错误可能由不匹配的情况下，在你的源代码或模块定义 (.def) 文件。 例如，如果为变量命名`var1`在一个 c + + 源文件，并尝试访问其作为`VAR1`中另一个，会生成此错误。 若要解决此问题，使用一致地拼写和大小写的名称。

可以使用的项目中导致此错误[函数内联](../../error-messages/tool-errors/function-inlining-problems.md)如果源代码文件中，而不是标头文件中定义的函数。 内联的函数无法查看外部定义它们的源代码文件。 若要解决此问题，请在其中声明的标头中定义内联的函数。

如果不使用从 c + + 程序上调用 C 函数可以导致此错误`extern "C"`C 函数声明。 编译器针对 C 和 c + + 代码，使用不同的内部符号命名约定，它是当正在解析符号时，链接器查找 internal 符号名称。 若要解决此问题，请使用`extern "C"`C 函数在 c + + 代码，这会导致编译器使用这些符号 C 内部命名约定中使用的所有声明周围的包装器。 编译器选项[/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)并[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)会导致编译器文件分别编译为 c + + 或 C，而不考虑文件扩展名。 这些选项可能会导致与您期望的不同内部函数名称。

尝试引用函数或不具有外部链接的数据可以导致此错误。 在 c + + 内联函数和`const`数据具有内部链接，除非显式指定为`extern`。 若要解决此问题，请使用显式`extern`上符号的声明定义源文件外部引用。

此错误可能引起[缺少函数体或变量](../../error-messages/tool-errors/missing-function-body-or-variable.md)定义。 声明，但未定义，变量、 函数或类在代码中时，此错误很常见。 编译器只需要一个函数原型或`extern`变量声明来生成没有错误，但链接器的对象文件无法解析对函数的调用或对该变量的引用，因为没有函数代码或变量空间保留。 若要解决此问题，请确保每个引用的函数和变量完全定义中的源文件或包含在链接中的库。

使用返回值和参数类型或不匹配函数定义中的调用约定的函数调用可导致此错误。 在 c + + 对象文件中[名称修饰](../../error-messages/tool-errors/name-decoration.md)合并到最终修饰的函数名称，用作符号以匹配时调用的调用约定、 类或命名空间范围和返回类型和参数类型的函数解决其他对象文件中的函数。 若要解决此问题，请确保声明、 定义和对所有函数的调用使用相同的作用域、 类型和调用约定。

可以在 c + + 代码中导致此错误，当您在类定义中包括函数原型，但故障到[包括实施](../../error-messages/tool-errors/missing-function-body-or-variable.md)的函数，然后调用它。 若要解决此问题，请确保提供所有名为声明类的成员的定义。

尝试从一个抽象基类调用纯虚函数可以导致此错误。 纯虚函数具有任何基类实现。 若要解决此问题，请确保所有调用虚函数实现。

此错误可能由尝试使用函数内声明的变量 ([局部变量](../../error-messages/tool-errors/automatic-function-scope-variables.md)) 该函数的作用域之外。 若要解决此问题，删除对不在范围内，该变量的引用，或将变量移到更高的作用域。

生成 ATL 项目的发布版本生成 CRT 启动代码是必需的消息时，会出现此错误。 若要解决此问题，请执行下列操作之一

- 删除`_ATL_MIN_CRT`从列表中的预处理器定义允许 CRT 启动代码将包括在内。 请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)有关详细信息。

- 如果可能，删除对需要 CRT 启动代码的 CRT 函数的调用。 相反，使用它们的 Win32 等效项。 例如，使用 `lstrcmp` 而不是 `strcmp`。 需要 CRT 启动代码的已知的功能是一些字符串和浮点函数。

### <a name="compilation-and-link-issues"></a>编译和链接问题

当项目缺少对库的引用时，会出现此错误 (。LIB) 或对象 (。OBJ) 文件。 若要解决此问题，请到您的项目添加到所需的库或对象文件的引用。 有关详细信息，请参阅[用作链接器输入的.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。

如果您使用可能发生此错误[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)或[/Zl](../../build/reference/zl-omit-default-library-name.md)选项。 当指定这些选项时，包含所需的代码的库除非显式包含了它们并未链接到项目。 若要解决此问题，请显式包括链接命令行使用的所有库。 如果您看到许多缺少 CRT 或标准库函数名称时使用这些选项，显式包括 CRT 和标准库 Dll 或库文件的链接中。

如果使用编译 **/clr**选项，可以对.cctor 缺少引用。 若要解决此问题，请参阅[混合程序集初始化](../../dotnet/initialization-of-mixed-assemblies.md)有关详细信息。

如果时生成的应用程序的调试版本链接到发布模式库，可以发生此错误。 同样，如果使用选项 **/MTd**或 **/MDd**或定义`_DEBUG`，然后链接到发布库，您将会发现很多潜在无法解析的外部，在其他问题。 链接发布模式生成的调试库还会导致类似问题。 若要解决此问题，请确保在您的调试版本中使用调试库，并在 retail 零售库生成。

如果你的代码引用符号从一个版本的库，但提供给链接器库的不同版本，可以发生此错误。 通常情况下，不能混合对象文件或为不同版本的编译器生成的库。 新版本中随附的库可能包含不能在早期版本中，以及进行相反转换中包含的库中找到的符号。 若要解决此问题，请将它们链接在一起之前生成的所有对象文件和库使用相同版本的编译器。

-  工具&#124;选项&#124;项目&#124;VC + + 目录对话框中，在库文件的所选内容，可以更改库搜索顺序。 在项目属性页对话框中的链接器文件夹也可能包含可能是过期的路径。

-  新的 SDK 安装 （可能是到其他位置） 和搜索顺序不会更新以指向新位置时，可能会出现此问题。 通常情况下，应将路径放到新的 SDK include 和 lib 目录默认 Visual c + + 位置的前面。 此外，包含嵌入的路径的项目可能仍然指向旧路径有效，但已过期的情况下安装到其他位置的新版本添加的新功能。

- 如果您在命令行生成并创建了自己的环境变量，请验证工具、 库和标头文件的路径转到一致的版本。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

目前没有标准[c + + 命名](../../error-messages/tool-errors/name-decoration.md)编译器供应商之间、 甚至之间不同版本的编译器。 因此，链接用其他编译器编译对象文件可能不生成相同的命名方案，并因此导致错误 LNK2001。

[混合内联和非内联编译选项](../../error-messages/tool-errors/function-inlining-problems.md)上不同的模块会导致 LNK2001。 如果使用函数内联开启创建 c + + 库 (**/ob1**或 **/ob2**) 描述函数的相应标头文件具有内联处于关闭状态，但 (没有`inline`关键字)，此错误会发生。 若要解决此问题，定义的函数`inline`在其他源文件中包含的标头文件中。

如果您使用`#pragma inline_depth`编译器指令，请确保你已[设置了 2 个或更高版本的值](../../error-messages/tool-errors/function-inlining-problems.md)，并确保也使用[/ob1](../../build/reference/ob-inline-function-expansion.md)或[/ob2](../../build/reference/ob-inline-function-expansion.md)编译器选项。

如果省略该链接可能出现此错误选项 /NOENTRY 时创建纯资源 DLL。 若要解决此问题，请添加到链接命令 /NOENTRY 选项。

如果在项目中使用不正确 /SUBSYSTEM 或 /ENTRY 设置，可以发生此错误。 例如，如果你编写的控制台应用程序，并指定 /subsystem: windows，则无法解析的外部错误生成的`WinMain`。 若要解决此问题，请确保匹配到项目类型的选项。 有关这些选项和入口点的详细信息，请参阅[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)并[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。

### <a name="exported-symbol-issues"></a>导出的符号问题

找不到.def 文件中列出的导出时，将发生此错误。 这可能是因为它不存在、 拼写错误，或使用 c + + 修饰名称。 .Def 文件才会修饰的名。 若要解决此问题，请删除不需要的导出，并使用`extern "C"`导出符号的声明。

## <a name="what-is-an-unresolved-external-symbol"></a>无法解析的外部符号是什么？

一个*符号*是函数或由已编译的对象文件或库在内部使用的全局变量的名称。 符号是由*定义*对象文件中的全局变量，或对于函数，其中分配存储放置在函数体的已编译的代码的位置。 *的外部符号*是一个符号的*引用*，即，使用或调用在一个对象文件中，但在不同的库或对象文件中定义。 *导出符号*是一种进行公开的对象文件或将其定义的库。 链接器必须*解决*，或找到的匹配定义，每个引用的对象文件时将其链接到应用程序或 DLL 的外部符号。 链接器将生成错误时它不能通过任何链接的文件中查找匹配的导出的符号解析的外部符号。

## <a name="use-the-decorated-name-to-find-the-error"></a>使用修饰的名以找出错误

C + + 编译器和链接器使用[名称修饰](../../error-messages/tool-errors/name-decoration.md)，也称为*名称重整*、 有关变量的类型或返回类型、 参数类型、 作用域，以及调用的额外信息进行编码中的符号名称的函数的约定。 此修饰的名是链接器搜索用于解析外部符号的符号名称。

由于的额外信息变得符号名称的一部分，如果函数或变量的声明不完全匹配的函数或变量的定义会导致链接错误。 这可能是即使相同的标头文件用于调用的代码和定义代码，如果编译的源文件时使用不同的编译器标志。 例如，如果你的代码编译为使用收到此错误`__vectorcall`调用约定，但您链接到要求客户端调用使用默认的库`__cdecl`或`__fastcall`调用约定。 在这种情况下，符号不匹配，因为不同的调用约定

为了帮助你找出这种错误的原因，链接器错误消息显示这两个"友好名称，"源代码和未解析的外部符号的修饰的名称 （在括号内） 中使用的名称。 不需要知道如何将转换为修饰的名，以便能够将其与其他修饰名称进行比较。 可以使用命令行工具附带编译器要比较的预期的符号名称和实际的符号名称：

- [/Exports](../../build/reference/dash-exports.md)并[/ 符号](../../build/reference/symbols.md)选项的 DUMPBIN 命令行工具可帮助你发现.dll 和对象或库文件中定义了哪些符号。 可以使用此验证导出的修饰名称的修饰名称链接器搜索的匹配项。

在某些情况下，链接器仅可以报告符号的修饰的名称。 UNDNAME 命令行工具可用于获取修饰名的未修饰的形式。

## <a name="additional-resources"></a>其他资源

LNK2001 可能的原因和解决方案的详细信息，请参阅堆栈溢出问题[什么是未定义引用/未解析的外部符号错误以及如何修复此错误？](http://stackoverflow.com/q/12573816/2002113)。

