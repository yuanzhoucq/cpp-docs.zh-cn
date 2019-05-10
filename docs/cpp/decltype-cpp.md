---
title: decltype （C++）
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 0a4e9eb015df056dfe2a35da18cfa50875ced432
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222453"
---
# <a name="decltype--c"></a>decltype （C++）

**Decltype**类型说明符生成指定表达式的类型。 **Decltype**类型说明符一起使用[auto 关键字](../cpp/auto-cpp.md)，主要的开发人员编写模板库非常有用。 使用**自动**并**decltype**声明模板函数的返回类型取决于其模板自变量的类型。 或者，使用**自动**并**decltype**声明包装对其他函数的调用，然后返回所包装的函数的返回类型的模板函数。

## <a name="syntax"></a>语法

```
decltype( expression )
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*expression*|一个表达式。 有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。|

## <a name="return-value"></a>返回值

类型*表达式*参数。

## <a name="remarks"></a>备注

**Decltype**类型说明符在 Visual Studio 2010 或更高版本中支持和可与本机或托管代码。 Visual Studio 2015 及更高版本支持 `decltype(auto)` (C++14)。

编译器使用以下规则来确定的类型*表达式*参数。

- 如果*表达式*参数是标识符或[类成员访问](../cpp/member-access-operators-dot-and.md)，`decltype(expression)`是命名的实体的类型*表达式*。 如果没有此类实体或*表达式*参数命名一组重载函数，则编译器将生成一条错误消息。

- 如果*表达式*参数是对函数或重载的运算符函数的调用`decltype(expression)`是该函数的返回类型。 将忽略重载运算符两边的括号。

- 如果*表达式*参数是[rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)，`decltype(expression)`是一种*表达式*。 如果*表达式*参数是[左值](../cpp/lvalues-and-rvalues-visual-cpp.md)，`decltype(expression)`是[左值引用](../cpp/lvalue-reference-declarator-amp.md)为的类型*表达式*。

下面的代码示例演示的一些用途**decltype**类型说明符。 首先，假定已编码下列语句。

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

接下来，检查类型，返回的四个**decltype**下表中的语句。

|语句|类型|说明|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)到**const int**。|
|`decltype(var);`|**int**|变量 `var` 的类型。|
|`decltype(a->x);`|**double**|成员访问的类型。|
|`decltype((a->x));`|`const double&`|内部括号导致语句作为表达式而不是成员访问计算。 而且由于`a`被声明为`const`指针，该类型是指**const 双**。|

## <a name="decltype-and-auto"></a>Decltype 和 Auto

在 C++ 14 中，你可以使用`decltype(auto)`不带尾随返回类型来声明其返回类型的模板函数取决于其模板自变量的类型。

在 C + + 11 中，可以使用**decltype**类型一起使用的尾随返回类型上的说明符**自动**关键字来声明其返回类型的模板函数取决于其模板的类型自变量。 例如，考虑下面的代码示例，其中模板函数的返回类型取决于模板参数类型。 在代码示例中，*未知*占位符指示不能指定返回类型。

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

引入**decltype**类型说明符使开发人员若要获取模板函数返回的表达式类型。 使用*替代函数声明语法*更高版本，显示**自动**关键字，并且**decltype**类型说明符来声明*后指定*返回类型。 后指定返回类型是在对声明进行编译而不是编码时确定的。

以下原型阐述一个替代函数声明的语法。 请注意， **const**并**易失性**限定符，并且**引发**[异常规范](../cpp/exception-specifications-throw-cpp.md)都是可选的。 *Function_body*占位符表示指定函数作用的复合语句。 作为最佳编码做法，*表达式*中的占位符**decltype**语句与指定的表达式应匹配**返回**语句，如果有，在*function_body*。

**自动** *function_name* **(** *参数*<sub>选择</sub> **)** **const**<sub>opt</sub> **易失性**<sub>opt</sub> **->** **decltype (***表达式* **)** **引发**<sub>选择</sub> **{** *function_body***};**

在下面的代码示例中，`myFunc` 模板函数的后指定返回类型取决于 `t` 和 `u` 模板参数的类型。 作为最佳编码做法，此代码示例还使用右值引用和`forward`函数模板来支持*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Decltype 和转发函数 (C++11)

转发函数包装对其他函数的调用。 请考虑将其参数或包含这些参数的表达式的结果转发到其他函数的函数模板。 此外，转发函数返回调用其他函数的结果。 在此方案中，转发函数的返回类型应与包装函数的返回类型相同。

在此方案中，您无法编写适当的类型表达式而无需**decltype**类型说明符。 **Decltype**类型说明符将启用泛型转发函数，因为它不会丢失有关函数是否返回引用类型所需的信息。 有关转发函数的代码示例，请参阅上面的 `myFunc` 模板函数示例。

## <a name="example"></a>示例

下面的代码示例声明模板函数 `Plus()` 的后指定返回类型。 `Plus`函数将处理与两个操作数**operator +** 重载。 因此，对 `Plus` 函数的加运算符 (+) 和返回类型的解释取决于函数参数的类型。

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>示例

**Visual Studio 2017 和更高版本：** 模板是声明而不是实例化时，编译器将分析 decltype 参数。 因此，如果在 decltype 参数中找到非依赖专用化，则它不会被推迟到实例化时间，而会被立即处理，并且将在此时诊断产生的所有错误。

以下示例显示了在声明时引发的这类编译器错误：

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>要求

Visual Studio 2010 或更高版本。

`decltype(auto)` 需要 Visual Studio 2015 或更高版本。