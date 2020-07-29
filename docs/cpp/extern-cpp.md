---
title: ':::no-loc(extern)::: (C++)'
description: 'C + + 语言 :::no-loc(extern)::: 关键字指南。'
ms.date: 01/28/2020
f1_keywords:
- ':::no-loc(extern):::'
- :::no-loc(extern):::_CPP
helpviewer_keywords:
- ':::no-loc(extern)::: keyword [C++], linkage to non-C++ functions'
- declarations, :::no-loc(extern):::al
- ':::no-loc(extern):::al linkage, :::no-loc(extern)::: modifier'
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- ':::no-loc(extern):::'
- ':::no-loc(const):::'
- ':::no-loc(constexpr):::'
- ':::no-loc(permissive):::'
ms.openlocfilehash: 510352f9e99e513f4a426f6ef89be4474085d97c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227499"
---
# <a name="no-locextern-c"></a>:::no-loc(extern)::: (C++)

**`:::no-loc(extern):::`** 关键字可应用于全局变量、函数或模板声明。 它指定该符号具有* :::no-loc(extern)::: al 链接*。 有关链接的背景信息和不鼓励使用全局变量的原因，请参阅[翻译单元和链接](program-and-linkage-cpp.md)。

**`:::no-loc(extern):::`** 关键字有四种含义，具体取决于上下文：

- 在非 **`:::no-loc(const):::`** 全局变量声明中， **`:::no-loc(extern):::`** 指定在其他翻译单元中定义变量或函数。 **`:::no-loc(extern):::`** 必须应用于除了定义变量的所有文件中。

- 在 **`:::no-loc(const):::`** 变量声明中，它指定变量具有 :::no-loc(extern)::: al 链接。 **`:::no-loc(extern):::`** 必须应用于所有文件中的所有声明。 （ **`:::no-loc(const):::`** 默认情况下，全局变量具有内部链接。）

- ** :::no-loc(extern)::: "C"** 指定在其他位置定义函数并使用 C 语言调用约定。 :::no-loc(extern):::"C" 修饰符也可以应用于块中的多个函数声明。

- 在模板声明中， **`:::no-loc(extern):::`** 指定模板已在其他位置实例化。 **`:::no-loc(extern):::`** 告诉编译器它可以重复使用另一个实例化，而不是在当前位置创建新的实例化。 有关此用法的详细信息 **`:::no-loc(extern):::`** ，请参阅[显式实例化](explicit-instantiation.md)。

## <a name="no-locextern-linkage-for-non-no-locconst-globals"></a>:::no-loc(extern):::非全局的链接 :::no-loc(const):::

当链接器在 **`:::no-loc(extern):::`** 全局变量声明之前查看时，它将在另一个翻译单元中查找定义。 **`:::no-loc(const):::`** 默认情况下，全局范围内的非变量声明为 :::no-loc(extern)::: al。 仅适用于 **`:::no-loc(extern):::`** 未提供定义的声明。

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileC.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
:::no-loc(extern)::: int i = 43; // same error (:::no-loc(extern)::: is ignored on definitions)
```

## <a name="no-locextern-linkage-for-no-locconst-globals"></a>:::no-loc(extern):::适用于 :::no-loc(const)::: globals 的链接

**`:::no-loc(const):::`** 全局变量默认具有内部链接。 如果希望变量具有 :::no-loc(extern)::: al 链接，请将关键字应用于 **`:::no-loc(extern):::`** 定义，并将其应用于其他文件中的所有其他声明：

```cpp
//fileA.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i = 42; // :::no-loc(extern)::: :::no-loc(const)::: definition

//fileB.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i;  // declaration only. same as i in FileA
```

## <a name="no-locextern-no-locconstexpr-linkage"></a>:::no-loc(extern)::::::no-loc(constexpr):::链接

在 Visual Studio 2017 版本15.3 及更早版本中，编译器始终提供 **`:::no-loc(constexpr):::`** 变量内部链接，即使该变量已标记 **`:::no-loc(extern):::`** 。 在 Visual Studio 2017 版本15.5 及更高版本中， [/zc： :::no-loc(extern)::: Constexpr](../build/reference/zc-:::no-loc(extern)::::::no-loc(constexpr):::.md)编译器开关实现了符合标准的正确行为。 最终，选项将成为默认值。 [/:::no-loc(permissive):::-](../build/reference/:::no-loc(permissive):::-standards-conformance.md)选项不启用 **/Zc： :::no-loc(extern)::: Constexpr**。

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: int x = 10; //error LNK2005: "int :::no-loc(const)::: x" already defined
```

如果标头文件包含已声明的变量 **`:::no-loc(extern):::`** **`:::no-loc(constexpr):::`** ，则必须将其标记 `__declspec(selectany)` 为正确地将其重复的声明组合在一起：

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: __declspec(selectany) int x = 10;
```

## <a name="no-locextern-c-and-no-locextern-c-function-declarations"></a>:::no-loc(extern):::"C" 和 :::no-loc(extern)::: "c + +" 函数声明

在 c + + 中，当与字符串一起使用时， **`:::no-loc(extern):::`** 指定将另一种语言的链接约定用于声明符。 仅当 c 函数和数据以前已声明为具有 C 链接时，才能访问这些函数和数据。 但是，必须在单独编译的翻译单元中定义它们。

Microsoft c + + 支持*字符串文本*字段中的字符串 **"c"** 和 **"c + +"** 。 所有标准包含文件都使用** :::no-loc(extern)::: "C"** 语法，以允许在 c + + 程序中使用运行时库函数。

## <a name="example"></a>示例

下面的示例演示如何声明具有 C 链接的名称：

```cpp
// Declare printf with C linkage.
:::no-loc(extern)::: "C" int printf(:::no-loc(const)::: char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
:::no-loc(extern)::: "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
:::no-loc(extern)::: "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
:::no-loc(extern)::: "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

:::no-loc(extern)::: "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
:::no-loc(extern)::: "C" int errno;
```

如果函数有多个链接规范，则必须同意。 使用 C 和 c + + 链接声明函数是错误的。 此外，如果一个函数的两个声明出现在一个程序中，并且它们一个有链接规范，另一个没有，则有链接规范的声明必须是第一个。 将为已具有链接规范的函数的所有冗余声明提供第一个声明中指定的链接。 例如：

```cpp
:::no-loc(extern)::: "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
:::no-loc(extern)::: "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>另请参阅

[字](../cpp/keywords-cpp.md)\
[翻译单元和链接](program-and-linkage-cpp.md)\
[:::no-loc(extern):::C 中的存储类说明符](../c-language/:::no-loc(extern):::-storage-class-specifier.md)\
[C 中标识符的行为](../c-language/behavior-of-identifiers.md)\
[C 中的链接](../c-language/linkage.md)
