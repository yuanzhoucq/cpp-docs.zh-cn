---
title: 构造函数 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08200320e30816ac45e6c91a14dc41508430cfae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069113"
---
# <a name="constructors-c"></a>构造函数 (C++)

若要自定义如何初始化类成员，或创建您的类的对象时调用的函数，定义*构造函数*。 构造函数具有与类相同的名称，没有返回值。 您可以定义任意数量的重载构造函数根据需要自定义初始化以各种方式。 通常情况下，构造函数具有公共可访问性，以便在类定义或继承层次结构之外的代码可以创建类的对象。 但您也可以声明为一个构造函数**受保护**或**专用**。

构造函数可以根据需要采用成员初始化列表。 这是更高效的方法来初始化类成员的成员数目在构造函数主体中的赋值。 下面的示例演示一个类`Box`具有三个重载构造函数。 最后两个使用 init 成员列表：

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
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

声明类的实例时，编译器将选择要调用的构造函数根据重载决策的规则：

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

- 构造函数可声明为**内联**，[显式](#explicit_constructors)，**友元**或者[constexpr](#constexpr_constructors)。
- 构造函数可以初始化已声明为对象**const**，**易失性**或**const 易失性**。 对象将成为**const**在构造函数完成后。
- 在实现文件中定义的构造函数，为其提供一个限定的名称与任何其他成员函数一样： `Box::Box(){...}`。

## <a name="member_init_list"></a> 成员初始值设定项列表

构造函数可根据需要初始化之前执行的构造函数主体的类成员的成员初始值设定项列表。 (请注意，成员初始值设定项列表不与相同的功能*初始值设定项列表*类型的[std:: initializer_list\<T >](../standard-library/initializer-list-class.md)。)

使用成员初始值设定项列表是首选通过分配的构造函数的正文中的值，因为它直接初始化成员。 在下面的示例演示成员初始值设定项列表包含所有**identifier(argument)** 冒号后面的表达式：

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

标识符必须指向类成员;它是使用参数的值进行初始化。 参数可以是一个构造函数参数，函数调用或[std:: initializer_list\<T >](../standard-library/initializer-list-class.md)。

**const**必须在成员初始值设定项列表中初始化成员和引用类型的成员。

对参数化的基类构造函数的调用应在初始值设定项列表中进行，以确保在执行派生构造函数之前完全初始化的基类。

## <a name="default_constructors"></a> 默认构造函数

*默认构造函数*通常没有任何参数，但它们可能有具有默认值的参数。

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

默认构造函数是之一[特殊成员函数](special-member-functions.md)。 如果在类中不声明了任何构造函数，则编译器会提供一种隐式**内联**默认构造函数。

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

如果您依赖于隐式默认构造函数，请务必初始化成员在类定义中，在前面的示例所示。 没有这些初始值设定项，成员将为未初始化并且 Volume() 调用将生成一个垃圾回收的值。 一般情况下，它是很好的做法初始化这种方式中的成员，即使不依赖于隐式默认构造函数。

可以阻止编译器生成的隐式默认构造函数通过定义其作为[删除](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;

```

将定义编译器生成的默认构造函数，为已删除，如果任何类成员不是默认可构造。 例如，默认构造函数和析构函数可访问的类类型的所有成员，必须都具有它们类类型的成员。 所有数据成员的引用都类型，也一样**const**成员都必须具有一个默认成员初始值设定项。

当您调用编译器生成的默认构造函数，并尝试使用括号时，则会发出警告：

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

这是“最棘手的解析”问题的示例。 这种示例表达式既可以解释为函数的声明，也可以解释为对默认构造函数的调用，而且 C++ 分析器更偏向于声明，因此表达式会被视为函数声明。 有关详细信息，请参阅[最棘手的解析](http://en.wikipedia.org/wiki/Most_vexing_parse)。

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

但是，可以使用一组初始值设定项列表初始化框对象的数组：

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

有关详细信息，请参阅[初始值设定项](initializers.md)。

## <a name="copy_and_move_constructors"></a> 复制构造函数

A*复制构造函数*是特殊成员函数，将作为输入的相同对象的引用类型，并使它的一个副本。 如果您的类成员是所有的简单类型，例如标量值，编译器生成的复制构造函数是否足够大，您不需要定义您自己。 如果您的类需要更复杂的初始化，然后需要实现一个自定义的复制构造函数。 例如，如果类成员是一个指针，然后需要定义复制构造函数以分配新内存，并从各自的指向的对象中复制值。 编译器生成的复制构造函数只需复制指针，以便新指针仍指向对方的内存位置。

复制构造函数可能会产生这些签名之一：

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

在定义一个复制构造函数时，还应定义复制赋值运算符 （=）。 有关更多信息，请参见[赋值](assignment.md)和[复制构造函数和复制赋值运算符](copy-constructors-and-copy-assignment-operators-cpp.md)。

您可以通过定义为已删除的复制构造函数复制阻止您的对象：

```cpp
    Box (const Box& other) = delete;
```

尝试将对象复制到生成错误*C2280： 尝试引用已删除的函数*。

## <a name="move_constructors"></a> 移动构造函数

一个*移动构造函数*是将现有对象的数据的所有权移动到新的变量，而不复制原始数据的特殊成员函数。 它采用右值引用作为其第一个参数，并且任何其他参数必须具有默认值。 当传递了大型对象时，移动构造函数可显著提高程序的效率。 移动构造函数采用右值引用作为其第一个参数。 任何其他参数必须具有默认值。

```cpp
Box(Box&& other);
```

编译器选择移动构造函数在某些情况下，正在由另一个是即将销毁，不再需要它的相同类型的对象初始化对象时的资源。 下面的示例演示一种情况下，当通过重载决策选择移动构造函数。 在变量*框*get_Box() 返回是*xvalue* （即将到期值） 这是即将超出范围。 若要提供有关此示例的目的，我们来试框一个大型的表示其内容的字符串向量。 而不是复制向量和其字符串，移动构造函数"窃取"它即将到期的值"框"中，以便该向量现在属于新对象。 在调用`std::move`是因为需要同时`vector`和`string`类实现其自己的移动构造函数。

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

如果类未定义的移动构造函数，编译器将生成一个隐式，如果没有用户声明复制构造函数、 复制赋值运算符、 移动赋值运算符或析构函数。 如果不定义了任何显式或隐式的移动构造函数，否则将使用移动构造函数的操作使用的复制构造函数。 如果一个类中声明的移动构造函数或移动赋值运算符，隐式声明的复制构造函数定义为已删除。

隐式声明的移动构造函数被定义为类类型的任何成员缺少析构函数或编译器无法确定要用于移动操作的构造函数被删除。

有关如何编写非普通移动构造函数的详细信息，请参阅[移动构造函数和移动赋值运算符 （C++）](../cpp/move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="explicitly_defaulted_and_deleted_constructors"></a> 显式默认和已删除构造函数

可以使用显式*默认*复制构造函数、 默认构造函数、 移动构造函数、 复制赋值运算符、 移动赋值运算符和析构函数。 可以使用显式*删除*的所有特殊成员函数。

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

有关详细信息，请参阅[显式默认设置和已删除的函数](../cpp/explicitly-defaulted-and-deleted-functions.md)。

## <a name="constexpr_constructors"></a> constexpr 构造函数

构造函数可声明为[constexpr](constexpr-cpp.md)如果

- 它是可以声明为默认设置，否则它满足所有条件[constexpr 函数](constexpr-cpp.md#constexpr_functions)一般情况下;
- 类具有虚拟基类;
- 每个参数是[文本类型](trivial-standard-layout-and-pod-types.md#literal_types);
- 正文不是函数 try 块;
- 所有非静态数据成员和基类的子对象进行初始化;
- 如果类是 （a） 一个具有 variant 类型的值成员的联合，或 （b） 提供了匿名联合，只有一个联合成员进行初始化;
- 类类型的每个非静态数据成员和所有基类的子对象具有 constexpr 构造函数

## <a name="init_list_constructors"></a> 初始值设定项列表构造函数

如果构造函数采用[std:: initializer_list\<T\> ](../standard-library/initializer-list-class.md)类时，该构造函数参数，以及任何其他参数具有默认自变量，如选择重载解决方法通过直接初始化实例化。 可以使用 initializer_list 来初始化任何成员都可以接受它。 例如，假定 （如上所示） 的类具有`std::vector<string>`成员`m_contents`。 你可以提供此类的构造函数：

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

并创建如下对象：

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> 显式构造函数

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

这类转换可能在某些情况下很有用，但更常见的是，它们可能会导致代码中发生细微但严重的错误。 作为一般规则，应使用**显式**上一个构造函数 （和用户定义的运算符） 以防止出现这种隐式类型转换关键字：

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

构造函数是显式函数时，此行会导致编译器错误：`ShippingOrder so(42, 10.8);`。  有关详细信息，请参阅[用户定义类型的转换](../cpp/user-defined-type-conversions-cpp.md)。

## <a name="order_of_construction"></a> 构造函数顺序

构造函数按此顺序执行工作：

1. 按声明顺序调用基类和成员构造函数。

2. 如果类派生自虚拟基类，则会将对象的虚拟基指针初始化。

3. 如果类具有或继承了虚函数，则会将对象的虚函数指针初始化。 虚函数指针指向类中的虚函数表，确保虚函数正确地调用绑定代码。

4. 它执行自己函数体中的所有代码。

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

派生类构造函数始终调用基类构造函数，因此，在完成任何额外任务之前，它可以依赖于完全构造的基类。 派生的顺序调用基类构造函数，例如，如果`ClassA`派生自`ClassB`，它派生自`ClassC`，则`ClassC`首先，调用构造函数则`ClassB`构造函数中，则`ClassA`构造函数。

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>具有多重继承的类的构造函数

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

## <a name="virtual_functions_in_constructors"></a> 在构造函数中的虚函数

我们建议你谨慎调用构造函数中的虚函数。 基类构造函数始终在派生类构造函数之前调用，因此基构造函数中调用的函数是基类版本，而非派生类版本。 在下面的示例中，构造 `DerivedClass` 会导致执行 `BaseClass` 的 `print_it()` 实现早于 `DerivedClass` 构造函数导致执行 `DerivedClass` 的 `print_it()` 实现：

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

这是输出：

```Output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> 委托构造函数

一个*委托构造函数*调用同一个类来执行某些初始化工作中的其他构造函数。 当有多个构造函数，都必须执行类似工作时，这很有用。 您可以编写一个构造函数中的主逻辑并调用它从其他人。 在下面的简单示例，Box(int) 其工作委托给 Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```


所有构造函数完成后，完全初始化的构造函数将立即创建对象。 有关详细信息，请参阅[统一初始化和委托构造函数](../cpp/uniform-initialization-and-delegating-constructors.md)。

## <a name="inheriting_constructors">继承构造函数 (C++ 11)</a>

在派生的类可以通过使用从直接基类继承构造函数**使用**声明如下面的示例中所示：

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

**Visual Studio 2017 版本 15.7 及更高版本**:**使用**中的语句 **/std: c + + 17**模式将引入作用域从基类除具有相同签名的所有构造函数在派生类中的构造函数。 一般而言，当派生类未声明新数据成员或构造函数时，最好使用继承构造函数。 另请参阅[Visual Studio 2017 版本 15.7 中的改进](../cpp-conformance-improvements-2017.md#improvements_157)。

如果类型指定基类，则类模板可以从类型参数继承所有构造函数：

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

如果基类的构造函数具有相同签名，则派生类无法从多个基类继承。

## <a name="constructors_in_composite_classes"></a> 构造函数和复合类

包含类类型成员的类称为*复合类*。 创建复合类的类类型成员时，调用类自己的构造函数之前，先调用构造函数。 当包含的类没有默认构造函数是，必须使用复合类构造函数中的初始化列表。 在之前的 `StorageBox` 示例中，如果将 `m_label` 成员变量的类型更改为新的 `Label` 类，则必须调用基类构造函数，并且将 `m_label` 变量（位于 `StorageBox` 构造函数中）初始化：

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
