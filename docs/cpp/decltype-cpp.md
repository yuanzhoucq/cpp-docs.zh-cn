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
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180207"
---
# <a name="decltype--c"></a>decltype （C++）

**Decltype**类型说明符生成指定表达式的类型。 **Decltype**类型说明符与[auto 关键字](../cpp/auto-cpp.md)一起主要用于编写模板库的开发人员。 使用**auto**和**decltype**声明其返回类型依赖于其模板参数类型的模板函数。 或者，使用**auto**和**decltype**声明一个模板函数，该函数包装对其他函数的调用，然后返回包装函数的返回类型。

## <a name="syntax"></a>语法

```
decltype( expression )
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*expression*|一个表达式。 有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。|

## <a name="return-value"></a>返回值

*表达式*参数的类型。

## <a name="remarks"></a>备注

在 Visual Studio 2010 或更高版本中支持**decltype**类型说明符，并可与本机或托管代码一起使用。 Visual Studio 2015 及更高版本支持 `decltype(auto)` (C++14)。

编译器使用以下规则来确定*expression*参数的类型。

- 如果*expression*参数是标识符或[类成员访问](../cpp/member-access-operators-dot-and.md)，`decltype(expression)` 是按*expression*命名的实体的类型。 如果没有此类实体或*表达式*参数命名一组重载函数，则编译器将生成错误消息。

- 如果*expression*参数是对函数或重载运算符函数的调用，则 `decltype(expression)` 是函数的返回类型。 将忽略重载运算符两边的括号。

- 如果*expression*参数是[右](../cpp/lvalues-and-rvalues-visual-cpp.md)值，则 `decltype(expression)` 为*表达式*的类型。 如果*expression*参数是[左](../cpp/lvalues-and-rvalues-visual-cpp.md)值，则 `decltype(expression)` 是对该*表达式*类型的[左值引用](../cpp/lvalue-reference-declarator-amp.md)。

下面的代码示例演示了**decltype**类型说明符的一些用途。 首先，假定已编码下列语句。

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

接下来，检查下表中的四个**decltype**语句返回的类型。

|语句|类型|说明|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|对**const int**的[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)。|
|`decltype(var);`|**int**|变量 `var` 的类型。|
|`decltype(a->x);`|**double**|成员访问的类型。|
|`decltype((a->x));`|`const double&`|内部括号导致语句作为表达式而不是成员访问计算。 由于 `a` 声明为 `const` 指针，因此该类型是对**const double**的引用。|

## <a name="decltype-and-auto"></a>Decltype 和 Auto

在 c + + 14 中，可以使用不带尾随返回类型的 `decltype(auto)` 来声明其返回类型依赖于其模板参数类型的模板函数。

在 c + + 11 中，可以对尾随返回类型使用**decltype**类型说明符，并使用**auto**关键字来声明其返回类型依赖于其模板参数类型的模板函数。 例如，考虑下面的代码示例，其中模板函数的返回类型取决于模板参数类型。 在代码示例中，*未知*占位符指示无法指定返回类型。

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

引入**decltype**类型说明符使开发人员能够获取模板函数返回的表达式的类型。 使用以后显示的*替代函数声明语法*、 **auto**关键字和**decltype**类型说明符来声明*后期指定*的返回类型。 后指定返回类型是在对声明进行编译而不是编码时确定的。

以下原型阐述一个替代函数声明的语法。 请注意， **const**和**volatile**限定符以及**throw** [异常规范](../cpp/exception-specifications-throw-cpp.md)是可选的。 *Function_body*占位符表示指定函数作用的复合语句。 作为最佳编码做法， **decltype**语句中的*表达式*占位符应与*function_body*中的**return**语句指定的表达式（如果有）匹配。

**auto** *function_name* **（** *参数*<sub>opt</sub> **）** **const**<sub>opt</sub> **volatile**<sub>opt</sub> **->** **decltype （** *expression* **）** **throw**<sub>opt</sub> **{** *function_body* **};**

在下面的代码示例中，`myFunc` 模板函数的后指定返回类型取决于 `t` 和 `u` 模板参数的类型。 作为最佳编码做法，该代码示例还使用右值引用和支持*完美转发*的 `forward` 函数模板。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

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

在这种情况下，不能编写没有**decltype**类型说明符的合适类型表达式。 **Decltype**类型说明符启用通用转发函数，因为它不会丢失有关函数是否返回引用类型所需的信息。 有关转发函数的代码示例，请参阅上面的 `myFunc` 模板函数示例。

## <a name="example"></a>示例

下面的代码示例声明模板函数 `Plus()` 的后指定返回类型。 `Plus` 函数用**运算符 +** 重载来处理两个操作数。 因此，对 `Plus` 函数的加运算符 (+) 和返回类型的解释取决于函数参数的类型。

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

**Visual Studio 2017 及更高版本：** 声明模板而不是实例化模板时，编译器会分析 decltype 参数。 因此，如果在 decltype 参数中找到非依赖专用化，则它不会被推迟到实例化时间，而会被立即处理，并且将在此时诊断产生的所有错误。

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
