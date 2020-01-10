---
title: 标头文件C++（）
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: ca5036ee53372f44e53b5a6452d4ab220fc3977d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301478"
---
# <a name="header-files-c"></a>标头文件C++（）

必须声明变量、函数、类等程序元素的名称，然后才能使用这些元素。 例如，不能只是在没有首先声明 "x" 的情况下编写 `x = 42`。

```cpp
int x; // declaration
x = 42; // use x
```

声明告知编译器元素是**int**、 **double**、**函数**、**类**还是其他一些内容。  而且，每个名称都必须在使用该名称的每个 .cpp 文件中（直接或间接）声明。 编译程序时，每个 .cpp 文件都单独编译到编译单元中。 编译器不知道哪些名称是在其他编译单元中声明的。 这意味着，如果定义了类或函数或全局变量，则必须在使用它的每个附加 .cpp 文件中提供该内容的声明。 所有文件中该内容的每个声明必须完全相同。 当链接器尝试将所有编译单元合并为一个程序时，稍微不一致会导致错误或意外的行为。

为了最大限度地减少可能C++出现的错误，已采用使用*头文件*来包含声明的约定。 在标头文件中创建声明，然后在每个 .cpp 文件或需要该声明的其他头文件中使用 #include 指令。 在编译之前，#include 指令会将标头文件的副本直接插入到 .cpp 文件中。

> [!NOTE]
> 在 Visual Studio 2019 中，c + + 20*模块*功能被引入为标头文件的改进和最终替换。 有关详细信息，请参阅[ C++中模块概述](modules-cpp.md)。

## <a name="example"></a>示例

下面的示例演示了一种用于声明类，然后在另一个源文件中使用该类的常见方法。 我们将从头文件开始，`my_class.h`。 它包含类定义，但请注意，定义不完整;未定义成员函数 `do_something`：

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

接下来，创建一个实现文件（通常使用 .cpp 或类似扩展名）。 我们将调用文件 my_class .cpp 并为成员声明提供定义。 我们添加了 "my_class" 文件的 `#include` 指令，以便在此点处插入 my_class 声明，并将 `<iostream>` 纳入 `std::cout`的声明中。 请注意，引号用于与源文件位于同一目录中的头文件，而尖括号用于标准库标头。 而且，许多标准库标头不包含 .h 或任何其他文件扩展名。

在实现文件中，可以选择性地使用**using**语句，以避免让 "my_class" 或 "cout" 的每个提到 "N：：" 或 "std：："。  请勿在标头文件中放置**using**语句！

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

现在，我们可以在另一个 .cpp 文件中使用 `my_class`。 #Include 标头文件，以便编译器提取声明。 所有编译器都需要知道，my_class 是一个具有名为 `do_something()`的公共成员函数的类。

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

在编译器将每个 .cpp 文件编译为 .obj 文件后，它会将 .obj 文件传递到链接器。 当链接器合并对象文件时，它只查找 my_class 的一个定义;它位于为 my_class 生成的 .obj 文件中，并且生成成功。

## <a name="include-guards"></a>Include 临界

通常情况下，头文件具有*include guard*或 `#pragma once` 指令，以确保不会多次将它们插入单个 .cpp 文件中。

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>要放置在标头文件中的内容

因为标头文件可能由多个文件包含，所以它不能包含可能产生同一名称的多个定义的定义。 不允许执行以下操作，或将其视为非常糟糕的做法：

- 命名空间或全局范围内的内置类型定义
- 非内联函数定义
- 非常量变量定义
- 聚合定义
- 未命名的命名空间
- using 指令

使用**using**指令不一定会导致错误，但可能会导致出现问题，因为它会将命名空间引入到直接或间接包含该标头的每个 .cpp 文件的范围中。

## <a name="sample-header-file"></a>示例标头文件

下面的示例演示了标头文件中允许的各种声明和定义：

```cpp
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
