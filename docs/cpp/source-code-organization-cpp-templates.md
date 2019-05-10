---
title: 源代码组织 （C++ 模板）
ms.date: 11/04/2016
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 592f17c08b9d4de0f67f17c60521d6e9a11dfc3a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222000"
---
# <a name="source-code-organization-c-templates"></a>源代码组织 （C++ 模板）

在定义类模板时，必须组织中的成员定义时，才会对编译器可见需要的方式的源代码。   您可以使用的选择*包含模型*或*显式实例化*模型。 在包含模型中，您包括在使用模板的每个文件中的成员定义。 此方法最简单的方法，并提供了哪些具体的类型可用于在模板的最大灵活性。 其缺点在于： 它可以增加编译时间。 影响却很重要，如果一个项目和/或包含的文件较大。 使用显式实例化方法时，模板本身实例化具体类或类成员的特定类型。  这种方法可以加快编译时间，但它限制到仅提前模板实施者已经启用了这些类的使用情况。 一般情况下，我们建议使用包含模型，除非编译时间会成为问题。

## <a name="background"></a>背景

模板不是类似于普通意义上说，编译器不生成的模板或任何其成员的对象代码的类。 没有要生成，直到使用具体类型实例化模板内容。 当编译器遇到模板实例化如`MyClass<int> mc;`且未设置类使用该签名尚未存在，则它将生成一个新类。 它还将尝试为使用的任何成员函数生成代码。 如果这些定义是在文件不是 #included，直接或间接正在编译的.cpp 文件中，编译器不能看到它们。  从编译器的角度来看，这并不一定错误因为函数可能在另一个翻译单元中，在其中用例链接器会发现它们中定义。  如果链接器未找到该代码，它会发出**无法解析的外部**错误。

## <a name="the-inclusion-model"></a>包含模型

使模板定义整个翻译单元中，可见的最简单且最常见方法是将定义放入标头文件本身。  使用模板的任何.cpp 文件只是对 #include 标头。 这是使用标准库中的方法。

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

使用此方法时，编译器有权访问完整的模板定义，并可以实例化模板按需的任何类型。 很简单，相对较容易维护。 但是，包含模型确实存在成本编译时间。   此成本可能很重要大型程序时，尤其是当模板标头本身 #includes 其他标头。 每个.cpp 文件的 #includes 标头将获取其自己的函数模板和所有定义的副本。 链接器将通常能够解决问题，以便最后不与多个定义对于函数，但它需要时间来完成这项工作。 较小的程序，额外的编译时间非常可能并不重要。

## <a name="the-explicit-instantiation-model"></a>显式实例化模型

如果包含模型不是可用于你的项目，并且您完全知道的将用来实例化模板的类型集，然后可以分离出来的.h 和.cpp 文件中，将模板代码并在.cpp 文件中显式实例化模板。 这将导致对象代码生成编译器将看到当遇到用户实例化。

使用想要实例化的实体的签名后跟关键字模板创建显式实例化。 这可以是一种类型或成员。 如果您显式实例化一个类型，所有成员被实例都化。

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
    for(const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

在上一示例中，显式实例化是在.cpp 文件的底部。 一个`MyArray`可能仅为使用**双**或`String`类型。

> [!NOTE]
> 在 C++ 11**导出**关键字在模板定义的上下文中已弃用。 实际上这具有几乎不影响因为大多数编译器永远不会支持它。