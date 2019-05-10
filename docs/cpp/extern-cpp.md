---
title: extern (C++)
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: 4a3a4e158794e06f28c638e87e014ddc3fb99837
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183734"
---
# <a name="extern-c"></a>extern (C++)

**Extern**关键字应用于全局变量、 函数或模板声明来指定该操作的名称具有*外部链接*。 链接和为何使用全局变量，建议不要使用的背景信息，请参阅[程序和链接](program-and-linkage-cpp.md)。

**Extern**关键字具有四个的含义，具体取决于上下文：

1. 在非常量全局变量声明中， **extern**指定另一个翻译单元中定义的变量或函数。 **Extern**必须应用在其中定义的变量除外的所有文件中。
1. 在 const 变量声明中，它指定该变量具有外部链接。 **Extern**必须应用于所有文件中的所有声明。 （全局常量变量具有内部链接默认情况下。）
1. **extern"C"** 指定该函数在其他地方定义，并使用 C 语言调用约定。 Extern"C"修饰符还可能会应用于在块中的多个函数声明。
1. 在模板声明中，它指定该模板，已实例化其他位置。 这是一种优化，告知编译器，它可以重新使用其他实例化，而不是创建一个新的当前的位置。 详细了解的这种用法**extern**，请参阅[模板](templates-cpp.md)。

## <a name="extern-linkage-for-non-const-globals"></a>非常量全局函数的外部链接

当链接器发现**extern**之前全局变量声明，它会查找另一个翻译单元中的定义。 在全局范围内的非常量变量的声明是外部默认设置。仅适用**extern**到不提供定义的声明。

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

## <a name="extern-linkage-for-const-globals"></a>const 全局函数的外部链接

一个**const**全局变量具有内部链接，默认情况下。 如果你想要具有外部链接的变量，将应用**extern**关键字来定义以及关于其他文件中的所有其他声明：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>extern constexpr 链接

在 Visual Studio 2017 版本 15.3 及更早版本中，编译器常常 constexpr 变量内部链接即使变量标记为外部。 在 Visual Studio 2017 版本 15.5 中，新编译器开关 ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) 启用符合标准的正确行为。 这最终将成为默认设置。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果标头文件包含变量的声明的 extern constexpr，它需要标记为 **__declspec （selectany)** 以便正确组合其重复声明：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>extern"C"和 extern"C++"函数声明

在C++，与字符串一起使用时**extern**指定另一种语言的链接约定，所用的声明符。 仅在之前被声明为具有 C 链接的情况下，才能访问 C 函数和数据。 但是，必须在单独编译的翻译单元中定义它们。

Microsoft C++ 支持字符串 **"C"** 和 **"C++"** 中*字符串文本*字段。 所有标准包含文件都使用**extern** "C"语法以允许运行时库函数中使用C++程序。

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

如果函数有多个链接规范，则它们必须一致；将函数声明为同时具有 C 和 C++ 链接是错误的。 此外，如果一个函数的两个声明出现在一个程序中，并且它们一个有链接规范，另一个没有，则有链接规范的声明必须是第一个。 将为已具有链接规范的函数的所有冗余声明提供第一个声明中指定的链接。 例如：

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[程序和链接](program-and-linkage-cpp.md)<br/>
[extern 存储类说明符在 C 中](../c-language/extern-storage-class-specifier.md)<br/>
[在 C 中的标识符的行为](../c-language/behavior-of-identifiers.md)<br/>
[C 中的链接](../c-language/linkage.md)