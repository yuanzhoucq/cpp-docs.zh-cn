---
title: 模板 (C++)
ms.date: 11/04/2016
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: f1532b5aa4ea712feab08b49b7c035187ca0d042
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547928"
---
# <a name="templates-c"></a>模板 (C++)

模板是用于在 C++ 中泛型的编程的基础。 作为强类型语言，C++ 需要具有特定类型，显式声明由程序员或由编译器推导的所有变量。 但是，许多数据结构和算法看起来相同，无论它们作用于哪种类型。 模板可使你能够定义的操作的类或函数，并允许用户指定哪些具体的类型的那些操作应处理。

## <a name="defining-and-using-templates"></a>定义和使用模板

模板是在编译时根据用户提供模板参数的参数生成的普通类型或函数的构造。 例如，可以定义与此类似的函数模板：

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上面的代码介绍了具有单个类型参数的泛型函数的模板*T*，它的返回值和调用参数 （lhs 和 rhs） 是所有此类。 可以命名为您类似，但通过约定单一大写字母最常用于名称的类型参数。 *T*是模板参数; **typename**关键字指示此参数是一种类型的占位符。 当调用该函数时，编译器将替换的每个实例`T`与具体的类型参数已由用户指定，或者由编译器推断。 进程在其中，编译器将生成一个类或函数模板中的称为*模板实例化*;`minimum<int>`是模板的实例化`minimum<T>`。

在其他位置，用户可以声明为 int。 专用化模板的实例假设 get_a() 和 get_b() 是返回 int 的函数：

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

但是，由于这是函数模板和编译器可以推断出的类型`T`从参数并*b*，可以就像普通函数一样调用它：

```cpp
int i = minimum(a, b);
```

当编译器遇到这最后一个语句时，它生成一个新的函数中的哪个每个匹配项*T*在模板中替换**int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

有关编译器如何在函数模板中执行类型推断规则基于普通函数的规则。 有关详细信息，请参阅[重载解析的函数模板调用](../cpp/overload-resolution-of-function-template-calls.md)。

## <a id="type_parameters"></a> 类型参数

在中`minimum`模板更高版本，请注意，类型参数*T*之前添加的常量和引用限定符用在函数调用参数中，未以任何方式进行限定。

类型参数的数目没有实际限制。 使用逗号分隔多个参数：

```cpp
template <typename T, typename U, typename V> class Foo{};
```

关键字**类**等效于**typename**在此上下文中。 可以表示为前面的示例：

```cpp
template <class T, class U, class V> class Foo{};
```

省略号运算符 （...） 可用于定义采用任意数量的零个或多个类型参数的模板：

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任何内置或用户定义类型可以用作类型参数。 例如，您可以使用 std:: vector 标准库中存储整数、 双精度型值、 字符串、 MyClass，const MyClass *，MyClass （& a)。 使用模板时的主要限制是类型参数必须支持应用于类型参数的任何操作。 例如，如果我们调用最小使用 MyClass，如此示例所示：

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

将生成编译器错误，因为 MyClass 不提供的重载 < 运算符。

没有固有要求任何特定模板中所有的类型参数属于相同的对象层次结构，尽管你可以定义强制此类的限制的模板。 您可以将面向对象的技术与模板;例如，您可以将存储派生 * 向量中\<Base\*>。    请注意，参数必须是指针

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

矢量和其他标准库容器施加的元素的基本要求`T`在于`T`为副本分配和复制构造。

## <a name="non-type-parameters"></a>非类型参数

与不同的是 C# 和 Java 等其他语言中的泛型类型，C++ 模板支持非类型参数，也称为值参数。 例如，您可以指定数组的长度的常量整数值与此类似于标准库中的 std:: array 类的示例一样：

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

注意，模板声明中的语法。 Size_t 值以传入的模板自变量在编译时，并且必须是常量或 constexpr 表达式。 此类中使用它：

```cpp
MyArray<MyClass*, 10> arr;
```

可以作为非类型参数中传递其他类型的值包括指针和引用。 例如，可以传递一个指针到函数或函数对象，若要自定义模板代码内的某些操作。

## <a id="template_parameters"></a> 作为模板参数的模板

模板可以是模板参数。 在此示例中，MyClass2 具有两个模板参数： typename 参数*T*和模板参数*Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

因为*Arr*参数本身有没有正文，不需要其参数名称。 事实上，它是错误来指代*Arr*的类型名称或类参数名称与主体内的`MyClass2`。 出于此原因， *Arr*的可以省略类型参数名称，在此示例中所示：

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>默认模板自变量

类和函数模板可以具有默认自变量。 当模板具有默认参数可以保留它未指定何时使用它。 例如，std:: vector 模板具有默认自变量分配器：

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

在大多数情况下默认 std:: allocator 类是可接受的因此使用一个向量，像这样：

```cpp
vector<int> myInts;
```

但是，如果必要您可以指定自定义分配器如下所示：

```cpp
vector<int, MyAllocator> ints;
```

对于多个模板自变量，第一个默认自变量后的所有自变量必须具有默认自变量。

使用其参数都所有默认模板时，使用空尖括号内：

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

## <a name="template-specialization"></a>模板专用化

在某些情况下，它并不可能的也最好用一个模板来定义的任何类型相同的代码。 例如，您可能想要定义要执行仅当类型参数是一个指针或 std:: wstring，或从特定基类派生的类型的代码路径。  在这种情况下可以定义*专用化*的该特定类型的模板。 当用户与该类型实例化模板时，编译器使用专用化来生成类，并对于所有其他类型，编译器将选择更常规模板。 所有参数都专用都化的专用化都*完成专用化*。 如果仅专用的某些参数，调用*部分专用化*。

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

模板可以包含任意数量的专用化，只要每个专用化的类型参数是唯一的。 只有类模板可以部分专用化。 必须在原始模板相同的命名空间中声明的模板的所有完整和部分专用化。

有关详细信息，请参阅[模板专用化](../cpp/template-specialization-cpp.md)。