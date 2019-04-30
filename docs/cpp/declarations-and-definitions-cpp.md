---
title: 声明和定义 (C++)
ms.date: 11/04/2016
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 1e76f636a6efd652ac629ad2f97f0b09f6171f9c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399065"
---
# <a name="declarations-and-definitions-c"></a>声明和定义 (C++)

声明引入名称在程序中，例如变量、 命名空间、 函数和类的名称。 声明还指定了类型信息以及正在声明的对象的其他特征。 必须声明一个名称，然后才能进行使用；C++ 中在声明名称的位置确定其是否对编译器可见。 您不能引用函数或在编译单元中; 在以后某个时刻声明的类可以使用*的前向声明*避开此限制。

定义指定代码或数据名称描述。 编译器需要定义，以为所声明的操作分配存储空间。

## <a name="declarations"></a>声明

声明将一个或多个名称引入程序中。 声明可以在一个程序中发生多次。 因此，可以为每个编译单元声明类、结构、枚举类型和其他用户定义的类型。 此多次声明的约束为所有声明必须相同。 声明还充当定义，除非声明：

1. 是函数原型（没有函数体的函数声明）。

1. 包含**extern**说明符，但没有初始值设定项 （对象和变量） 或函数体 （函数）。 这表明定义不一定在当前翻译单元中并提供名称外部链接。

1. 是类声明中的静态数据成员。

   由于静态类数据成员是类的所有对象所共享的分离变量，因此必须在类声明的外部对它们进行定义和初始化。 (有关类和类成员的详细信息，请参阅[类](../cpp/classes-and-structs-cpp.md)。)

1. 是没有下列定义的类名声明，例如 `class T;`。

1. 是**typedef**语句。

同时作为定义的声明的示例为：

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
            Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

不是定义的某些声明为：

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

名称被视为在紧靠其声明符之后，但位于其（可选）初始值设定项之前的位置进行声明。 有关详细信息，请参阅[声明点](../cpp/point-of-declaration-in-cpp.md)。

声明出现在*作用域*。 范围控制已声明的名称的可见性和已定义的对象的持续时间（如果有）。 有关范围规则如何与声明进行交互的详细信息，请参阅[作用域](../cpp/scope-visual-cpp.md)。

对象声明也是一种定义，除非它包含**extern**中所述的存储类说明符[存储类](storage-classes-cpp.md)。 函数声明也可作为定义，除非它为原型。 原型是没指有定义的函数体的函数头。 对象的定义会对该对象导致存储的分配以及相应的初始化。

## <a name="definitions"></a>定义

定义是对象、变量、函数、类或枚举数的唯一规范。 由于定义必须是唯一的，因此程序只能包含一个给定程序元素的定义。 声明和定义之间可存在多对一的对应关系。 在两种情况下，可声明但不定义程序元素：

1. 声明函数，但决不将其与函数调用或采用函数地址的表达式一起引用。

1. 只能通过无需知道其定义的方式使用类。 但是，必须声明该类。 下面的代码阐释了这样的情况：

    ```cpp
    // definitions.cpp
    class WindowCounter;   // Forward declaration; no definition

    class Window
    {
       // Definition of WindowCounter not required
       static WindowCounter windowCounter;
    };

    int main()
    {
    }
    ```

## <a name="see-also"></a>请参阅

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
[声明点](../cpp/point-of-declaration-in-cpp.md)