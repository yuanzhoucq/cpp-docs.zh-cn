---
title: 模板 (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 5f8322d850084ca53e946dcff1b67dc81b493fe3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160770"
---
# <a name="templates-c"></a>模板 (C++)

模板是用于在 C++ 中泛型的编程的基础。 作为强类型语言，C++ 需要具有特定类型，显式声明由程序员或由编译器推导的所有变量。 但是，许多数据结构和算法的外观都是相同的，无论它们的操作类型是什么。 利用模板，您可以定义类或函数的操作，并允许用户指定这些操作应使用的具体类型。

## <a name="defining-and-using-templates"></a>定义和使用模板

模板是一种构造，它基于用户为模板参数提供的参数在编译时生成普通类型或函数。 例如，可以按如下所示定义函数模板：

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上面的代码描述了具有单类型参数*T*的泛型函数的模板，其返回值和调用参数（lhs 和 rhs）都是此类型。 你可以使用你喜欢的任意名称来命名类型参数，但通常情况下，最常使用单个大写字母。 *T*是一个模板参数;**typename**关键字指出此参数是某个类型的占位符。 调用函数时，编译器会将 `T` 的每个实例替换为具体类型参数，该参数由用户指定或由编译器推断。 编译器从模板生成类或函数的过程称为*模板实例化*;`minimum<int>` 是 `minimum<T>`模板的实例化。

在其他地方，用户可以声明专用于 int 的模板的实例。假定 get_a （）和 get_b （）是返回 int 的函数：

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

不过，由于这是一个函数模板，并且编译器可以从参数*a*和*b*推导 `T` 的类型，因此可以像普通函数一样调用它：

```cpp
int i = minimum(a, b);
```

当编译器遇到最后一个语句时，它会生成一个新函数，其中，模板中的每个*T*均替换为**int**：

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

编译器在函数模板中执行类型推导的规则基于普通函数的规则。 有关详细信息，请参阅[函数模板调用的重载解析](../cpp/overload-resolution-of-function-template-calls.md)。

## <a name="type-parameters"></a><a id="type_parameters"></a>类型参数

请注意，在上面的 `minimum` 模板中，类型参数*t*在函数调用参数中使用时是不以任何方式限定的，在该参数中添加了 const 和 reference 限定符。

类型参数的数量没有实际限制。 用逗号分隔多个参数：

```cpp
template <typename T, typename U, typename V> class Foo{};
```

关键字**类**与此上下文中的**typename**等效。 您可以将上一个示例表示为：

```cpp
template <class T, class U, class V> class Foo{};
```

您可以使用省略号运算符（...）来定义一个模板，该模板采用任意数量的零个或多个类型参数：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何内置或用户定义的类型都可用作类型参数。 例如，可以在标准库中使用[std：： vector](../standard-library/vector-class.md)来存储**int**、 **double**、 [std：： string](../standard-library/basic-string-class.md)、`MyClass`、 **const** `MyClass`*、`MyClass&`等类型的变量。 使用模板时的主要限制是类型参数必须支持应用于类型参数的任何操作。 例如，如果使用 `MyClass` 调用 `minimum`，如本示例所示：

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

将生成编译器错误，因为 `MyClass` 不为 **<** 运算符提供重载。

虽然您可以定义强制此类限制的模板，但任何特定模板的类型参数都不属于同一对象层次结构。 可以将面向对象的技术与模板结合起来;例如，可以在向量中存储派生 *\<基\*>。    请注意，参数必须是指针

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector` 和其他标准库容器对 `T` 的元素施加的基本要求是，`T` 可以是可复制的，也可以是可构造。

## <a name="non-type-parameters"></a>非类型参数

不同于其他语言（如C#和 Java）中的C++泛型类型，模板支持*非类型参数*（也称为值参数）。 例如，你可以提供常量整数值来指定数组的长度，如此示例类似于标准库中的[std：： array](../standard-library/array-class-stl.md)类：

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

请注意模板声明中的语法。 在编译时，`size_t` 值作为模板参数传入，并且它必须是**常量**或**constexpr**表达式。 如下所示：

```cpp
MyArray<MyClass*, 10> arr;
```

其他类型的值（包括指针和引用）可以作为非类型参数传入。 例如，你可以传入指向函数或函数对象的指针，以自定义模板代码内的某些操作。

### <a name="type-deduction-for-non-type-template-parameters"></a>非类型模板参数的类型推导

在 Visual Studio 2017 和更高版本中，在 **/std： c + + 17**模式下，编译器推导使用**auto**声明的非类型模板参数的类型：

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>模板作为模板参数

模板可以是模板参数。 在此示例中，MyClass2 具有两个模板参数： typename 参数*T*和模板参数*Arr*：

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

由于*Arr*参数本身没有正文，因此不需要它的参数名称。 事实上，从 `MyClass2`体内引用*Arr*的 typename 或类参数名称是错误的。 出于此原因，可以省略*Arr*的类型参数名称，如以下示例中所示：

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>默认模板参数

类和函数模板可以有默认参数。 如果模板具有默认参数，则可以在使用时将其保留为未指定状态。 例如，std：： vector 模板具有分配器的默认参数：

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大多数情况下，默认 std：：分配器类是可接受的，因此你可以使用如下所示的向量：

```cpp
vector<int> myInts;
```

但如有必要，可以指定自定义分配器，如下所示：

```cpp
vector<int, MyAllocator> ints;
```

对于多个模板参数，第一个默认参数后的所有参数必须具有默认参数。

如果使用的模板的参数均为默认参数，请使用空白尖括号：

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

在某些情况下，不可能或不需要模板为任何类型定义完全相同的代码。 例如，你可能希望定义要在类型参数是指针、std：： wstring 或从特定基类派生的类型时执行的代码路径。  在这种情况下，您可以为该特定类型定义模板的*专用化*。 当用户使用该类型对模板进行实例化时，编译器将使用特殊化来生成类，对于所有其他类型，编译器将选择更常规的模板。 专用化，其中所有参数*都是专用的。* 如果仅某些参数是专用的，则称为*部分专用化*。

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

只要每个专用类型参数都是唯一的，模板就可以拥有任意数量的专用化。 只有类模板可以部分专用化。 模板的所有完整和部分专用化必须在与原始模板相同的命名空间中声明。

有关详细信息，请参阅[模板特殊化](../cpp/template-specialization-cpp.md)。
