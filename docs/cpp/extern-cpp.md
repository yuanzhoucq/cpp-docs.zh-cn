---
title: extern （C++）
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301530"
---
# <a name="extern-c"></a>extern （C++）

**Extern**关键字应用于全局变量、函数或模板声明，以指定该内容的名称具有*外部链接*。 有关链接的背景信息和不鼓励使用全局变量的原因，请参阅[翻译单元和链接](program-and-linkage-cpp.md)。

**Extern**关键字有四种含义，具体取决于上下文：

1. 在非常量的全局变量声明中， **extern**指定在另一个翻译单元中定义变量或函数。 **外部**必须应用于除了定义变量的所有文件中。
1. 在 const 变量声明中，它指定变量具有外部链接。 **Extern**必须应用于所有文件中的所有声明。 （默认情况下，全局常量变量具有内部链接。）
1. **extern "C"** 指定在其他位置定义了该函数，并使用 C 语言调用约定。 外部 "C" 修饰符也可以应用于块中的多个函数声明。
1. 在模板声明中，它指定已在其他位置实例化模板。 这是一种优化，告诉编译器它可以重新使用其他实例化，而不是在当前位置创建一个新实例。 有关此使用**extern**的详细信息，请参阅[模板](templates-cpp.md)。

## <a name="extern-linkage-for-non-const-globals"></a>非 const 全局的 extern 链接

当链接器在全局变量声明之前看到**extern**时，它将在另一个翻译单元中查找定义。 默认情况下，全局范围内的非常量变量的声明是外部的;仅将**extern**应用于未提供定义的声明。

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

## <a name="extern-linkage-for-const-globals"></a>常数全局的 extern 链接

默认情况下， **const**全局变量具有内部链接。 如果希望变量有外部链接，请将**extern**关键字应用于定义以及其他文件中的所有其他声明：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>extern constexpr 链接

在 Visual Studio 2017 版本15.3 及更早版本中，即使变量标记为 extern，编译器始终会提供一个 constexpr 变量内部链接。 在 Visual Studio 2017 版本 15.5 中，新编译器开关 ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) 启用符合标准的正确行为。 这最终将成为默认设置。 /Permissive-选项不启用/Zc： externConstexpr。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果头文件包含声明为 extern constexpr 的变量，则需要将其标记 **__declspec （selectany）** ，以便正确地将其重复的声明组合在一起：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>extern "C" 和 extern "C++" 函数声明

在C++中，当与字符串一起使用时， **extern**指定将另一种语言的链接约定用于声明符。 仅在之前被声明为具有 C 链接的情况下，才能访问 C 函数和数据。 但是，必须在单独编译的翻译单元中定义它们。

Microsoft C++ 支持字符串 **"C"** 和 **"C++"** 中*字符串文本*字段。 所有标准包含文件都使用**extern** "C" 语法，以允许在程序中C++使用运行时库函数。

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
[翻译单元和链接](program-and-linkage-cpp.md)<br/>
[C 中的 extern 存储类说明符](../c-language/extern-storage-class-specifier.md)<br/>
[C 中标识符的行为](../c-language/behavior-of-identifiers.md)<br/>
[C 中的链接](../c-language/linkage.md)