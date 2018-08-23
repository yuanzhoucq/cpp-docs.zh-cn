---
title: 标头文件 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be194095b6461eaedd9e814c6130801b431fef5d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602408"
---
# <a name="header-files-c"></a>标头文件 （c + +）

必须声明变量、 函数、 类等的程序元素的名称，然后才能使用。 例如，你不能只需编写`x = 42`而无需第一个声明 x。 

```cpp
int x; // declaration
x = 42; // use x
```

 声明会告知编译器是否是**int**、 **double**即**函数**、**类**或一些其他事情。  此外，每个名称必须声明 （直接或间接） 在每个.cpp 文件中使用它。 当编译的程序时，每个.cpp 文件单独编译到编译单元。 编译器并不知道哪些名称在其他编译单元中声明。 这意味着，如果你定义类或函数或全局变量，你必须提供在使用它的每个其他.cpp 文件中的该操作的声明。 该操作的每个声明中的所有文件必须完全相同。 当链接器尝试将所有编译单元都合并为单个程序时，略微不一致将导致错误或意外的行为。

为了尽量减少出错的危险，c + + 已采用使用的约定*标头文件*包含声明。 在标头文件中，进行声明，然后使用 #include 指令中的每个.cpp 文件或其他标头文件所需的声明。 #Include 指令插入标头文件的副本直接在之前编译的.cpp 文件。 

## <a name="example"></a>示例

下面的示例演示声明一个类，然后使用它在不同源文件中的常用方法。 我们将开始标头文件中， `my_class.h`。 它包含类定义，但请注意，定义不完整;成员函数`do_something`未定义：

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

接下来，创建实现文件 （通常具有.cpp 或类似的扩展）。 我们将调用文件 my_class.cpp 并提供成员声明的定义。 我们将添加`#include`指令"my_class.h"文件，以便具有插入 my_class 声明，此时在.cpp 文件中，和我们包括`<iostream>`的声明中提取`std::cout`。 请注意，与源文件相同的目录中的标头文件中用引号将尖括号用于标准库标头。 此外，许多标准库标头有.h 或任何其他文件扩展名。

在实现文件中，我们可以选择使用**使用**语句以避免无需限定每个提及"my_class"或"cout"与"n::"或"std::"。  请勿在放入**使用**标头文件中的语句 ！

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

现在我们可以使用`my_class`另一个.cpp 文件中。 我们 #include 标头文件，以便编译器中提取的声明中。 所有编译器需要知道是否该 my_class 是具有一个名为的公共成员函数的类， `do_something()`。

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

编译器完成每个.cpp 文件编译到.obj 文件后，它将链接器传递.obj 文件。 链接器的对象文件合并时它找到一个定义 my_class;它是针对 my_class.cpp，生成的.obj 文件中，生成成功。

## <a name="include-guards"></a>包含保护

通常情况下，标头文件具有*include 防护*或`#pragma once`指令以确保，它们不会插入多个时间到单一的.cpp 文件。 

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

## <a name="what-to-put-in-a-header-file"></a>要放置在头文件中的内容

由于可能可能由多个文件都包括标头文件，它不能包含可能会生成具有相同名称的多个定义的定义。 以下不允许，或被视为非常不良实践：

- 在命名空间或全局范围的内置类型定义
- 非内联函数定义 
- 非常量变量定义
- 聚合的定义
- 未命名的命名空间
- using 指令

利用**使用**指令一定不会导致错误，但可能会出现问题，因为它将命名空间引入作用域中直接或间接包含该标头的每个.cpp 文件。 

## <a name="sample-header-file"></a>示例标头文件

下面的示例显示了各种类型的声明和定义允许的标头文件：

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