---
title: 模板 (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032338"
---
# <a name="templates-c"></a>模板 (C++)

模板是C++通用编程的基础。 作为强类型语言，C++要求所有变量具有特定类型，要么由程序员显式声明或由编译器推断。 但是，无论它们使用哪种类型，许多数据结构和算法看起来都相同。 模板使您能够定义类或函数的操作，并允许用户指定这些操作应处理的具体类型。

## <a name="defining-and-using-templates"></a>定义和使用模板

模板是一种构造，它基于用户为模板参数提供的论点在编译时生成普通类型或函数。 例如，您可以定义如下所示的函数模板：

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上述代码描述了具有单类型参数*T*的泛型函数的模板，其返回值和调用参数（lhs 和 rhs）都是此类。 您可以命名任何你喜欢的类型参数，但按照惯例，最常用的是单个大写字母。 *T*是模板参数;**类型名称**关键字表示此参数是类型的占位符。 调用函数时，编译器将用用户指定或编译器推导`T`的混凝土类型参数替换 其每个实例。 编译器从模板生成类或函数的过程称为*模板实例化*;`minimum<int>`是模板`minimum<T>`的实例化。

在其他地方，用户可以声明专用于 int 的模板实例。假定 get_a（）和 get_b（）是返回 int 的函数：

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

但是，由于这是一个函数模板，编译器可以从参数`T`*a*和*b*推断其类型，因此可以像普通函数一样调用它：

```cpp
int i = minimum(a, b);
```

当编译器遇到最后一个语句时，它生成一个新函数，其中模板中*T*的每一次发生都替换为**int**：

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

编译器如何在函数模板中执行类型演绎的规则基于普通函数的规则。 有关详细信息，请参阅[函数模板调用的重载解析](../cpp/overload-resolution-of-function-template-calls.md)。

## <a name="type-parameters"></a><a id="type_parameters"></a>类型参数

在上面的`minimum`模板中，请注意，在函数调用参数中添加 const 和引用限定符之前，类型参数*T*不会以任何方式限定。

类型参数的数量没有实际限制。 按逗号分隔多个参数：

```cpp
template <typename T, typename U, typename V> class Foo{};
```

关键字**类**等效于此上下文中**的类型命名**。 您可以将前面的示例表示为：

```cpp
template <class T, class U, class V> class Foo{};
```

可以使用椭圆运算符 （...） 定义具有任意数为零个或多个类型参数的模板：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何内置类型或用户定义类型都可以用作类型参数。 例如，您可以在标准库中使用[std：：vector](../standard-library/vector-class.md)来存储**int**类型、**双**[、std：：字符串](../standard-library/basic-string-class.md)`MyClass`**、const** `MyClass`*`MyClass&`等的变量。 使用模板时的主要限制是类型参数必须支持应用于类型参数的任何操作。 例如，如果我们调用`minimum`using，`MyClass`如在此示例中所示：

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

将生成编译器错误，因为`MyClass`不为**<** 运算符提供重载。

没有任何固有要求，即任何特定模板的类型参数都属于同一对象层次结构，尽管您可以定义强制实施此类限制的模板。 您可以将面向对象的技术与模板相结合;例如，可以将派生* 存储在向量\<库\*>。    请注意，参数必须是指针

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector`和其他标准库容器对 的元素`T`施加的基本要求是`T`可复制和可复制构造。

## <a name="non-type-parameters"></a>非类型参数

与其他语言（如 C# 和 Java）中的泛型类型不同，C++模板支持*非类型参数*，也称为值参数。 例如，可以提供常量整数值来指定数组的长度，如本示例类似于标准库中的[std：：array](../standard-library/array-class-stl.md)类：

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

请注意模板声明中的语法。 该`size_t`值在编译时作为模板参数传入，并且必须是**const**或**constexpr**表达式。 像这样使用它：

```cpp
MyArray<MyClass*, 10> arr;
```

其他类型的值（包括指针和引用）可以作为非类型参数传入。 例如，可以将指针传递到函数或函数对象以自定义模板代码中的一些操作。

### <a name="type-deduction-for-non-type-template-parameters"></a>非类型模板参数的类型扣除

在 Visual Studio 2017 及更高版本中，在 **/std：c++17**模式下，编译器推导出使用**auto**声明的非类型模板参数的类型：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>模板作为模板参数

模板可以是模板参数。 在此示例中，MyClass2 有两个模板参数：类型名称参数*T*和模板参数*Arr*：

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

由于*Arr*参数本身没有正文，因此不需要其参数名称。 事实上，从 正文中引用*Arr*的类型名称或类参数名称是错误的`MyClass2`。 因此，可以省略*Arr*的类型参数名称，如以下示例所示：

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>默认模板参数

类和函数模板可以具有默认参数。 当模板具有默认参数时，您可以在使用它时将其保留为未指定参数。 例如，std：：vector 模板具有分配器的默认参数：

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大多数情况下，默认 std：：：分配器类是可以接受的，因此您可以使用如下所示的矢量：

```cpp
vector<int> myInts;
```

但是，如有必要，您可以指定如下所示的自定义分配器：

```cpp
vector<int, MyAllocator> ints;
```

对于多个模板参数，第一个默认参数后的所有参数必须具有默认参数。

使用参数全部为默认的模板时，请使用空角度括号：

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>模板特殊化

在某些情况下，模板不可能或不希望为任何类型的定义完全相同的代码。 例如，您可能希望定义仅在类型参数是指针或 std：：wstring 或派生自特定基类的类型时才能执行的代码路径。  在这种情况下，您可以为该特定类型定义模板的*专门化*。 当用户使用该类型实例化模板时，编译器使用专门化生成类，对于所有其他类型，编译器选择更通用的模板。 所有参数都专用的专业化化是*完整的专业化化*。 如果只有某些参数是专门化的，则称为*部分专业化化*。

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

只要每个专用类型参数是唯一的，模板就可以具有任意数量的专门化。 只有类模板可以部分专用。 模板的所有完整和部分专门化都必须在与原始模板相同的命名空间中声明。

有关详细信息，请参阅[模板专业化 。](../cpp/template-specialization-cpp.md)
