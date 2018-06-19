---
title: 源代码组织 （C++ 模板） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 05a5b0423b79e817e16aeb0d39f1d0dcf856c1ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423111"
---
# <a name="source-code-organization-c-templates"></a>源代码组织 （C++ 模板）

在定义类模板时，必须将组织中需要它们时，此成员定义对编译器可见的方式的源代码。   你可以选择使用*包含模型*或*显式实例化*模型。 在包含模型中，你将包括使用模板的每个文件中的成员定义。 此方法是最简单的并提供可与你的模板使用何种具体类型方面的最大灵活性。 其缺点是它会增加了编译次数。 影响可显著如果一个项目和/或包含的文件本身较大。 借助显式实例化的方法，具体类或类成员的特定类型实例化该模板本身。  这种方法可以提高了编译时间，但是它限制了使用情况与仅模板实施者已提前启用这些类。 通常情况下，我们建议你使用包含模型，除非编译时间会成为问题。

## <a name="background"></a>背景

模板不是像普通类在编译器不生成模板或任何其成员的对象代码的意义上一样。 无需进行任何生成模板实例化具体类型使用之前。 当编译器遇到为模板实例化如`MyClass<int> mc;`并且没有任何使用该签名的类尚未存在，则它将生成一个新类。 它还将尝试为其生成代码使用的任何成员函数。 这些定义是否在文件不是 #included，直接或间接在.cpp 文件正在编译，编译器无法看到它们。  从编译器的角度来看，这不一定是错误原因可能在另一个翻译单元中，在其中用例链接器将找到它们中定义的函数。  如果链接器找不到该代码，它会引发**无法解析的外部**错误。

## <a name="the-inclusion-model"></a>包含模型

使模板定义在翻译单元中，整个可见的最简单也是最常见方法是将定义放入标头文件本身。  使用模板的任何.cpp 文件只需对所拥有 #include 标头。 这是在标准库中使用的方法。

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

使用此方法时，编译器将有权访问的完整的模板定义，以及可以实例化模板按需为任何类型。 很简单，相对较容易维护。 但是，包含模型不必在编译时间方面的成本。   此成本可能很重要在较大程序中，尤其是如果本身的模板标头 #includes 其他标头。 每个.cpp 文件 #includes 标头将获得自己的函数模板和所有定义的副本。 通常，链接器能够理清操作，以便你没有停止与多个定义的函数，但它需要时间来完成此工作。 较小的程序额外的编译时间并可能不重要。

## <a name="the-explicit-instantiation-model"></a>显式实例化模型

如果包含模型是不可行的为你的项目，并且您知道明确的将用来实例化模板的类型集，然后可以分离出的模板代码到.h 和.cpp 文件，并在.cpp 文件中显式实例化模板。 编译器将看到它在遇到用户实例化时，这将导致要生成对象代码。

使用你想要实例化的实体签名后跟关键字模板创建的显式实例化。 这可以是一种类型或成员。 如果你显式实例化一个类型，所有成员被实例都化。

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
#include "stdafx.h"
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

在前面的示例中，显式实例化位于.cpp 文件的底部。 A`MyArray`可能仅可用于**double**或**字符串**类型。

> [!NOTE]
> 在 C++ 11**导出**关键字在模板定义的上下文中已弃用。 在实际情况下，则此项影响很小因为大多数编译器永远不会支持它。
