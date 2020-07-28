---
title: 源代码组织（C++ 模板）
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: ecd682056f27200ae31c27295c1aabaf72c74a18
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186108"
---
# <a name="source-code-organization-c-templates"></a>源代码组织（C++ 模板）

在定义类模板时，必须以这样一种方式组织源代码：在编译器需要成员定义时，可以看到成员定义。 可以选择使用包含模型** 或显式实例化** 模型。 在包含模型中，您在使用模板的每个文件中都包含成员定义。 这是最简单的方法，它在可与模板一起使用的具体类型方面提供了最大的灵活性。 缺点是会增加编译时间。 如果项目和/或包含的文件本身很大，那么影响可能很大。 使用显式实例化方法，模板本身会实例化特定类型的具体类或类成员。  此方法可以加快编译时间，但它仅限于模板实现者提前启用的那些类的使用情况。 通常，我们建议使用包含模型，除非由于编译时间问题而存在局限性。

## <a name="background"></a>背景

模板与普通类不同，因为编译器不会为模板或其任何成员生成对象代码。 在使用具体类型实例化模板之前，不会生成任何内容。 当编译器遇到模板实例化（例如 `MyClass<int> mc;`）并且尚未存在具有该签名的类时，它将生成一个新类。 它还会尝试为使用的任何成员函数生成代码。 如果这些定义位于一个并未直接或间接 #included 在正在编译的 .cpp 文件内的文件中，则编译器无法看到它们。  从编译器的角度来看，这不一定是错误，因为函数可能在另一个翻译单元中定义，在这种情况下，链接器将可以找到它们。  如果链接器找不到该代码，则会引发无法解析的外部** 错误。

## <a name="the-inclusion-model"></a>包含模型

使模板定义在整个翻译单元中可见的最简单、最常见的方法是将定义放入头文件本身。  使用模板的任何 .cpp 文件只需 #include 标头。 这是标准库中使用的方法。

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   }
};
#endif
```

使用此方法时，编译器可以访问完整的模板定义，并可根据需要为任何类型实例化模板。 这很简单，而且相对容易维护。 但是，包含模型确实存在编译时间成本。 在大型程序中，此类成本可能很高，尤其是在模板标头本身 #include 其他标头的情况下。 *`.cpp`*#Includes 标头的每个文件都将获取其自己的函数模板和所有定义的副本。 链接器通常能够解决问题，这样最终便不会得到函数的多个定义，但是完成这项工作需要时间。 在较小的程序中，可能不需要太长的额外编译时间。

## <a name="the-explicit-instantiation-model"></a>显式实例化模型

如果包含模型对于您的项目是不可行的，并且您明确知道将用于实例化模板的类型集，则可以将模板代码分开到 *`.h`* 和 *`.cpp`* 文件中，并在 *`.cpp`* 文件中显式实例化模板。 这将导致生成编译器在遇到用户实例化时将看到的对象代码。

通过使用关键字模板，然后使用要实例化的实体的签名，创建显式实例化。 这可以是类型或成员。 如果显式实例化类型，则会实例化所有成员。

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for (const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

在前面的示例中，显式实例化位于 .cpp 文件的底部。 `MyArray`只能用于 **`double`** 或 `String` 类型。

> [!NOTE]
> 在 c + + 11 中， **`export`** 关键字已在模板定义的上下文中弃用。 实际上，这几乎没有影响，因为大多数编译器从不支持它。
