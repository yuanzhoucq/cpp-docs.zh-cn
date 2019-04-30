---
title: 链接器工具错误 LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: af40a48e36d316842ec9a744ad95d6c3b3af3731
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386338"
---
# <a name="linker-tools-error-lnk2019"></a>链接器工具错误 LNK2019

无法解析的外部符号*符号*函数中引用*函数*

编译后的代码*函数*使引用或调用*符号*，但该符号并不定义中的任何库或链接器指定的对象文件。

此错误消息后跟错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 必须修复所有 LNK2001 和 LNK2019 错误，若要修复错误 LNK1120。

## <a name="possible-causes"></a>可能的原因

有许多方法来获取此错误，但所有这些涉及对函数或变量的链接器不能引用*解决*，或查找的定义。 编译器可标识时某个符号未*声明*，但不是时它不是*定义*，因为可以在不同的源代码文件或库中的定义。 如果符号引用，但永远不会定义，链接器将生成未解析的外部符号错误。

以下是一些导致 LNK2019 的常见问题：

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>不链接的对象文件或库，它包含符号定义

在 Visual Studio 中，验证包含定义的源文件生成和链接为你的项目的一部分。 在命令行中，验证包含定义的源文件进行编译，并且生成的对象文件包含要链接的文件列表中。

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>符号的声明不拼写与符号的定义相同

验证声明和定义，用于正确拼写和大小写，并使用或调用符号的任何位置。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>使用了函数，但类型或参数数目不匹配函数定义

函数声明必须匹配定义。 验证函数调用是否匹配声明以及声明是否匹配定义。 调用模板函数的代码还必须拥有包括与定义相同的模板参数的匹配模板函数声明。 模板声明不匹配的示例，请参阅示例 LNK2019e.cpp 示例部分中。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>声明但未定义的函数或变量

这通常意味着在标头文件中，存在声明，但没有匹配的定义实现。 对于成员函数或静态数据成员，实现必须包括类范围选择器。 有关示例，请参见 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>调用约定是函数声明和函数定义之间的差异

调用约定 ([__cdecl](../../cpp/cdecl.md)、 [__stdcall](../../cpp/stdcall.md)、 [__fastcall](../../cpp/fastcall.md)或 [__vectorcall](../../cpp/vectorcall.md)) 作为修饰名称的一部分进行编码。 验证调用约定是否相同。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>符号在 C 文件中，定义但未使用 extern"C"中声明C++文件

在作为 C 编译的文件中定义的符号拥有与在 C++ 文件中声明的符号不同的修饰名称，除非使用了 [extern "C"](../../cpp/using-extern-to-specify-linkage.md) 修饰符。 验证声明是否匹配每个符号的编译链接。 同样，如果在 C 程序将使用的 C++ 文件中定义符号，请在定义中使用 `extern "C"` 。

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>符号定义为静态，并随后在文件外部引用

与 C 不同，在 C++ 中， [全局常量](../../error-messages/tool-errors/global-constants-in-cpp.md) 拥有 `static` 链接。 若要避开此限制，你可以在头文件中包括 `const` 初始化并将该标头包括在你的 .cpp 文件中，或者你可以让变量成为非常量并使用常量引用来访问它。

### <a name="a-static-member-of-a-class-is-not-defined"></a>未定义类的静态成员

静态类成员必须拥有唯一的定义，否则它将违反单个定义规则。 无法以内联方式定义的静态类成员必须通过使用其完全限定名称在一个源文件中进行定义。 如果没有进行定义，那么链接器会生成 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>生成依赖项仅定义为解决方案中的项目依赖项

在早期版本的 Visual Studio 中，此级别的依赖项已经足够。 但是，需要从 Visual Studio 2010 开始，Visual Studio[项目到项目引用](/visualstudio/ide/managing-references-in-a-project)。 如果你的项目没有项目到项目引用，那么你可能收到此链接器错误。 添加项目到项目引用以修复此错误。

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>生成控制台应用程序使用 Windows 应用程序的设置

如果错误消息类似于**WinMain 函数中引用无法解析的外部符号** *function_name*，通过使用链接 **/subsystem: console**而不是 **/Subsystem: windows**。 有关此设置的详细信息以及如何在 Visual Studio 中设置此属性的说明，请参阅 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>尝试将 64 位库链接到 32 位代码或 32 位到 64 位代码库

必须为你的代码相同的体系结构编译库和对象文件链接到你的代码。 验证你的项目引用针对你的项目相同的体系结构编译的库。 请确保[/LIBPATH](../../build/reference/libpath-additional-libpath.md)或**附加库目录**path 选项由链接器指向正确的体系结构构建的库。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>为在不同源文件中内联的函数使用不同的编译器选项

使用 .cpp 文件中定义的内联函数并在不同源文件中混合使用函数内联编译器可能会导致 LNK2019。 有关详细信息，请参阅 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>范围外使用自动变量

自动（函数范围）变量仅可在该函数的范围内使用。 这些变量不可声明为 `extern` ，也不能在其他源文件中使用。 有关示例，请参见 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>调用内部函数或将参数类型传递到目标体系结构不支持的内部函数

例如，如果你使用 AVX2 内部函数，但未指定 [/ARCH:AVX2](../../build/reference/arch-x86.md) 编译器选项，那么编译器会假定该内部函数是外部函数。 编译器不会生成内联指令，相反，它会生成一个对与内部函数同名的外部符号的调用。 当链接器尝试找到此缺失函数的定义时，它会生成 LNK2019。 验证是否只使用了目标体系结构支持的内部函数和类型。

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>混合使用本机 wchar\_代码不会使用 t

在 Visual C++ 2005 中完成的 C++ 语言一致性工作让 `wchar_t` 成为默认本机类型。 你必须使用 [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 编译器选项来生成兼容使用 Visual C++ 早期版本进行编译的库和对象文件的代码。 如果不是所有文件使用相同的已都编译 **/Zc:wchar\_t**设置，类型引用可能不会解析为兼容的类型。 验证所有库和对象文件中的 `wchar_t` 类型是否兼容，方法是更新使用的类型或在编译时使用一致的 **/Zc:wchar_t** 设置。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果尝试将第三方库配置为生成的一部分时看到此错误，请考虑使用[Vcpkg](../../vcpkg.md)，视觉对象C++包管理器中，若要安装并生成库。 Vcpkg 支持大量且持续增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)，并设置所有配置属性和依赖项所需的成功生成项目的一部分。 有关详细信息，请参阅相关[可视化C++博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="diagnosis-tools"></a>诊断工具

很难判断为什么链接器无法找到特定的符号定义。 问题通常是未包含的代码包含在生成中的定义或生成选项创建了不同修饰外部符号的名称。 有许多工具和选项可以帮助你诊断 LNK2019 错误。

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 链接器选项可帮助你确定链接器引用了哪些文件。 这可以帮助验证你的生成中是否包括了包含符号定义的文件。

- [/Exports](../../build/reference/dash-exports.md)并[/ 符号](../../build/reference/symbols.md)选项**DUMPBIN**实用工具可帮助你发现.dll 和对象或库文件中定义了哪些符号。 验证导出的修饰名称是否匹配链接器搜索的修饰名称。

- **UNDNAME**实用工具可以显示修饰名称的等效未修饰外部符号。

## <a name="examples"></a>示例

以下是一些导致 LNK2019 错误的代码示例，以及关于如何修复错误的信息。

### <a name="a-symbol-is-declared-but-not-defined"></a>声明了符号，但是未对其进行定义

在此示例中，外部声明变量，但未定义：

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

下面是一个变量和函数声明为另一个示例`extern`但不提供任何定义：

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

除非`i`和`g`定义在生成中包含的文件之一，链接器会生成 LNK2019。 你可以通过将包含定义的源代码文件作为编译的一部分包括在其中来修复错误。 或者，可以传递.obj 文件或.lib 文件包含到链接器的定义。

### <a name="a-static-data-member-is-declared-but-not-defined"></a>声明了静态数据成员，但是未对其进行定义

LNK2019 还可能会在声明了静态数据成员但未对其进行定义时发生。 以下示例生成 LNK2019，并演示如何修复此错误。

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

### <a name="declaration-parameters-do-not-match-definition"></a>声明参数不匹配定义

调用模板函数的代码必须拥有匹配的模板函数声明。 声明必须包括与定义相同的模板参数。 以下示例在用户定义的运算符上生成 LNK2019，并演示如何修复此错误。

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
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

### <a name="inconsistent-wchart-type-definitions"></a>不一致的 wchar_t 类型定义

此示例将创建具有使用的导出的 DLL `WCHAR`，它解析为`wchar_t`。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

下一步的示例在上一示例中，使用该 DLL，并生成 LNK2019，原因类型无符号 short * 和 WCHAR\*不相同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

若要解决此错误，请更改`unsigned short`到`wchar_t`或`WCHAR`，或使用编译 LNK2019g.cpp **/zc: wchar_t-**。

## <a name="additional-resources"></a>其他资源

LNK2001 可能的原因和解决方案的详细信息，请参阅堆栈溢出问题[什么是未定义引用/未解析的外部符号错误以及如何修复此错误？](http://stackoverflow.com/q/12573816/2002113)。

