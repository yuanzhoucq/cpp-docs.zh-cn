---
title: 构造函数 (C++)
ms.date: 11/19/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 6cdf6241542c3f93484097c65015181a91647d49
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246620"
---
# <a name="constructors-c"></a>构造函数 (C++)

To customize how class members are initialized, or to invoke functions when an object of your class is created, define a *constructor*. 构造函数具有与类相同的名称，没有返回值。 You can define as many overloaded constructors as needed to customize initialization in various ways. Typically, constructors have public accessibility so that code outside the class definition or inheritance hierarchy can create objects of the class. But you can also declare a constructor as **protected** or **private**.

Constructors can optionally take a member init list. This is a more efficient way to initialize class members than assigning values in the constructor body. The following example shows a class `Box` with three overloaded constructors. The last two use member init lists:

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

When you declare an instance of a class, the compiler chooses which constructor to invoke based on the rules of overload resolution:

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Constructors may be declared as **inline**, [explicit](#explicit_constructors), **friend** or [constexpr](#constexpr_constructors).
- A constructor can initialize an object that has been declared as **const**, **volatile** or **const volatile**. The object becomes **const** after the constructor completes.
- To define a constructor in an implementation file, give it a qualified name as with any other member function: `Box::Box(){...}`.

## <a name="member_init_list"></a> Member initializer lists

A constructor can optionally have a member initializer list, which initializes class members prior to execution of the constructor body. (Note that a member initializer list is not the same thing as an *initializer list* of type [std::initializer_list\<T>](../standard-library/initializer-list-class.md).)

Using a member initializer list is preferred over assigning values in the body of the constructor because it directly initializes the member. In the following example shows the member initializer list consists of all the **identifier(argument)** expressions after the colon:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

The identifier must refer to a class member; it is initialized with the value of the argument. The argument can be one of the constructor parameters, a function call or a [std::initializer_list\<T>](../standard-library/initializer-list-class.md).

**const** members and members of reference type must be initialized in the member initializer list.

Calls to parameterized base class constructors should be made in the initializer list to ensure the base class is fully initialized prior to execution of the derived constructor.

## <a name="default_constructors"></a> Default constructors

*Default constructors* typically have no parameters, but they can have parameters with default values.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Default constructors are one of the [special member functions](special-member-functions.md). If no constructors are declared in a class, the compiler provides an implicit **inline** default constructor.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

If you rely on an implicit default constructor, be sure to initialize members in the class definition, as shown in the previous example. Without those initializers, the members would be uninitialized and the Volume() call would produce a garbage value. In general, it is good practice to initialize members in this way even when not relying on an implicit default constructor.

You can prevent the compiler from generating an implicit default constructor by defining it as [deleted](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

A compiler-generated default constructor will be defined as deleted if any class members are not default-constructible. For example, all members of class type, and their class-type members, must have a default constructor and destructors that are accessible. All data members of reference type, as well as **const** members must have a default member initializer.

When you call a compiler-generated default constructor and try to use parentheses, a warning is issued:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

这是“最棘手的解析”问题的示例。 这种示例表达式既可以解释为函数的声明，也可以解释为对默认构造函数的调用，而且 C++ 分析器更偏向于声明，因此表达式会被视为函数声明。 For more information, see [Most Vexing Parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

如果声明了任何非默认构造函数，编译器不会提供默认构造函数：

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

如果类没有默认构造函数，将无法通过单独使用方括号语法来构造该类的对象数组。 例如，在前面提到的代码块中，框的数组无法进行如下声明：

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

However, you can use a set of initializer lists to initialize an array of Box objects:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

For more information, see [Initializers](initializers.md).

## <a name="copy_and_move_constructors"></a> Copy constructors

A *copy constructor* initializes an object by copying the member values from an object of the same type. If your class members are all simple types such as scalar values, the compiler-generated copy constructor is sufficient and you do not need to define your own. If your class requires more complex initialization, then you need to implement a custom copy constructor. For example, if a class member is a pointer then you need to define a copy constructor to allocate new memory and copy the values from the other's pointed-to object. The compiler-generated copy constructor simply copies the pointer, so that the new pointer still points to the other's memory location.

A copy constructor may have one of these signatures:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

When you define a copy constructor, you should also define a copy assignment operator (=). For more information, see [Assignment](assignment.md) and [Copy constructors and copy assignment operators](copy-constructors-and-copy-assignment-operators-cpp.md).

You can prevent your object from being copied by defining the copy constructor as deleted:

```cpp
    Box (const Box& other) = delete;
```

Attempting to copy the object produces error *C2280: attempting to reference a deleted function*.

## <a name="move_constructors"></a> Move constructors

A *move constructor* is a special member function that moves ownership of an existing object's data to a new variable without copying the original data. It takes an rvalue reference as its first parameter, and any additional parameters must have default values. Move constructors can significantly increase your program's efficiency when passing around large objects.

```cpp
Box(Box&& other);
```

The compiler chooses a move constructor in certain situations where the object is being initialized by another object of the same type that is about to be destroyed and no longer needs its resources. The following example shows one case when a move constructor is selected by overload resolution. In the constructor that calls `get_Box()`, the returned value is an *xvalue* (eXpiring value). It is not assigned to any variable and is therefore about to go out of scope. To provide motivation for this example, let's give Box a large vector of strings that represent its contents. Rather than copying the vector and its strings, the move constructor "steals" it from the expiring value "box" so that the vector now belongs to the new object. The call to `std::move` is all that's needed because both `vector` and `string` classes implement their own move constructors.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Get_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

If a class does not define a move constructor, the compiler generates an implicit one if there is no user-declared copy constructor, copy assignment operator, move assignment operator, or destructor. If no explicit or implicit move constructor is defined, operations that would otherwise use a move constructor use the copy constructor instead. If a class declares a move constructor or move assignment operator, the implicitly declared copy constructor is defined as deleted.

An implicitly declared move constructor is defined as deleted if any members that are class types lack a destructor or the compiler cannot determine which constructor to use for the move operation.

For more information about how to write a non-trivial move constructor, see [Move Constructors and Move Assignment Operators (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Explicitly defaulted and deleted constructors

You can explicitly *default* copy constructors, default constructors, move constructors, copy assignment operators, move assignment operators, and destructors. You can explicitly *delete* all of the special member functions.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

For more information, see [Explicitly Defaulted and Deleted Functions](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> constexpr constructors

A constructor may be declared as [constexpr](constexpr-cpp.md) if

- it is either declared as defaulted or else it satisfies all the conditions for [constexpr functions](constexpr-cpp.md#constexpr_functions) in general;
- the class has no virtual base classes;
- each of the parameters is a [literal type](trivial-standard-layout-and-pod-types.md#literal_types);
- the body is not a function try-block;
- all non-static data members and base class sub-objects are initialized;
- if the class is (a) a union having variant members, or (b) has anonymous unions, only one of the union members is initialized;
- every non-static data member of class type, and all base-class sub-objects have a constexpr constructor

## <a name="init_list_constructors"></a> Initializer list constructors

If a constructor takes a [std::initializer_list\<T\>](../standard-library/initializer-list-class.md) as its parameter, and any other parameters have default arguments, that constructor will be selected in overload resolution when the class is instantiated through direct initialization. You can use the initializer_list to initialize any member that can accept it. For example, assume the Box class (shown previously) has a `std::vector<string>` member `m_contents`. You can provide a constructor like this:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

And then create Box objects like this:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Explicit constructors

如果类具有带一个参数的构造函数，或是如果除了一个参数之外的所有参数都具有默认值，则参数类型可以隐式转换为类类型。 例如，如果 `Box` 类具有一个类似于下面这样的构造函数：

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

可以初始化 Box，如下所示：

```cpp
Box b = 42;
```

或将一个 int 传递给采用 Box 的函数：

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

这类转换可能在某些情况下很有用，但更常见的是，它们可能会导致代码中发生细微但严重的错误。 As a general rule, you should use the **explicit** keyword on a constructor (and user-defined operators) to prevent this kind of implicit type conversion:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

构造函数是显式函数时，此行会导致编译器错误：`ShippingOrder so(42, 10.8);`。  For more information, see [User-Defined Type Conversions](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Order of construction

构造函数按此顺序执行工作：

1. 按声明顺序调用基类和成员构造函数。

1. 如果类派生自虚拟基类，则会将对象的虚拟基指针初始化。

1. 如果类具有或继承了虚函数，则会将对象的虚函数指针初始化。 虚函数指针指向类中的虚函数表，确保虚函数正确地调用绑定代码。

1. 它执行自己函数体中的所有代码。

下面的示例显示，在派生类的构造函数中，基类和成员构造函数的调用顺序。 首先，调用基构造函数，然后按照基类成员在类声明中出现的顺序对这些成员进行初始化，然后，调用派生构造函数。

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

这是输出：

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

派生类构造函数始终调用基类构造函数，因此，在完成任何额外任务之前，它可以依赖于完全构造的基类。 The base class constructors are called in order of derivation—for example, if `ClassA` is derived from `ClassB`, which is derived from `ClassC`, the `ClassC` constructor is called first, then the `ClassB` constructor, then the `ClassA` constructor.

如果基类没有默认构造函数，则必须在派生类构造函数中提供基类构造函数参数：

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

如果构造函数引发异常，析构的顺序与构造的顺序相反：

1. 构造函数主体中的代码将展开。

1. 基类和成员对象将被销毁，顺序与声明顺序相反。

1. 如果是非委托构造函数，所有完全构造的基类对象和成员均将被销毁。 但是，对象本身不是完全构造的，因此析构函数不会运行。

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructors for classes that have multiple inheritance

如果类从多个基类派生，那么将按照派生类声明中列出的顺序调用基类构造函数：

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

你应看到以下输出：

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating_constructors"></a> Delegating constructors

A *delegating constructor* calls a different constructor in the same class to do some of the work of initialization. This is useful when you have multiple constructors that all have to perform similar work. You can write the main logic in one constructor and invoke it from others. In the following trivial example, Box(int) delegates its work to Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

所有构造函数完成后，完全初始化的构造函数将立即创建对象。 For more information, see [Delegating Constructors](../cpp/delegating-constructors.md).

## <a name="inheriting_constructors"></a> Inheriting constructors (C++11)

A derived class can inherit the constructors from a direct base class by using a **using** declaration as shown in the following example:

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 and later**: The **using** statement in **/std:c++17** mode brings into scope all constructors from the base class except those that have an identical signature to constructors in the derived class. 一般而言，当派生类未声明新数据成员或构造函数时，最好使用继承构造函数。 See also [Improvements in Visual Studio 2017 version 15.7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

如果类型指定基类，则类模板可以从类型参数继承所有构造函数：

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

如果基类的构造函数具有相同签名，则派生类无法从多个基类继承。

## <a name="constructors_in_composite_classes"></a> Constructors and composite classes

Classes that contain class-type members are known as *composite classes*. 创建复合类的类类型成员时，调用类自己的构造函数之前，先调用构造函数。 当包含的类没有默认构造函数是，必须使用复合类构造函数中的初始化列表。 在之前的 `StorageBox` 示例中，如果将 `m_label` 成员变量的类型更改为新的 `Label` 类，则必须调用基类构造函数，并且将 `m_label` 变量（位于 `StorageBox` 构造函数中）初始化：

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>本节内容

- [Copy constructors and copy assignment operators](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Move constructors and move assignment operators](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegating constructors](delegating-constructors.md)

## <a name="see-also"></a>请参阅

[Classes and structs](classes-and-structs-cpp.md)
