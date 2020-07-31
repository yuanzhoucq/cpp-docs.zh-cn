---
title: 链接器工具错误 LNK2019
description: 有关 Microsoft Visual Studio 链接器错误 LNK2019 的全部信息，以及如何在 C 和 c + + 代码中诊断和更正此问题。
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(WinMain):::'
- ':::no-loc(wmain):::'
- ':::no-loc(wWinMain):::'
- ':::no-loc(__cdecl):::'
- ':::no-loc(__stdcall):::'
- ':::no-loc(__fastcall):::'
- ':::no-loc(__vectorcall):::'
- ':::no-loc(extern):::'
- ':::no-loc(static):::'
- ':::no-loc(const):::'
- ':::no-loc(ARCH):::'
- ':::no-loc(AVX2):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(VERBOSE):::'
- ':::no-loc(EXPORTS):::'
- ':::no-loc(SYMBOLS):::'
- ':::no-loc(DUMPBIN):::'
- ':::no-loc(UNDNAME):::'
ms.openlocfilehash: b83ed3663e6b199e0f3384f6d30cb1c87c0e52c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219802"
---
# <a name="linker-tools-error-lnk2019"></a>链接器工具错误 LNK2019

> :::no-loc(extern):::函数 "*function*" 中引用了未解析的 al 符号 "*symbol*"

已编译的*函数的函数*对*符号*进行引用或调用，但是链接器在要链接的任何库或对象文件中都找不到符号定义。

此错误消息后跟严重错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 若要修复错误 LNK1120，必须先修复所有 LNK2001 和 LNK2019 错误。

## <a name="possible-causes"></a>可能的原因

有多种方法可获取此错误。 所有这些都涉及到链接器无法*解析*的函数或变量的引用，或查找的定义。 编译器可以确定符号未*声明*的时间，但无法判断符号未*定义*的时间。 这是因为定义可能位于不同的源文件或库中。 如果某个符号被引用但从未定义，则链接器将生成一个无法解析的 :::no-loc(extern)::: al 符号错误。

以下是一些导致 LNK2019 的常见问题：

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>不编译包含符号定义的源文件

在 Visual Studio 中，请确保定义符号的源文件编译为项目的一部分。 查看中间生成输出目录中是否有匹配的 .obj 文件。 如果未编译源文件，请在解决方案资源管理器中右键单击该文件，然后选择 "**属性**" 以检查该文件的属性。 "**配置属性**" "  >  **常规**" 页应显示**C/c + + 编译器**的**项类型**。 在命令行上，确保编译了包含定义的源文件。

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>未链接包含符号定义的对象文件或库

在 Visual Studio 中，请确保包含符号定义的对象文件或库链接为项目的一部分。 在命令行上，确保要链接的文件列表包含对象文件或库。

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>符号声明的拼写与符号的定义不同

验证在声明和定义中以及使用或调用该符号的任何位置都使用正确的拼写和大小写。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>使用了函数，但是参数的类型或数量与函数定义不匹配

函数声明必须匹配定义。 请确保函数调用与声明匹配，并且声明与定义匹配。 调用模板函数的代码还必须拥有包括与定义相同的模板参数的匹配模板函数声明。 有关模板声明不匹配的示例，请参阅示例部分中的示例 LNK2019e。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>已声明但未定义函数或变量

当标头文件中存在声明，但未实现匹配定义时，可能会出现 LNK2019。 对于成员函数或 :::no-loc(static)::: 数据成员，实现必须包括类范围选择器。 有关示例，请参见 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>函数声明和函数定义之间的调用约定不同

调用约定（ [:::no-loc(__cdecl):::](../../cpp/cdecl.md) 、 [:::no-loc(__stdcall):::](../../cpp/stdcall.md) 、 [:::no-loc(__fastcall):::](../../cpp/fastcall.md) 或 [:::no-loc(__vectorcall):::](../../cpp/vectorcall.md) ）作为修饰名称的一部分进行编码。 请确保调用约定是相同的。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>符号在 C 文件中定义，但未 :::no-loc(extern)::: 在 c + + 文件中使用 "C" 进行声明

在编译为 c 的文件中定义的符号具有与 c + + 文件中声明的符号不同的修饰名称，除非使用[ :::no-loc(extern)::: "C"](../../cpp/using-:::no-loc(extern):::-to-specify-linkage.md)修饰符。 请确保该声明匹配每个符号的编译链接。 同样，如果在 C 程序将使用的 C++ 文件中定义符号，请在定义中使用 `:::no-loc(extern)::: "C"` 。

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>符号定义为 :::no-loc(static)::: ，稍后在文件外部引用

在 c + + 中，与 C 不同， [global :::no-loc(const)::: 蚂蚁](../../error-messages/tool-errors/global-:::no-loc(const):::ants-in-cpp.md)有 **`:::no-loc(static):::`** 链接。 若要绕过此限制，可以 **`:::no-loc(const):::`** 在标头文件中包括初始化并将该标头包含在 .cpp 文件中，也可以将变量设置为非 :::no-loc(const)::: ant，并使用 :::no-loc(const)::: ant 引用来访问它。

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>:::no-loc(static):::未定义类的成员

:::no-loc(static):::类成员必须具有唯一的定义，否则它将违反单个定义规则。 :::no-loc(static):::无法以内联方式定义的类成员必须通过使用其完全限定名称在一个源文件中进行定义。 如果根本没有定义此方法，则链接器会生成 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>生成依赖项仅在解决方案中定义为项目依赖项

在 Visual Studio 的早期版本中，此级别的依赖项已经足够。 但是，从 Visual Studio 2010 开始，Visual Studio 需要一个[项目到项目的引用](/visualstudio/ide/managing-references-in-a-project)。 如果你的项目没有项目到项目的引用，则可能会收到此链接器错误。 添加项目到项目引用以修复此错误。

### <a name="an-entry-point-isnt-defined"></a>未定义入口点

应用程序代码必须 `:::no-loc(main):::` `:::no-loc(wmain):::` 为控制台应用程序和 `:::no-loc(WinMain):::` 或 `:::no-loc(wWinMain):::` Windows 应用程序定义适当的入口点。 有关详细信息，请参阅[ :::no-loc(main)::: 函数和命令行参数](../../cpp/:::no-loc(main):::-function-command-line-args.md)或[ :::no-loc(WinMain)::: 函数](/windows/win32/api/winbase/nf-winbase-win:::no-loc(main):::)。 若要使用自定义入口点，请指定[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)链接器选项。

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>使用 Windows 应用程序的设置生成控制台应用程序

如果错误消息类似于函数*function_name* ** :::no-loc(extern)::: :::no-loc(WinMain)::: 中引用的无法解析的 al 符号**，则使用 **/SUBSYSTEM：控制台**（而不是 **/SUBSYSTEM： WINDOWS**）进行链接。 有关此设置的详细信息以及如何在 Visual Studio 中设置此属性的说明，请参阅 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>尝试将64位库链接到32位代码，或将32位库链接到64代码

链接到代码的库和对象文件必须编译为与代码相同的体系结构。 确保项目引用的库是针对与项目相同的体系结构编译的。 请确保 " [/LIBPATH](../../build/reference/libpath-additional-libpath.md) " 或 "**其他库目录**" 属性指向为正确的体系结构生成的库。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>将不同的编译器选项用于不同源文件中的函数内联

使用 .cpp 文件中定义的内联函数并在不同源文件中混合使用函数内联编译器可能会导致 LNK2019。 有关详细信息，请参阅 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>在其作用域外使用自动变量

自动（函数范围）变量仅可在该函数的范围内使用。 不能 **`:::no-loc(extern):::`** 在其他源文件中声明和使用这些变量。 有关示例，请参见 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>调用内部函数或将参数类型传递到目标体系结构不支持的内部函数

例如，如果您使用 :::no-loc(AVX2)::: 内部函数，但未指定[ / :::no-loc(ARCH)::: ： :::no-loc(AVX2)::: ](../../build/reference/arch-x86.md)编译器选项，则编译器会假定该内部 :::no-loc(extern)::: 函数为 al 函数。 编译器不会生成内联指令，而是生成对 :::no-loc(extern)::: 与内部函数同名的 al 符号的调用。 当链接器尝试找到此缺失函数的定义时，它会生成 LNK2019。 请确保仅使用目标体系结构支持的内部函数和类型。

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>混合使用本机代码 :::no-loc(wchar_t)::: 和代码

默认情况下，在 Visual Studio 2005 中完成的 c + + 语言一致性工作 **`:::no-loc(wchar_t):::`** 是本机类型。 如果并非所有文件都是使用相同的 **/zc： :::no-loc(wchar_t)::: **设置编译的，则类型引用可能不会解析为兼容的类型。 请确保 **`:::no-loc(wchar_t):::`** 所有库和对象文件中的类型都是兼容的。 请从 typedef 中更新 **`:::no-loc(wchar_t):::`** ，或在编译时使用一致的 **/zc： :::no-loc(wchar_t)::: **设置。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 vcpkg

如果尝试在生成过程中配置第三方库时遇到此错误，请考虑使用[vcpkg](../../vcpkg.md)（c + + 程序包管理器）安装和生成库。 vcpkg 支持较大和不断增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)。 它将成功生成所需的所有配置属性和依赖项设置为项目的一部分。

## <a name="diagnosis-tools"></a>诊断工具

有时很难判断链接器无法找到特定的符号定义的原因。 通常，问题是您在生成中未包含包含定义的代码。 或者，生成选项已为 al 符号创建了不同的修饰名称 :::no-loc(extern)::: 。 有多种工具和选项可以帮助你诊断 LNK2019 错误。

- [/:::no-loc(VERBOSE):::](../../build/reference/verbose-print-progress-messages.md)链接器选项可帮助你确定链接器引用了哪些文件。 此选项可帮助您验证您的生成中是否包括包含符号定义的文件。

- [/:::no-loc(EXPORTS):::](../../build/reference/dash-exports.md)实用工具的和 [/:::no-loc(SYMBOLS):::](../../build/reference/symbols.md) 选项 **:::no-loc(DUMPBIN):::** 可帮助你发现 .dll 和对象或库文件中定义了哪些符号。 请确保导出的修饰名与链接器搜索的修饰名称匹配。

- **:::no-loc(UNDNAME):::** 实用工具可以显示修饰名称的等效未修饰 :::no-loc(extern)::: al 符号。

## <a name="examples"></a>示例

以下是一些导致 LNK2019 错误的代码示例，以及关于如何修复错误的信息。

### <a name="a-symbol-is-declared-but-not-defined"></a>声明了符号，但是未对其进行定义

在此示例中， :::no-loc(extern)::: 声明了 al 变量但未对其进行定义：

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
:::no-loc(extern)::: char B[100];   // B isn't available to the linker
int :::no-loc(main):::() {
   B[0] = ' ';   // LNK2019
}
```

下面是另一个示例，其中变量和函数声明为 **`:::no-loc(extern):::`** 但未提供定义：

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
:::no-loc(extern)::: int i;
:::no-loc(extern)::: void g();
void f() {
   i++;
   g();
}
int :::no-loc(main):::() {}
```

除非 `i` 和 `g` 是在生成中包含的其中一个文件中定义的，否则链接器会生成 LNK2019。 你可以通过将包含定义的源代码文件作为编译的一部分包括在其中来修复错误。 或者，可以将包含定义的 .obj 文件或 .lib 文件传递到链接器。

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>:::no-loc(static):::已声明但未定义数据成员

当 :::no-loc(static)::: 声明但未定义数据成员时，也可能出现 LNK2019。 以下示例生成 LNK2019，并演示如何修复此错误。

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   :::no-loc(static)::: int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int :::no-loc(main):::() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-dont-match-the-definition"></a>声明参数不匹配定义

调用模板函数的代码必须拥有匹配的模板函数声明。 声明必须包括与定义相同的模板参数。 以下示例在用户定义的运算符上生成 LNK2019，并演示如何修复此错误。

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int :::no-loc(main):::() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved :::no-loc(extern):::al
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>:::no-loc(wchar_t):::类型定义不一致

此示例创建一个 DLL，该 DLL 包含一个使用的导出 `WCHAR` ，该导出将解析为 **`:::no-loc(wchar_t):::`** 。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to :::no-loc(wchar_t):::
__declspec(dllexport) void func(WCHAR*) {}
```

下一个示例使用上一示例中的 DLL，并生成 LNK2019，因为类型 `unsigned short*` 和 `WCHAR*` 不同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int :::no-loc(main):::() {
   func(0);
}
```

若要修复此错误，请将更改 **`unsigned short`** 为 **`:::no-loc(wchar_t):::`** 或 `WCHAR` ，或使用/zc 编译 LNK2019g **： :::no-loc(wchar_t)::: - **。

## <a name="additional-resources"></a>其他资源

有关 LNK2001 的可能原因和解决方案的详细信息，请参阅 Stack Overflow 问题：未[定义的引用/未解析的 " :::no-loc(extern)::: 符号错误"，以及如何修复该错误？](https://stackoverflow.com/q/12573816/2002113)。
