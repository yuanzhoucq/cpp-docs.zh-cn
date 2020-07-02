---
title: 函数调用运算符：（）
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 5bb87795d3e91d853dc0d269ee9d2aa3ba025c0e
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813545"
---
# <a name="function-call-operator-"></a>函数调用运算符：()

函数调用是一种 *`postfix-expression`* 由表达式构成的，该表达式的计算结果为函数或可调用的对象，后跟函数调用运算符 **`()`** 。 对象可以声明一个 `operator ()` 函数，该函数为对象提供函数调用语义。

## <a name="syntax"></a>语法

> *`postfix-expression`*:\
> &emsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>备注

函数调用运算符的参数来自以 *`argument-expression-list`* 逗号分隔的表达式列表。 这些表达式的值作为参数传递给函数。 *参数表达式列表*可以为空。 在 c + + 17 之前，函数表达式的计算顺序是未指定的，并且可以按任意顺序出现。 在 c + + 17 和更高版本中，函数表达式在任何参数表达式或默认参数之前计算。 参数表达式按不确定的顺序进行计算。

*`postfix-expression`* 计算结果为要调用的函数。 它可以采用以下任意一种形式：

- 函数标识符在当前范围内或在所提供的任何函数参数的作用域中可见，
- 一个表达式，该表达式的计算结果为函数、函数指针、可调用对象或对一个的引用。
- 成员函数访问器，无论是显式的还是隐式的
- 指向成员函数的取消引用的指针。

*`postfix-expression`* 可能是重载的函数标识符或重载成员函数访问器。 重载决策的规则确定要调用的实际函数。 如果成员函数是虚拟的，则在运行时确定要调用的函数。

一些示例声明：

- 函数返回类型 `T`。 示例声明如下

    ```cpp
    T func( int i );
    ```

- 指向函数返回类型 `T` 的指针。 示例声明如下

    ```cpp
    T (*func)( int i );
    ```

- 对函数返回类型 `T` 的引用。 示例声明如下

    ```cpp
    T (&func)(int i);
    ```

- 指向成员的指针函数取消引用返回类型 `T`。 示例函数调用如下

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>示例

以下示例调用带有三个自变量的标准库函数 `strcat_s`：

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>函数调用结果

函数调用的计算结果为右值，除非该函数声明为引用类型。 引用返回类型的函数的计算结果为左值。 这些函数可用于赋值语句的左侧，如下所示：

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

前面的代码定义一个名为的类 `Point` ，该类包含表示*x*和*y*坐标的私有数据对象。 必须修改这些数据对象，并且必须检索其值。 该程序只是针对此类的多个设计之一；另一种可能的设计是使用 `GetX` 与 `SetX` 函数或使用 `GetY` 与 `SetY` 函数。

返回类类型的函数、指向类类型的指针或对类类型的引用可以用作成员选择运算符的左操作数。 以下代码是合法的：

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

可以递归方式调用函数。 有关函数声明的详细信息，请参阅[函数](functions-cpp.md)。 相关材料位于[翻译单元和链接](../cpp/program-and-linkage-cpp.md)中。

## <a name="see-also"></a>请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C + + 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[函数调用](../c-language/function-call-c.md)
