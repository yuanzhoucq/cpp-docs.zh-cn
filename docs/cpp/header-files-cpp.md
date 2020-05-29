---
title: 标题文件 （C++）
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367230"
---
# <a name="header-files-c"></a>标题文件 （C++）

在使用变量、函数、类等之前，必须声明程序元素的名称。 例如，不能只写`x = 42`而不首先声明"x"。

```cpp
int x; // declaration
x = 42; // use x
```

声明告诉编译器该元素是**int、****双组**、**函数**、**类**还是其他内容。  此外，必须在使用每个 .cpp 的文件中（直接或间接）声明每个名称。 编译程序时，每个 .cpp 文件将独立编译为编译单元。 编译器不知道在其他编译单元中声明的名称。 这意味着，如果定义类或函数或全局变量，则必须在使用它的每个附加 .cpp 文件中提供该事物的声明。 该事物的每个声明在所有文件中必须完全相同。 当链接器尝试将所有编译单元合并到单个程序中时，轻微的不一致将导致错误或意外行为。

为了将错误的可能性降至最低，C++采用了使用*标头文件*来包含声明的惯例。 在标头文件中创建声明，然后在每个 .cpp 文件或其他需要该声明的标头文件中使用#include指令。 #include指令在编译前将头文件的副本直接插入到 .cpp 文件中。

> [!NOTE]
> 在 Visual Studio 2019 中，C++20*模块*功能作为改进和最终替换头文件引入。 有关详细信息，请参阅[C++ 中的模块概述](modules-cpp.md)。

## <a name="example"></a>示例

下面的示例显示了一种声明类，然后在其他源文件中使用它的常见方法。 我们将从头文件开始。 `my_class.h` 它包含类定义，但请注意该定义不完整;未定义成员`do_something`函数：

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

接下来，创建一个实现文件（通常使用 .cpp 或类似扩展名）。 我们将调用文件my_class.cpp，并为成员声明提供定义。 我们添加"my_class.h"文件的`#include`指令，以便将 my_class 声明插入 .cpp 文件中的此时，并且我们包括在`<iostream>``std::cout`中拉取 声明。 请注意，引号用于与源文件位于同一目录中的标头文件，角度括号用于标准库标头。 此外，许多标准库标头没有 .h 或任何其他文件扩展名。

在实现文件中，我们可以选择使用**using**语句，以避免每次提及"my_class"或"cout"与"N：："或"std："进行限定。  不要把**使用**语句放在你的头文件中！

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

现在，我们可以在另`my_class`一个 .cpp 文件中使用。 我们#include头文件，以便编译器在声明中提取。 编译器需要知道的是，my_class是一个具有公共成员函数的类`do_something()`。

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

编译器完成将每个 .cpp 文件编译到 .obj 文件中后，它将 .obj 文件传递给链接器。 当链接器合并对象文件时，它正好找到my_class一个定义;当链接器合并对象文件时，它将找到一个定义，用于my_class。它位于为 my_class.cpp 生成的 .obj 文件中，生成成功。

## <a name="include-guards"></a>包括护卫

通常，标头文件具有*包含防护*或`#pragma once`指令，以确保它们不会多次插入到单个 .cpp 文件中。

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

## <a name="what-to-put-in-a-header-file"></a>在头文件中放入什么

由于头文件可能由多个文件包含，因此它不能包含可能产生同名多个定义的定义。 不允许使用以下操作，或被视为非常糟糕的做法：

- 命名空间或全局作用域的内置类型定义
- 非内联函数定义
- 非同义变量定义
- 聚合定义
- 未命名的命名空间
- using 指令

**使用 using**指令不一定会导致错误，但可能会导致问题，因为它会将命名空间引入直接或间接包含该标头的每个 .cpp 文件中的范围。

## <a name="sample-header-file"></a>示例头文件

下面的示例显示了标头文件中允许的各种声明和定义：

```cpp
// sample.h
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
