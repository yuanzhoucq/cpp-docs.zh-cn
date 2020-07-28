---
title: 成员访问控制 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: de775c511701cd0b7cf923f47e33723b30a966e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186966"
---
# <a name="member-access-control-c"></a>成员访问控制 (C++)

使用访问控制，可以将类的[公共](../cpp/public-cpp.md)接口与[专用](../cpp/private-cpp.md)实现详细信息和仅供派生类使用的[受保护](../cpp/protected-cpp.md)成员分离。 访问说明符应用于在它之后声明的所有成员，直到遇到下一个访问说明符。

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

默认访问权限 **`private`** 在类和 **`public`** 结构或联合中。 类中的访问说明符可按任何顺序使用任意次数。 类类型的对象的存储分配是取决于实现的，但成员一定能分配到访问说明符之间的依次升高的内存地址。

## <a name="member-access-control"></a>成员访问控制

|访问类型|含义|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|声明为的类成员只能 **`private`** 由类的成员函数和友元（类或函数）使用。|
|[受保护](../cpp/protected-cpp.md)|声明为的类成员 **`protected`** 可由类的成员函数和友元（类或函数）使用。 此外，它们还可由派生自该类的类使用。|
|[public](../cpp/public-cpp.md)|声明为的类成员 **`public`** 可由任何函数使用。|

访问控制有助于阻止您通过不适当的方式使用对象。 在执行显式类型转换（强制转换）时，此保护将丢失。

> [!NOTE]
> 访问控制同样适用于所有名称：成员函数、成员数据、嵌套类和枚举数。

## <a name="access-control-in-derived-classes"></a>派生类中的访问控制

两个因素控制基类的哪些成员可在派生类中访问；这些相同的因素控制对派生类中的继承成员的访问：

- 派生类是否使用 **`public`** 访问说明符声明基类。

- 基类中对成员的访问权限如何。

下表显示了这些因素之间的交互以及如何确定基类成员访问。

### <a name="member-access-in-base-class"></a>基类中的成员访问

|private|protected|公共|
|-------------|---------------|------------|
|无论派生访问权限如何，始终不可访问|如果使用私有派生，则在派生类中为私有|如果使用私有派生，则在派生类中为私有|
||如果使用受保护派生，则在派生类中为受保护|如果使用受保护派生，则在派生类中为受保护|
||如果使用公有派生，则在派生类中为受保护|如果使用公有派生，则在派生类中为公有|

以下示例对此进行了说明：

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

在 `DerivedClass1` 中，成员函数 `PublicFunc` 是公共成员，`ProtectedFunc` 是受保护成员，因为 `BaseClass` 是公共基类。 `PrivateFunc` 对于 `BaseClass` 是私有的，因此任何派生类都无法访问它。

在 `DerivedClass2` 中，函数 `PublicFunc` 和 `ProtectedFunc` 被视为私有成员，因为 `BaseClass` 是私有基类。 同样，`PrivateFunc` 对于 `BaseClass` 是私有的，因此任何派生类都无法访问它。

您可以声明派生类而不使用基类访问说明符。 在这种情况下，如果派生类声明使用关键字，则将派生视为私有 **`class`** 。 如果派生类声明使用关键字，则将派生视为公共的 **`struct`** 。 例如，以下代码：

```cpp
class Derived : Base
...
```

等效于：

```cpp
class Derived : private Base
...
```

同样，以下代码：

```cpp
struct Derived : Base
...
```

等效于：

```cpp
struct Derived : public Base
...
```

请注意，声明为具有私有访问权限的成员无法访问函数或派生类，除非这些函数或类是使用 **`friend`** 基类中的声明声明的。

**`union`** 类型不能具有基类。

> [!NOTE]
> 指定私有基类时，建议显式使用 **`private`** 关键字，以便派生类的用户理解成员访问权限。

## <a name="access-control-and-static-members"></a>访问控制和静态成员

将基类指定为时 **`private`** ，它只会影响非静态成员。 在派生类中，公共静态成员仍是可访问的。 但是，使用指针、引用或对象访问基类的成员需要转换，此时将再次应用访问控制。 请考虑以下示例：

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

在前面的代码中，访问控制禁止从指向 `Derived2` 的指针转换为指向 `Base` 的指针。 **`this`** 指针的类型为隐式 `Derived2 *` 。 若要选择 `CountOf` 函数， **`this`** 必须将转换为类型 `Base *` 。 不允许执行此类转换，因为 `Base` 是 `Derived2` 的私有间接基类。 到私有基类类型的转换仅对于指向立即派生类的指针是可接受的。 因此，可以将 `Derived1 *` 类型的指针转换为 `Base *` 类型。

请注意，显式调用 `CountOf` 函数而不使用指针、引用或对象来选择它，则表示没有转换。 因此，允许该调用。

派生类 `T` 的成员和朋友可以将指向 `T` 的指针转换为指向 `T` 的私有直接基类的指针。

## <a name="access-to-virtual-functions"></a>对虚函数的访问

应用于[虚](../cpp/virtual-cpp.md)函数的访问控制由用于进行函数调用的类型确定。 重写函数的声明不会影响给定类型的访问控制。 例如：

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

在前面的示例中，使用指向 `GetState` 类型的指针调用虚函数 `VFuncBase` 将调用 `VFuncDerived::GetState`，并且会将 `GetState` 视为公共的。 但是，使用指向 `GetState` 类型的指针调用 `VFuncDerived` 是访问控制冲突，因为在 `GetState` 类中将 `VFuncDerived` 声明为私有的。

> [!CAUTION]
> 可以使用指向基类 `GetState` 的指针调用虚函数 `VFuncBase`。 这并不意味着调用的函数是该函数的基类版本。

## <a name="access-control-with-multiple-inheritance"></a>具有多重继承的访问控制

在涉及虚拟基类的多重继承方格中，可通过多个路径到达给定的名称。 由于可沿着这些不同的路径应用不同的访问控制，因此该编译器选择允许大多数访问的路径。 请参阅下图。

![沿继承图的路径访问](../cpp/media/vc38v91.gif "沿继承图的路径访问") <br/>
沿继承图的路径访问

在该图中，通过类 `VBase` 始终到达类 `RightPath` 中声明的名称。 右路径是更易于访问的，因为 `RightPath` 将 `VBase` 声明为公共基类，而 `LeftPath` 将 `VBase` 声明为私有基类。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)
