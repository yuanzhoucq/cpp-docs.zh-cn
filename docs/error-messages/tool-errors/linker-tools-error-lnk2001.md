---
title: 链接器工具错误 LNK2001
ms.date: 12/19/2019
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: b6d1e53d8f057ddc93e2dfde65cb951d247dfcc0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302128"
---
# <a name="linker-tools-error-lnk2001"></a>链接器工具错误 LNK2001

> 无法解析的外部符号 "*symbol*"

已编译的代码对*符号*进行引用或调用。 链接器搜索的任何库或对象文件中未定义该符号。

此错误消息后跟严重错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 若要修复错误 LNK1120，请先修复所有 LNK2001 和 LNK2019 错误。

有多种方法可获取 LNK2001 错误。 所有这些方法都涉及到对链接器无法*解析*的函数或变量的*引用*，或者查找的定义。 当你的代码未*声明*符号，而未*定义*符号时，编译器可以确定它。 这是因为定义可能位于不同的源文件或库中。 如果代码引用符号，但从未定义过，则链接器将生成错误。

## <a name="what-is-an-unresolved-external-symbol"></a>什么是无法解析的外部符号？

*符号*是函数或全局变量的内部名称。 它是在已编译的对象文件或库中使用或定义的名称的形式。 全局变量是在为其分配存储的对象文件中定义的。 函数在对象文件中定义，该对象文件中放置了函数体的已编译代码。 *外部符号*在一个对象文件中引用，但在不同的库或对象文件中定义。 *导出的符号*是指由定义它的对象文件或库公开提供的符号。

若要创建应用程序或 DLL，每个使用的符号必须具有定义。 链接器必须*解析*或查找每个对象文件引用的每个外部符号的匹配定义。 如果链接器无法解析外部符号，则会生成错误。 这意味着链接器无法在任何链接的文件中找到匹配的已导出符号定义。

## <a name="compilation-and-link-issues"></a>编译和链接问题

发生此错误的原因可能是：

- 如果项目缺少对库的引用（。LIB）或对象（。OBJ）文件。 若要解决此问题，请在项目中添加对所需库或对象文件的引用。 有关详细信息，请参阅[Lib 文件作为链接器输入](../../build/reference/dot-lib-files-as-linker-input.md)。

- 如果项目具有对库的引用（。LIB）或对象（。OBJ）文件，而该文件又需要另一个库中的符号。 即使您不调用导致依赖关系的函数，也可能会发生这种情况。 若要解决此问题，请向项目添加对另一个库的引用。 有关详细信息，请参阅[了解用于链接的传统模型：获取用于进行操作的符号](https://devblogs.microsoft.com/oldnewthing/20130108-00/?p=5623)。

- 如果使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)或[/zl](../../build/reference/zl-omit-default-library-name.md)选项。 当你指定这些选项时，包含所需代码的库不会链接到项目中，除非你显式包含它们。 若要解决此问题，请显式包含在链接命令行上使用的所有库。 如果在使用这些选项时发现许多缺少 CRT 或标准库函数名称，请在链接中显式包含 CRT 和标准库 Dll 或库文件。

- 如果使用 **/clr**选项编译，则为。 可能缺少对 `.cctor`的引用。 有关如何解决此问题的详细信息，请参阅[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。

- 如果在生成应用程序的调试版本时链接到发布模式库。 同样，如果使用选项 **/MTd**或 **/MDd**或定义 `_DEBUG` 然后链接到发布库，则可能会预计许多潜在的无法解析的外部函数，还有其他问题。 将发布模式版本与调试库链接还会导致类似的问题。 若要解决此问题，请确保在调试版本中使用调试库，并在零售版本中使用零售库。

- 如果你的代码引用一个库版本中的符号，但你链接的是不同版本的库。 通常，不能混合为不同版本的编译器生成的对象文件或库。 在一个版本中随附的库可能包含在其他版本随附的库中找不到的符号。 若要解决此问题，请在将对象文件和库与编译器的版本结合在一起之前生成它们。 有关详细信息，请参阅[ C++二进制兼容性 2015-2019](../../porting/binary-compat-2015-2017.md)。

- 如果库路径过期，则为。 "**工具" > > 选项 "> VC + + 目录**" 对话框中的 "**库文件**" 对话框下，可以更改库的搜索顺序。 项目的 "属性页" 对话框中的 "链接器" 文件夹可能还包含可能已过期的路径。

- 当安装新的 Windows SDK 时（可能位于其他位置）。 必须更新库搜索顺序才能指向新位置。 通常情况下，应将新的 SDK 包含的路径和 lib 目录放在默认的视觉C++位置之前。 此外，包含嵌入路径的项目仍可指向有效但过期的旧路径。 更新安装到不同位置的新版本添加的新功能的路径。

- 如果在命令行中生成，并创建了自己的环境变量。 验证工具、库和头文件的路径是否为一致的版本。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

## <a name="coding-issues"></a>编码问题

此错误可由以下原因引起：

- 源代码或模块定义（.def）文件中的大小写不匹配。 例如，如果将一个变量命名 `var1` 在一个C++源文件中，然后尝试将其作为 `VAR1` 在另一个源文件中进行访问，则会生成此错误。 若要解决此问题，请使用一致拼写和大小写的名称。

- 使用[函数内联](../../error-messages/tool-errors/function-inlining-problems.md)的项目。 当您在源文件中将函数定义为 `inline`，而不是在头文件中定义时，可能会发生这种情况。 内联函数在定义它们的源文件之外无法查看。 若要解决此问题，请在声明它们的标头中定义内联函数。

- 从C++程序调用 c 函数，而不使用 C 函数的 `extern "C"` 声明。 编译器对 C 和C++代码使用不同的内部符号命名约定。 内部符号名称是链接器在解析符号时所查找的内容。 若要解决此问题，请在C++代码中使用的所有 C 函数声明中使用 `extern "C"` 包装，这将导致编译器对这些符号使用 c 内部命名约定。 编译器选项[/tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)和[/tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)导致编译器分别将文件编译为C++或 C，无论文件扩展名是什么。 这些选项可能会导致内部函数名称与预期的名称不同。

- 尝试引用不具有外部链接的函数或数据。 在C++中，内联函数和 `const` 数据具有内部链接，除非显式指定为 `extern`。 若要解决此问题，请在定义源文件之外的符号上使用显式 `extern` 声明。

- [缺少函数体或变量](../../error-messages/tool-errors/missing-function-body-or-variable.md)定义。 当你在代码中声明但不定义、变量、函数或类时，此错误很常见。 编译器只需要一个函数原型或 `extern` 变量声明来生成对象文件，而不会出错，但链接器无法解析对该函数的调用或对该变量的引用，因为没有保留函数代码或变量空间。 若要解决此问题，请确保在所链接的源文件或库中定义每个引用的函数和变量。

- 使用返回类型和参数类型的函数调用，或调用不与函数定义中的类型匹配的约定。 在C++对象文件中，[名称修饰](../../error-messages/tool-errors/name-decoration.md)对调用约定、类或命名空间范围进行编码，并对函数的返回类型和参数类型进行编码。 编码的字符串将成为最终修饰函数名称的一部分。 链接器使用此名称来解析或匹配其他对象文件中对函数的调用。 若要解决此问题，请确保函数声明、定义和调用都使用相同的作用域、类型和调用约定。

- C++当你在类定义中包括函数原型，但不[包括函数的实现](../../error-messages/tool-errors/missing-function-body-or-variable.md)时，调用的代码。 若要解决此问题，请确保为调用的所有类成员提供定义。

- 尝试从抽象基类调用纯虚函数。 纯虚函数没有基类实现。 若要解决此问题，请确保已实现所有调用的虚拟函数。

- 尝试使用函数内声明的变量（[局部变量](../../error-messages/tool-errors/automatic-function-scope-variables.md)）在该函数的范围之外。 若要解决此问题，请删除对不在作用域中的变量的引用，或将变量移动到更高的作用域。

- 生成 ATL 项目的发行版时，会生成一条消息，要求 CRT 启动代码是必需的。 若要解决此问题，请执行以下操作之一：

  - 从预处理器定义的列表中删除 `_ATL_MIN_CRT`，以允许包含 CRT 启动代码。 有关详细信息，请参阅 "[常规" 属性页（项目）](../../build/reference/general-property-page-project.md)。

  - 如果可能，请删除对需要 CRT 启动代码的 CRT 函数的调用。 请改用其 Win32 等效项。 例如，请使用 `lstrcmp` 而不是 `strcmp`。 需要 CRT 启动代码的已知函数是字符串和浮点函数的一部分。

## <a name="consistency-issues"></a>一致性问题

在编译器供应商之间，甚至在同一编译器的不同版本之间没有[ C++名称修饰](../../error-messages/tool-errors/name-decoration.md)的标准。 使用不同编译器编译的对象文件不能使用相同的命名方案。 链接它们可能会导致错误 LNK2001。

混合不同模块上的[内联和非内联编译选项](../../error-messages/tool-errors/function-inlining-problems.md)可能会导致 LNK2001。 如果创建C++库时启用了函数内联（ **/Ob1**或 **/Ob2**），但描述函数的相应标头文件启用了内联（无 `inline` 关键字），则会发生此错误。 若要解决此问题，请在包含在其他源文件中的标头文件中定义函数 `inline`。

如果使用 `#pragma inline_depth` 编译器指令，请确保将[值设置为2或更大](../../error-messages/tool-errors/function-inlining-problems.md)，并确保还使用[/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)编译器选项。

如果在创建纯资源 DLL 时省略了 LINK 选项/NOENTRY，则会出现此错误。 若要解决此问题，请将/NOENTRY 选项添加到 link 命令。

如果在项目中使用不正确的/SUBSYSTEM 或/ENTRY 设置，则会发生此错误。 例如，如果编写一个控制台应用程序并指定/SUBSYSTEM： WINDOWS，则会为 `WinMain`生成一个无法解析的外部错误。 若要解决此问题，请确保将选项与项目类型匹配。 有关这些选项和入口点的详细信息，请参阅[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)和[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。

## <a name="exported-def-file-symbol-issues"></a>导出的 .def 文件符号问题

当找不到 .def 文件中列出的导出时，将出现此错误。 这可能是因为导出不存在、拼写错误或使用C++修饰名。 .Def 文件不采用修饰名。 若要解决此问题，请删除不需要的导出，并对导出的符号使用 `extern "C"` 声明。

## <a name="use-the-decorated-name-to-find-the-error"></a>使用修饰名查找错误

C++编译器和链接器使用[名称修饰](../../error-messages/tool-errors/name-decoration.md)（也称为*名称重整*）。 名称修饰对其符号名称中的变量类型的额外信息进行编码。 函数的符号名称对其返回类型、参数类型、作用域和调用约定进行编码。 此修饰名是链接器搜索以解析外部符号的符号名称。

如果函数或变量的声明与函数或变量的定义不*完全*匹配，则可能会导致链接错误。 这是因为任何差异都会成为要匹配的符号名称的一部分。 即使在调用代码和定义代码中使用相同的头文件，也可能发生此错误。 出现这种情况的一种方法是使用不同的编译器标志来编译源文件。 例如，如果你的代码编译为使用 `__vectorcall` 调用约定，但你链接到的库要求客户端使用默认 `__cdecl` 或 `__fastcall` 调用约定来调用它。 在这种情况下，由于调用约定不同，因此符号不匹配。

为了帮助你找到原因，错误消息会显示两个名称版本。 它既显示 "友好名称"、"在源代码中使用的名称"，也显示修饰名称（在括号中）。 不需要知道如何解释修饰名。 你仍可以搜索并将其与其他修饰名称进行比较。 命令行工具可帮助查找和比较预期符号名称和实际符号名称：

- 此处的 DUMPBIN 命令行工具的[/EXPORTS](../../build/reference/dash-exports.md)和[/SYMBOLS](../../build/reference/symbols.md)选项非常有用。 它们可帮助你发现 .dll 和对象或库文件中定义了哪些符号。 您可以使用符号列表来验证导出的修饰名称是否匹配链接器搜索的修饰名称。

- 在某些情况下，链接器只能报告符号的修饰名。 可以使用 UNDNAME 命令行工具来获取修饰名的未修饰形式。

## <a name="additional-resources"></a>其他资源

有关详细信息，请参阅 Stack Overflow 问题["什么是未定义的引用/未解析的外部符号错误以及如何修复此错误？"](https://stackoverflow.com/q/12573816/2002113)。
