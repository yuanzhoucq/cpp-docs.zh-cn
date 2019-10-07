---
title: 标头文件C++()
ms.date: 04/20/2018
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 98d37944f8c037f3ba25d80c7d35b3560ad11d40
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980476"
---
# <a name="header-files-c"></a>标头文件C++()

必须声明变量、函数、类等程序元素的名称, 然后才能使用这些元素。 例如, 不能仅在不`x = 42`首先声明 "x" 的情况下编写。

```cpp
int x; // declaration
x = 42; // use x
```

声明告知编译器元素是**int**、 **double**、**函数**、**类**还是其他一些内容。  而且, 每个名称都必须在使用该名称的每个 .cpp 文件中 (直接或间接) 声明。 编译程序时, 每个 .cpp 文件都单独编译到编译单元中。 编译器不知道哪些名称是在其他编译单元中声明的。 这意味着, 如果定义了类或函数或全局变量, 则必须在使用它的每个附加 .cpp 文件中提供该内容的声明。 所有文件中该内容的每个声明必须完全相同。 当链接器尝试将所有编译单元合并为一个程序时, 稍微不一致会导致错误或意外的行为。

为了最大限度地减少可能C++出现的错误, 已采用使用*头文件*来包含声明的约定。 在标头文件中创建声明, 然后在每个 .cpp 文件或需要该声明的其他头文件中使用 #include 指令。 在编译之前, #include 指令会将标头文件的副本直接插入到 .cpp 文件中。

## <a name="example"></a>示例

下面的示例演示了一种用于声明类, 然后在另一个源文件中使用该类的常见方法。 我们将从头文件开始, `my_class.h`。 它包含类定义, 但请注意, 定义不完整;未定义成员`do_something`函数:

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

接下来, 创建一个实现文件 (通常使用 .cpp 或类似扩展名)。 我们将调用文件 my_class, 并为成员声明提供定义。 我们为 " `#include` my_class" 文件添加了指令, 以便在此点处插入 my_class 声明, 并在的声明`std::cout`中加入`<iostream>` 。 请注意, 引号用于与源文件位于同一目录中的头文件, 而尖括号用于标准库标头。 而且, 许多标准库标头不包含 .h 或任何其他文件扩展名。

在实现文件中, 可以选择性地使用**using**语句, 以避免将 "my_class" 或 "cout" 的每个提及都限定为 "N::" 或 "std::"。  请勿在标头文件中放置**using**语句!

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

现在, 我们可以`my_class`在另一个 .cpp 文件中使用。 #Include 标头文件, 以便编译器提取声明。 所有编译器都需要知道, my_class 是一个具有名`do_something()`为的公共成员函数的类。

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

在编译器将每个 .cpp 文件编译为 .obj 文件后, 它会将 .obj 文件传递到链接器。 当链接器合并对象文件时, 它只查找 my_class 的一个定义;它在为 my_class 生成的 .obj 文件中, 并且生成成功。

## <a name="include-guards"></a>Include 临界

通常情况下, 头文件具有*include guard*或`#pragma once`指令, 以确保不会多次将它们插入到单个 .cpp 文件中。

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

因为标头文件可能由多个文件包含, 所以它不能包含可能产生同一名称的多个定义的定义。 不允许执行以下操作, 或将其视为非常糟糕的做法:

- 命名空间或全局范围内的内置类型定义
- 非内联函数定义
- 非常量变量定义
- 聚合定义
- 未命名的命名空间
- using 指令

使用**using**指令不一定会导致错误, 但可能会导致出现问题, 因为它会将命名空间引入到直接或间接包含该标头的每个 .cpp 文件的范围中。

## <a name="sample-header-file"></a>示例标头文件

下面的示例演示了标头文件中允许的各种声明和定义:

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
