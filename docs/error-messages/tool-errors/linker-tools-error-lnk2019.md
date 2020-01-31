---
title: 链接器工具错误 LNK2019
description: 有关 Microsoft Visual Studio 链接器错误 LNK2019 的全部信息，以及如何在 C 和C++代码中诊断和更正此问题。
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- main
- WinMain
- wmain
- wWinMain
- __cdecl
- __stdcall
- __fastcall
- __vectorcall
- extern
- static
- const
- ARCH
- AVX2
- wchar_t
- VERBOSE
- EXPORTS
- SYMBOLS
- DUMPBIN
- UNDNAME
ms.openlocfilehash: 0e741c1442f9762c4cf5f9b891c4cd7c38103dfe
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123911"
---
# <a name="linker-tools-error-lnk2019"></a>链接器工具错误 LNK2019

> 函数 "*function*" 中引用了未解析的外部符号 "*symbol*"

已编译的*函数的函数*对*符号*进行引用或调用，但是链接器在要链接的任何库或对象文件中都找不到符号定义。

此错误消息后跟严重错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 若要修复错误 LNK1120，必须先修复所有 LNK2001 和 LNK2019 错误。

## <a name="possible-causes"></a>可能的原因

有多种方法可获取此错误。 所有这些都涉及到链接器无法*解析*的函数或变量的引用，或查找的定义。 编译器可以确定符号未*声明*的时间，但无法判断符号未*定义*的时间。 这是因为定义可能位于不同的源文件或库中。 如果某个符号被引用但从未定义，则链接器将生成一个无法解析的外部符号错误。

以下是一些导致 LNK2019 的常见问题：

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>不编译包含符号定义的源文件

在 Visual Studio 中，请确保定义符号的源文件编译为项目的一部分。 查看中间生成输出目录中是否有匹配的 .obj 文件。 如果未编译源文件，请在解决方案资源管理器中右键单击该文件，然后选择 "**属性**" 以检查该文件的属性。 "**常规**" 页上的 "**配置属性**" > 应显示**CC++ /编译器** **项类型**。 在命令行上，确保编译了包含定义的源文件。

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>未链接包含符号定义的对象文件或库

在 Visual Studio 中，请确保包含符号定义的对象文件或库链接为项目的一部分。 在命令行上，确保要链接的文件列表包含对象文件或库。

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>符号声明的拼写与符号的定义不同

验证在声明和定义中以及使用或调用该符号的任何位置都使用正确的拼写和大小写。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>使用了函数，但是参数的类型或数量与函数定义不匹配

函数声明必须匹配定义。 请确保函数调用与声明匹配，并且声明与定义匹配。 调用模板函数的代码还必须拥有包括与定义相同的模板参数的匹配模板函数声明。 有关模板声明不匹配的示例，请参阅示例部分中的示例 LNK2019e。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>已声明但未定义函数或变量

当标头文件中存在声明，但未实现匹配定义时，可能会出现 LNK2019。 对于成员函数或 static 数据成员，实现必须包括类范围选择器。 有关示例，请参见 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>函数声明和函数定义之间的调用约定不同

调用约定（[__cdecl](../../cpp/cdecl.md)、 [__stdcall](../../cpp/stdcall.md)、 [__fastcall](../../cpp/fastcall.md)或[__vectorcall](../../cpp/vectorcall.md)）作为修饰名称的一部分进行编码。 请确保调用约定是相同的。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-opno-locextern-c-in-a-c-file"></a>符号在 C 文件中定义，但未使用C++文件中的 extern "C" 声明

在编译为 C 的文件中定义的符号具有与C++文件中声明的符号不同的修饰名称，除非使用[extern "C"](../../cpp/using-extern-to-specify-linkage.md)修饰符。 请确保该声明匹配每个符号的编译链接。 同样，如果在 C 程序将使用的 C++ 文件中定义符号，请在定义中使用 `extern "C"` 。

### <a name="a-symbol-is-defined-as-opno-locstatic-and-then-later-referenced-outside-the-file"></a>符号定义为 static，并随后在文件外部引用。

与 C 不同，在 C++ 中， [全局常量](../../error-messages/tool-errors/global-constants-in-cpp.md) 拥有 `static` 链接。 若要避开此限制，你可以在头文件中包括 `const` 初始化并将该标头包括在你的 .cpp 文件中，或者你可以让变量成为非常量并使用常量引用来访问它。

### <a name="a-opno-locstatic-member-of-a-class-isnt-defined"></a>未定义类的 static 成员

static 类成员必须具有唯一的定义，否则它将违反单个定义规则。 不能以内联方式定义 static 类成员必须通过使用其完全限定名称在一个源文件中进行定义。 如果根本没有定义此方法，则链接器会生成 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>生成依赖项仅在解决方案中定义为项目依赖项

在 Visual Studio 的早期版本中，此级别的依赖项已经足够。 但是，从 Visual Studio 2010 开始，Visual Studio 需要一个[项目到项目的引用](/visualstudio/ide/managing-references-in-a-project)。 如果你的项目没有项目到项目的引用，则可能会收到此链接器错误。 添加项目到项目引用以修复此错误。

### <a name="an-entry-point-isnt-defined"></a>未定义入口点

应用程序代码必须定义适用于控制台应用程序的 `main` 或 `wmain`，以及 Windows 应用程序 `WinMain` 或 `wWinMain`。 有关详细信息，请参阅[main 函数和命令行参数](../../cpp/main-function-command-line-args.md)或[WinMain 函数](/windows/win32/api/winbase/nf-winbase-winmain)。 若要使用自定义入口点，请指定[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)链接器选项。

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>使用 Windows 应用程序的设置生成控制台应用程序

如果错误消息类似于函数 function_name**中引用的无法解析的外部符号 WinMain** ，请使用 **/SUBSYSTEM：控制台**而不是 **/SUBSYSTEM： WINDOWS**进行链接。 有关此设置的详细信息以及如何在 Visual Studio 中设置此属性的说明，请参阅 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>尝试将64位库链接到32位代码，或将32位库链接到64代码

链接到代码的库和对象文件必须编译为与代码相同的体系结构。 确保项目引用的库是针对与项目相同的体系结构编译的。 请确保 " [/LIBPATH](../../build/reference/libpath-additional-libpath.md) " 或 "**其他库目录**" 属性指向为正确的体系结构生成的库。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>将不同的编译器选项用于不同源文件中的函数内联

使用 .cpp 文件中定义的内联函数并在不同源文件中混合使用函数内联编译器可能会导致 LNK2019。 有关详细信息，请参阅 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>在其作用域外使用自动变量

自动（函数范围）变量仅可在该函数的范围内使用。 这些变量不可声明为 `extern` ，也不能在其他源文件中使用。 有关示例，请参见 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>调用内部函数或将参数类型传递到目标体系结构不支持的内部函数

例如，如果使用 AVX2 内部函数，但未指定[/ARCH：AVX2](../../build/reference/arch-x86.md)编译器选项，则编译器假定该内部函数是外部函数。 编译器不会生成内联指令，相反，它会生成一个对与内部函数同名的外部符号的调用。 当链接器尝试找到此缺失函数的定义时，它会生成 LNK2019。 请确保仅使用目标体系结构支持的内部函数和类型。

### <a name="you-mix-code-that-uses-native-opno-locwchar_t-with-code-that-doesnt"></a>将使用本机 wchar_t 的代码与不

C++默认情况下，在 Visual Studio 2005 中所执行的语言一致性工作 **wchar_t** 本机类型。 如果并非所有文件都是使用同一个 **/zc：wchar_t** 设置编译的，则类型引用可能不会解析为兼容的类型。 请确保所有库和对象文件中的 **wchar_t** 类型都是兼容的。 请从 **wchar_t** 的 typedef 进行更新，或在编译时使用一致的 **/zc：wchar_t** 设置。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果尝试在生成过程中配置第三方库时遇到此错误，请考虑使用[Vcpkg](../../vcpkg.md)（Visual C++ Package Manager）来安装和生成库。 Vcpkg 支持较大和不断增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)。 它将成功生成所需的所有配置属性和依赖项设置为项目的一部分。 有关详细信息，请参阅相关[的C++视觉对象博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="diagnosis-tools"></a>诊断工具

有时很难判断链接器无法找到特定的符号定义的原因。 通常，问题是您在生成中未包含包含定义的代码。 或者，生成选项为外部符号创建了不同的修饰名。 有多种工具和选项可以帮助你诊断 LNK2019 错误。

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)链接器选项可帮助你确定链接器引用了哪些文件。 此选项可帮助您验证您的生成中是否包括包含符号定义的文件。

- **DUMPBIN** 实用工具的[/EXPORTS](../../build/reference/dash-exports.md)和[/SYMBOLS](../../build/reference/symbols.md)选项可帮助你发现 .dll 和对象或库文件中定义了哪些符号。 请确保导出的修饰名与链接器搜索的修饰名称匹配。

- **UNDNAME** 实用工具可以显示修饰名称的等效未修饰外部符号。

## <a name="examples"></a>示例

以下是一些导致 LNK2019 错误的代码示例，以及关于如何修复错误的信息。

### <a name="a-symbol-is-declared-but-not-defined"></a>声明了符号，但是未对其进行定义

在此示例中，声明了外部变量但未对其进行定义：

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

下面是另一个示例，其中变量和函数被声明为 `extern` 但未提供定义：

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

除非在生成中包含的其中一个文件中定义 `i` 和 `g`，否则链接器会生成 LNK2019。 你可以通过将包含定义的源代码文件作为编译的一部分包括在其中来修复错误。 或者，可以将包含定义的 .obj 文件或 .lib 文件传递到链接器。

### <a name="a-opno-locstatic-data-member-is-declared-but-not-defined"></a>已声明但未定义 static 数据成员

如果声明了 static 数据成员但未对其进行定义，则可能出现 LNK2019。 以下示例生成 LNK2019，并演示如何修复此错误。

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
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

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-opno-locwchar_t-type-definitions"></a>wchar_t 类型定义不一致

此示例创建一个 DLL，该 DLL 包含一个使用 `WCHAR`的导出，该导出可解析为 `wchar_t`。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

下一个示例使用上一示例中的 DLL，并生成 LNK2019，因为 `unsigned short*` 和 `WCHAR*` 的类型不相同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

若要修复此错误，请将 `unsigned short` 更改为 `wchar_t` 或 `WCHAR`，或者使用 **/zc：wchar_t-** 编译 LNK2019g。

## <a name="additional-resources"></a>其他资源

有关 LNK2001 的可能原因和解决方案的详细信息，请参阅 Stack Overflow 问题[：未定义的引用/未解析的外部符号错误以及如何修复该错误？](https://stackoverflow.com/q/12573816/2002113)。
