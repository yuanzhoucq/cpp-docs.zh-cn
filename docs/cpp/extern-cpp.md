---
title: extern (C++)
description: C++ Language extern 关键字指导。
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821761"
---
# <a name="opno-locextern-c"></a>extern (C++)

**extern** 关键字可应用于全局变量、函数或模板声明。 它指定该符号具有*外部链接*。 有关链接的背景信息和不鼓励使用全局变量的原因，请参阅[翻译单元和链接](program-and-linkage-cpp.md)。

根据上下文， **extern** 关键字有四种含义：

- 在非 **const** 全局变量声明中， **extern** 指定在另一个翻译单元中定义变量或函数。 除了定义变量的文件以外， **extern** 必须应用于所有文件中。

- 在 **const** 变量声明中，它指定变量具有外部链接。 **extern** 必须应用于所有文件中的所有声明。 （默认情况下，全局 **const** 变量具有内部链接。）

- **extern "C"** 指定在其他位置定义该函数，并使用 C 语言调用约定。 extern "C" 修饰符也可以应用于块中的多个函数声明。

- 在模板声明中， **extern** 指定已在其他位置实例化模板。 **extern** 告知编译器可以重复使用其他实例化，而不是在当前位置创建新的实例化。 有关 **extern** 的这种用法的详细信息，请参阅[显式实例化](explicit-instantiation.md)。

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>extern 非const globals 的链接

当链接器在全局变量声明之前看到 **extern** ，它将在另一个翻译单元中查找定义。 默认情况下，全局范围内的非 **const** 变量的声明是外部的。 仅将 **extern** 应用到未提供定义的声明。

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>const 全局 extern 链接

默认情况下， **const** 全局变量具有内部链接。 如果希望变量有外部链接，请将 **extern** 关键字应用于定义，并应用于其他文件中的所有其他声明：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>extern constexpr 链接

在 Visual Studio 2017 版本15.3 及更早版本中，编译器始终提供 **constexpr** 变量内部链接，即使该变量标记为 **extern** 。 在 Visual Studio 2017 版本15.5 及更高版本中， [/zc： externConstexpr](../build/reference/zc-externconstexpr.md)编译器开关可实现符合标准的正确行为。 最终，选项将成为默认值。 [/permissive-](../build/reference/permissive-standards-conformance.md)选项不会启用 **/zc： externConstexpr**。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果标头文件包含 **constexpr** 声明 **extern** 的变量，则必须将其标记为 `__declspec(selectany)`，以正确地将其重复的声明组合在一起：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern "C" 和 extern "C++" 函数声明

在C++中，当与字符串一起使用时， **extern** 指定将另一种语言的链接约定用于声明符。 仅当 c 函数和数据以前已声明为具有 C 链接时，才能访问这些函数和数据。 但是，必须在单独编译的翻译单元中定义它们。

Microsoft C++ 支持字符串 **"C"** 和 **"C++"** 中*字符串文本*字段。 所有标准包含文件都使用 **extern "C"** 语法，以允许在程序中C++使用运行时库函数。

## <a name="example"></a>示例

下面的示例演示如何声明具有 C 链接的名称：

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

如果函数有多个链接规范，则必须同意。 将函数声明为具有 C 和C++链接都是错误的。 此外，如果一个函数的两个声明出现在一个程序中，并且它们一个有链接规范，另一个没有，则有链接规范的声明必须是第一个。 将为已具有链接规范的函数的所有冗余声明提供第一个声明中指定的链接。 例如：

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)\
[翻译单元和链接](program-and-linkage-cpp.md)\
[C\ 中的extern 存储类说明符](../c-language/extern-storage-class-specifier.md)
[C\ 中标识符的行为](../c-language/behavior-of-identifiers.md)
[C 中的链接](../c-language/linkage.md)
