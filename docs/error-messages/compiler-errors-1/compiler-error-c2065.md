---
title: 编译器错误 C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 68817498d6f29ef5982b72a2fee4e64a4423ccde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214810"
---
# <a name="compiler-error-c2065"></a>编译器错误 C2065

> "*identifier*"：未声明的标识符

编译器找不到标识符的声明。 此错误有许多可能的原因。 C2065 的最常见原因是未声明标识符，标识符的拼写错误，文件中未包含声明标识符的标头，或者标识符缺少作用域限定符，例如， `cout` 而不是 `std::cout` 。 有关 c + + 中的声明的详细信息，请参阅[声明和定义（c + +）](../../cpp/declarations-and-definitions-cpp.md)。

下面是一些常见的问题和解决方案。

## <a name="the-identifier-is-undeclared"></a>标识符未声明

如果标识符为变量或函数名称，则必须在使用之前对其进行声明。 函数声明还必须包含其参数的类型，然后才能使用函数。 如果使用声明该变量 **`auto`** ，则编译器必须能够从其初始值设定项推断类型。

如果标识符是类或结构的成员，或者是在命名空间中声明的，则必须通过类或结构名称或命名空间名称（在结构、类或命名空间范围外使用时）对其进行限定。 此外，命名空间必须通过 **`using`** 指令（如）置于范围内 `using namespace std;` ，或者必须通过声明将成员名称置于范围内 **`using`** ，如 `using std::string;` 。 否则，非限定名称将被视为当前范围中未声明的标识符。

如果标识符是用户定义的类型（例如，或）的标记，则 **`class`** **`struct`** 必须先声明标记的类型，然后才能使用。 例如，声明 `struct SomeStruct { /*...*/ };` 必须存在，然后才能 `SomeStruct myStruct;` 在代码中声明变量。

如果标识符是类型别名，则必须使用 **`using`** 声明或 **`typedef`** 在使用之前声明类型。 例如，必须先声明， `using my_flags = std::ios_base::fmtflags;` 然后才能将 `my_flags` 用作的类型别名 `std::ios_base::fmtflags` 。

## <a name="example-misspelled-identifier"></a>示例：拼写错误的标识符

如果标识符名称拼写错误，或者标识符使用了错误的大写和小写字母，则通常会出现此错误。 声明中的名称必须与你使用的名称完全匹配。

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>示例：使用未区分范围的标识符

如果标识符的范围不正确，则会发生此错误。 如果你在使用时看到 C2065 `cout` ，这就是原因。 如果 c + + 标准库函数和运算符不是由命名空间完全限定的，或者您未 `std` 使用指令将命名空间引入当前范围 **`using`** ，则编译器无法找到它们。 若要解决此问题，必须完全限定标识符名称，或指定具有指令的命名空间 **`using`** 。

由于 `cout` 和 `endl` 在命名空间中定义，因此此示例无法编译 `std` ：

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

**`class`** 当在、或类型内声明的标识符在 **`struct`** **`enum class`** 该范围之外使用时，还必须通过其封闭范围的名称进行限定。

## <a name="example-precompiled-header-isnt-first"></a>示例：预编译头不是第一

如果在预编译头文件 #include 之前放置了任何预处理器指令，如 #include、#define 或 #pragma，则会发生此错误。 如果源文件使用预编译头文件（即，如果它是使用 **/yu**编译器选项编译的），则将忽略预编译头文件之前的所有预处理器指令。

此示例无法编译，因为 `cout` 和 `endl` 在 \<iostream> 标头中定义，这会被忽略，因为它包含在预编译头文件之前。 若要生成此示例，请创建所有三个文件，然后编译 stdafx.h，然后编译 C2065_pch .cpp。

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

若要解决此问题，请将的 #include 添加 \<iostream> 到预编译头文件中，或在预编译头文件包含在您的源文件中后移动它。

## <a name="example-missing-header-file"></a>示例：缺少标头文件

尚未包含声明该标识符的标头文件。 确保包含标识符声明的文件包含在使用它的每个源文件中。

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

另一个可能的原因是，使用初始值设定项列表时不包含 \<initializer_list> 标头。

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

如果你定义、或，你可能会在 Windows 桌面应用源文件中看到此错误 `VC_EXTRALEAN` `WIN32_LEAN_AND_MEAN` `WIN32_EXTRA_LEAN` 。 这些预处理器宏从 windows .h 和 afxv w32 中排除一些标头文件， \_ 以加快编译速度。 查看 windows .h，并 afxv_w32 .h 了解排除内容的最新说明。

## <a name="example-missing-closing-quote"></a>示例：缺少右引号

如果在字符串常量后缺少右引号，则会出现此错误。 这是混淆编译器的一种简单方法。 请注意，缺少的右引号可能在报告的错误位置之前有多行。

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>示例：在 for 循环范围之外使用迭代器

如果在循环中声明迭代器变量 **`for`** ，然后尝试在循环范围之外使用该迭代器变量，则会发生此错误 **`for`** 。 默认情况下，编译器启用[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。 有关详细信息，请参阅[调试迭代器支持](../../standard-library/debug-iterator-support.md)。

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>示例：预处理器删除声明

如果你引用的函数或变量属于有条件编译的代码，但没有为当前配置进行编译，则会出现此错误。 如果在当前不受生成环境支持的标头文件中调用函数，也会发生这种情况。 如果某些变量或函数仅在定义特定预处理器宏时才可用，请确保仅当定义了同一预处理器宏时，才能编译调用这些函数的代码。 此问题很容易出现在 IDE 中，因为如果没有为当前生成配置定义所需的预处理器宏，则函数的声明将灰显。

这是在调试（而不是零售）中生成时有效的代码示例：

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>示例： c + +/CLI 类型推导失败

如果无法从使用的参数推导出预期类型参数，则调用泛型函数时可能会发生此错误。 有关详细信息，请参阅[泛型函数（c + +/cli）](../../extensions/generic-functions-cpp-cli.md)。

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>示例： c + +/CLI 特性参数

此错误还可能是对 Visual Studio 2005 执行的编译器一致性工作的结果：对 Visual C++ 属性的参数检查。

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
