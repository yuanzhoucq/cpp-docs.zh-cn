---
title: 类成员概述
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 02c5593d9fb5e72ee6b398c9637397ab26c9f3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229059"
---
# <a name="class-member-overview"></a>类成员概述

类或结构由其成员组成。 类的工作由其成员函数执行。 它所维持的状态存储在其数据成员中。 成员的初始化由构造函数完成，而清理工作（如释放内存和释放资源由析构函数完成）。 在 C++ 11 和更高版本中，数据成员可以（并且通常应该）在声明时初始化。

## <a name="kinds-of-class-members"></a>类成员的种类

成员类别的完整列表如下：

- [特殊成员函数](special-member-functions.md)。

- [成员函数的概述](overview-of-member-functions.md)。

- 包含内置类型和其他用户定义类型的[数据成员](static-members-cpp.md)。

- 运算符

- [嵌套类声明](nested-class-declarations.md)和。）

- [Unions](unions.md)

- [枚举](../cpp/enumerations-cpp.md)。

- [位域](../cpp/cpp-bit-fields.md)。

- [朋友](../cpp/friend-cpp.md)。

- [别名和 typedef](../cpp/aliases-and-typedefs-cpp.md)。

    > [!NOTE]
    >  前面的列表中包括友元，因为它们包含在类声明中。 但是，它们不是真正的类成员，因为它们不在类范围内。

## <a name="example-class-declaration"></a>类声明示例

下面的示例显示了一个简单的类声明：

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>成员可访问性

在成员列表中声明类的成员。 类的成员列表可以分为任意数量 **`private`** ， **`protected`** 并 **`public`** 使用关键字称为访问说明符。  冒号 **：** 必须遵循访问说明符。  这些部分不需要是连续的，也就是说，这些关键字中的任何一个都可能在成员列表中多次出现。  关键字指定所有成员直到下一个访问说明符或右大括号的访问。 有关详细信息，请参阅[成员访问控制（c + +）](../cpp/member-access-control-cpp.md)。

## <a name="static-members"></a>静态成员

可将数据成员声明为静态，这表示类的所有对象都有权访问它的同一副本。 成员函数可以声明为静态，在这种情况下，它只能访问类的静态数据成员（并且没有*此*指针）。 有关详细信息，请参阅[静态数据成员](../cpp/static-members-cpp.md)。

## <a name="special-member-functions"></a>特殊成员函数

如果你并未在源代码中指定特殊成员函数，那么编译器自动提供的函数则为特殊成员函数。

1. 默认构造函数

1. 复制构造函数

1. **（C + + 11）** 移动构造函数

1. 复制赋值运算符

1. **（C + + 11）** 移动赋值运算符

1. 析构函数

有关详细信息，请参阅[特殊成员函数](../cpp/special-member-functions.md)。

## <a name="memberwise-initialization"></a>按成员初始化

在 C++ 11 和更高版本中，非静态成员声明符可以包含初始值设定项。

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

如果在构造函数中对一个成员分配了一个值，则该值将覆盖声明时用于初始化该成员的值。

对于给定类类型的所有对象，只有一个静态数据成员的共享副本。 必须在文件范围内定义静态数据成员并可在此范围内将其初始化。 （有关静态数据成员的详细信息，请参阅[静态数据成员](../cpp/static-members-cpp.md)。）下面的示例演示如何执行这些初始化：

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
> 类名 `CanInit2` 的前面必须有 `i` 以指定所定义的 `i` 是类 `CanInit2` 的成员。

## <a name="see-also"></a>另请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)
