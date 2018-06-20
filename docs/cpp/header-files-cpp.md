---
title: 标头文件 （c + +） |Microsoft 文档
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261043"
---
# <a name="header-files-c"></a>标头文件 （c + +）

必须声明的变量、 函数、 类等的程序元素的名称后，才可以使用。 例如，你不能只是编写`x = 42`不必先声明 x。 

```cpp
int x; // declaration
x = 42; // use x
```

 声明告知编译器是否是**int**、 **double**、**函数**、**类**或一些其他操作。  此外，每个名称必须声明 （直接或间接） 在每个.cpp 文件中使用它。 当你编译的程序时，每个.cpp 文件会独立编译成编译单元中。 编译器都必须在其他编译单元中声明的哪些名称并不知道。 这意味着，如果你定义的类或函数或全局变量，你必须提供该事物使用它的每个其他的.cpp 文件中的声明。 该事物的每个声明的所有文件中必须是完全相同的。 链接器尝试将所有的编译单元合并到单个程序时，稍有不一致将导致错误或意外的行为。

为了尽量减少错误的可能性，c + + 已采用使用的约定*标头文件*以包含声明。 在标头文件中，进行声明，则使用 #include 指令中的每个.cpp 文件或其他标头文件要求该声明。 #Include 指令插入标头文件的副本直接在编译之前的.cpp 文件。 

## <a name="example"></a>示例

下面的示例演示声明一个类，然后使用它在不同源文件中的常用方法。 标头文件中，我们将从开始**my_class.h**。 它包含类定义，但请注意该定义不完整;成员函数`do_something`未定义：

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

接下来，创建一个实现文件 （通常具有.cpp 或类似的扩展）。 我们将调用文件 my_class.cpp，并提供成员声明的定义。 我们添加`#include`针对"my_class.h"文件，该文件具有 my_class 声明插入的指令，此时在.cpp 文件，和我们包括 **\<iostream >** 以提取的声明`std::cout`。 请注意引号用于源文件所在的目录中的标头文件和命令的尖括号用于标准库头文件。 此外，许多标准库头文件没有.h 或任何其他文件扩展名。

在实现文件中，我们可以选择使用**使用**语句以避免与无需限定"my_class"或"cout"每个提及"n::"或"std::"。  不要拖延**使用**标头文件中的语句 ！

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

现在我们可以使用`my_class`另一个在.cpp 文件中。 我们 #include 标头文件，以便编译器将在声明中拉取。 所有编译器需要知道是否为该 my_class 是具有调用的公共成员函数的类`do_something()`。

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

编译器完成编译到.obj 文件中的每个.cpp 文件后，它将的.obj 文件传递到链接器。 当链接器会对象文件合并它会查找恰好一个定义 my_class;它是针对 my_class.cpp，生成的.obj 文件中，成功生成。

## <a name="include-guards"></a>Include 防护

通常，标头文件具有*include 防护*或 **#pragma 一次**指令以确保，它们不会插入多次到单个.cpp 文件。 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>ifndef MY_CLASS_H / / include 防护
#<a name="define-myclassh"></a>定义 MY_CLASS_H


命名空间 N {类 my_class {公共： void do_something();};

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>要放置在头文件中的内容

标头文件可能可能包括受多个文件中，因为它不能包含可能会产生相同的名称的多个定义的定义。 以下不允许，或将被视为非常不好的做法：

- 在命名空间或全局范围的内置类型定义
- 非内联函数定义 
- 非常量变量定义
- 聚合的定义
- 未命名的命名空间
- using 指令

利用**使用**指令不一定导致错误，但可能会导致问题，因为它引入命名空间范围直接或间接包含该标头每个.cpp 文件中。 

## <a name="sample-header-file"></a>示例标头文件

下面的示例演示了各种类型的声明和标头文件中允许的定义：

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
