---
title: "编译器错误 C2065 |Microsoft 文档"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a20fee308a8ed9d237f8fc76df60964704c9c69d
ms.sourcegitcommit: 1e367a5f5c5a6fd0b6018f4fb5edcdf2f1a8085c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2018
---
# <a name="compiler-error-c2065"></a>编译器错误 C2065

> *标识符*： 未声明的标识符

编译器找不到标识符的声明。 有许多可能的原因，此错误。 C2065 最常见原因是，该标识符未声明、 拼写错误标识符、 标识符的声明位置的标头未包含在文件中，或标识符缺少范围限定符，例如，`cout`而不是`std::cout`. 有关 c + + 中的声明的详细信息，请参阅[声明和定义 （c + +）](../../cpp/declarations-and-definitions-cpp.md)。

以下是一些常见的问题和解决方案中更多详细信息。

## <a name="the-identifier-is-undeclared"></a>未声明的标识符都是

如果该标识符是变量或函数名，必须将其声明，然后才能使用。 函数声明还必须包括其参数的类型，然后才能使用该函数。 如果使用声明变量`auto`，编译器必须能够从其初始值设定项推断类型。

如果标识符是类或结构的成员或命名空间中声明，则必须表示为类或结构名称或命名空间名称，这是时的结构、 类或命名空间的范围之外使用。 或者，命名空间必须放入范围内`using`指令如`using namespace std;`，或成员名称必须放入范围内`using`声明，如`using std::string;`。 否则的非限定的名称被视为可在当前范围内未声明的标识符。

如果该标识符是的标记的用户定义的类型，例如，`class`或`struct`，必须声明该标记的类型，然后才能使用。 例如，声明`struct SomeStruct { /*...*/ };`之前可以声明一个变量，必须存在`SomeStruct myStruct;`在代码中。

如果该标识符是类型别名，必须通过使用声明的类型`using`声明或`typedef`前，可以使用它。 例如，您必须声明`using my_flags = std::ios_base::fmtflags;`然后才能使用`my_flags`为的类型别名`std::ios_base::fmtflags`。

## <a name="example-misspelled-identifier"></a>示例： 拼写错误的标识符

此错误通常在标识符名称拼写错误，或标识符使用错误的大写和小写字母时发生。 声明中的名称必须与你使用的名称完全匹配。

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

## <a name="example-use-an-unscoped-identifier"></a>示例： 使用未区分范围的标识符

如果你的标识符的范围不正确，可能出现此错误。 如果你使用时，将显示 C2065 `cout`，这是可能的原因。 当 c + + 标准库函数和运算符未完全限定的命名空间，或不使`std`到使用的当前作用域的命名空间`using`指令，编译器找不到它们。 若要解决此问题，你必须完全限定的标识符名称，或指定的命名空间与`using`指令。

此示例无法进行编译因为`cout`和`endl`中定义`std`命名空间：

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

内部声明的标识符`class`， `struct`，或`enum class`超出该作用域中使用它们时类型必须还通过其封闭作用域的名称进行限定。

## <a name="example-precompiled-header-isnt-first"></a>预编译标头不第一个示例：

如果你将任何预处理器指令，例如，可能出现此错误 #include，#define，或 #pragma 之前, #include 的预编译的头文件。 如果源文件使用预编译标头文件 (即，如果它通过编译**/Yu**编译器选项) 然后忽略预编译标头文件之前的所有预处理器指令。

此示例无法进行编译因为`cout`和`endl`中定义\<iostream > 标头，因为它包含在预编译的头文件之前忽略。 若要生成此示例中，创建所有三个文件，然后编译 stdafx.cpp，然后编译 C2065_pch.cpp。

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
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

若要解决此问题，添加 #include \<iostream > 到预编译的头文件或移动之后预编译的头文件包含在您的源文件。

## <a name="example-missing-header-file"></a>示例： 缺少标头文件

你没有包括头文件声明标识符。 请确保在使用它的每个源代码文件中包括包含标识符的声明的文件。

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

另一个可能的原因是如果你使用初始值设定项列表而不包括\<initializer_list > 标头。

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

如果你定义，可能会看到此错误在 Windows 桌面应用程序源文件`VC_EXTRALEAN`， `WIN32_LEAN_AND_MEAN`，或`WIN32_EXTRA_LEAN`。 这些预处理器宏排除某些头文件从 windows.h 和 afxv\_w32.h 加快编译。 查看 windows.h 和 afxv_w32.h，了解排除的最新描述。

## <a name="example-missing-closing-quote"></a>示例： 缺少右引号

如果字符串常量后缺少右引号，则可能出现此错误。 这是一种混淆编译器简便方法。 请注意，缺少右引号可能报告的错误位置前面几行。 

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>示例： 使用 for 循环范围之外的迭代器

如果声明中的迭代器变量，会出现此错误`for`循环，然后尝试使用该迭代器变量的作用域之外`for`循环。 编译器启用[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)默认情况下的编译器选项。 请参阅[调试迭代器支持](../../standard-library/debug-iterator-support.md)有关详细信息。

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

## <a name="example-preprocessor-removed-declaration"></a>预处理器已删除的声明示例：

如果引用的函数或在未编译为你的当前配置的有条件地编译代码的变量，则可能出现此错误。 如果你在生成环境中当前不支持的标头文件中调用函数，也会发生此问题。 如果定义特定的预处理器宏时，某些变量或函数才可用，，请确保定义相同的预处理器宏时，可以仅编译调用这些函数的代码。 此问题是很容易识别在 IDE 中，因为如果没有为当前生成配置定义所需的预处理器宏，该函数的声明灰显。

这是代码的适用于构建在调试，但不是零售的一个示例：

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

## <a name="example-ccli-type-deduction-failure"></a>示例： C + + /cli CLI 类型推理失败

如果不能从所使用的参数推导预期的类型参数，会调用泛型函数时，此错误。 有关详细信息，请参阅[泛型函数 (C + + /cli CLI)](../../windows/generic-functions-cpp-cli.md)。

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

## <a name="example-ccli-attribute-parameters"></a>示例： C + + /cli CLI 属性参数

此错误还可能来自于为 Visual C++ 2005 执行的编译器一致性工作：Visual C++ 特性的参数检查。

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
