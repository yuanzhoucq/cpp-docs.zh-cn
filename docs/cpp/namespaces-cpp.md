---
title: 命名空间 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- namespace_CPP
- using_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7992402d13535e2b57516e5a3481aad16256fe29
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077199"
---
# <a name="namespaces-c"></a>命名空间 (C++)

命名空间是一个声明性区域，为其内部的标识符（类型、函数和变量等的名称）提供一个范围。 命名空间用于将代码组织到逻辑组中，还可用于避免名称冲突，尤其是在基本代码包括多个库时。 命名空间范围内的所有标识符彼此可见，而没有任何限制。 命名空间之外的标识符可以通过使用为每个标识符的完全限定的名称，例如访问成员`std::vector<std::string> vec;`，也可通过[using 声明](../cpp/using-declaration.md)单个标识符 (`using std::string`)，或[using 指令](../cpp/namespaces-cpp.md#using_directives)命名空间中的所有标识符 (`using namespace std;`)。 头文件中的代码应始终使用完全限定的命名空间名称。

下面的示例演示了一个命名空间声明和命名空间之外的代码可访问其成员的三种方法。

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

使用完全限定名：

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

使用 using 声明，以将一个标识符引入范围：

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

使用 using 指令，以将命名空间中的所有内容引入范围：

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a id="using_directives"></a> using 指令

**使用**指令允许中的所有名称**命名空间**若要使用不带*命名空间名称*为显式限定符。 使用 using 指令在实现文件 (即 *.cpp) 如果在命名空间; 使用多个不同的标识符如果只需要使用一个或两个标识符，请考虑使用声明，以仅将这些标识符到作用域中，并不是所有标识符的命名空间中。 如果本地变量的名称与命名空间变量的名称相同，则隐藏命名空间变量。 使命名空间变量具有与全局变量相同的名称是错误的。

> [!NOTE]
>  using 指令可以放置在 .cpp 文件的顶部（在文件范围内），或放置在类或函数定义内。
>
>  一般情况下，避免将 using 指令放置在头文件 (*.h) 中，因为任何包含该标头的文件都会将命名空间中的所有内容引入范围，这将导致非常难以调试的名称隐藏和名称冲突问题。 在头文件中，始终使用完全限定名。 如果这些名称太长，可以使用命名空间别名将其缩短。 （请参阅下文。）

## <a name="declaring-namespaces-and-namespace-members"></a>声明命名空间和命名空间成员

通常情况下，在头文件中声明一个命名空间。 如果函数实现位于一个单独的文件中，则限定函数名称，如本示例所示。

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Contosodata.cpp 中的函数实现应使用完全限定的名称，即使将**使用**指令置于文件顶部：

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

可以在单个文件中的多个块中声明命名空间，也可在多个文件中声明命名空间。 编译器在预处理过程中将各部分联接在一起，产生的命名空间中包含所有部分中声明的所有成员。 一个相关示例是在标准库中的每个头文件中声明的 std 命名空间。

可以通过显式限定所定义的名称的声明的命名空间外定义命名的命名空间的成员。 但是，定义必须出现在命名空间中的声明位置之后，该命名空间包含在声明的命名空间中。 例如：

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
        void f();
    }

    void V::f() { }        // ok
    void V::g() { }        // C2039, g() is not yet a member of V

    namespace V {
        void g();
    }
}
```

当跨多个头文件声明命名空间成员，并且未以正确的顺序包含这些标头时，可能出现此错误。

## <a name="the-global-namespace"></a>全局命名空间

如果未在显式命名空间中声明某个标识符，则该标识符属于隐式全局命名空间的一部分。 一般情况下，尝试避免创建在全局范围内，如果可能，除了入口点的声明[主函数](../c-language/main-function-and-program-execution.md)，这必须是全局命名空间中。 若要显式限定全局标识符，请使用没有名称的范围解析运算符，如 `::SomeFunction(x);` 中所示。 这将使标识符与任何其他命名空间中具有相同名称的任何内容区分开来，并且还有助于使其他人更轻松地了解你的代码。

## <a name="the-std-namespace"></a>Std 命名空间

所有 C++ 标准库类型和函数声明中`std`命名空间或命名空间嵌套`std`。

## <a name="nested-namespaces"></a>嵌套命名空间

可以嵌套命名空间。 普通的嵌套命名空间具有对其父级成员的非限定访问权限，而父成员不具有对嵌套命名空间的非限定访问权限（除非它被声明为内联），如下面的示例所示：

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

普通嵌套命名空间可用于封装不属于父命名空间的公共接口的一部分的内部实现详细信息。

## <a name="inline-namespaces-c-11"></a>内联命名空间 (C++ 11)

与普通嵌套命名空间不同，内联命名空间的成员会被视为父命名空间的成员。 这一特性使针对重载函数的依赖于参数的查找可以对父命名空间和嵌套内联命名空间中具有重载的函数起作用。 它还可让你在内联命名空间中声明的模板的父命名空间中声明专用化。 下面的示例演示在默认情况下，外部代码如何绑定到内联命名空间：

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

下面的示例演示如何在内联命名空间中声明的模板的父命名空间中声明专用化：

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

可以将内联命名空间用作版本控制机制，以管理对库的公共接口的更改。 例如，可以创建单个父命名空间，并将接口的每个版本封装到嵌套在父命名空间内的其自己的命名空间中。 保留最新或首选的版本的命名空间限定为内联，并因此以父命名空间的直接成员的形式公开。 调用 Parent::Class 的客户端代码将自动绑定到新代码。 通过使用指向包含该代码的嵌套命名空间的完全限定路径，选择使用较旧版本的客户端仍可以对其进行访问。

Inline 关键字必须应用到编译单元中命名空间的第一个声明中。

下面的示例演示一个接口的两个版本，每个版本位于一个嵌套命名空间中。 通过 `v_10` 接口对 `v_20` 命名空间进行了某些修改，且该命名空间被标记为内联。 使用新库并调用 `Contoso::Funcs::Add` 的客户端代码将调用 v_20 版本。 尝试调用 `Contoso::Funcs::Divide` 的代码现在将获取一个编译时错误。 如果它们确实需要该函数，则仍可以通过显式调用 `Contoso::v_10::Funcs::Divide` 访问 `v_10` 版本。

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a id="namespace_aliases"></a> Namespace 别名

命名空间名称必须是唯一的，这意味着通常它们不应太短。 如果名称的长度使代码难以阅读，或在不能使用 using 指令的头文件中进行键入单调乏味，则可以使用用作实际名称的缩写的命名空间别名。 例如：

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>匿名或未命名的命名空间

可以创建显式命名空间，但不为其提供一个名称：

```cpp
namespace
{
    int MyFunc(){}
}
```

这称为未命名或匿名命名空间，当你想要使其他文件中的变量声明对代码不可见时非常有用 （即为他们提供内部链接） 而无需创建一个命名的命名空间。 同一文件中的所有代码都可以看到未命名的命名空间中的标识符，但这些标识符以及命名空间本身在该文件外部（或更准确地说，在翻译单元外部）不可见。

## <a name="see-also"></a>请参阅

[声明和定义](declarations-and-definitions-cpp.md)