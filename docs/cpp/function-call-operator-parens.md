---
title: 函数调用运算符：()
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
ms.openlocfilehash: 08c60ff261e944ed5b54b51a013a6d331f212154
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179765"
---
# <a name="function-call-operator-"></a>函数调用运算符：()

后跟函数调用运算符 **（）** 的后缀表达式指定函数调用。

## <a name="syntax"></a>语法

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>备注

函数调用运算符的自变量是零或用逗号分隔的多个表达式 - 函数的自变量。

*后缀表达式*的计算结果必须为函数地址（例如，函数标识符或函数指针的值），*参数表达式列表*是值（参数）传递到函数的表达式的列表（用逗号分隔）。 argument-expression-list 参数可以为空。

*后缀表达式*必须是以下类型之一：

- 函数返回类型 `T`。 示例声明如下

    ```cpp
    T func( int i )
    ```

- 指向函数返回类型 `T` 的指针。 示例声明如下

    ```cpp
    T (*func)( int i )
    ```

- 对函数返回类型 `T` 的引用。 示例声明如下

    ```cpp
    T (&func)(int i)
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

除非函数被声明为引用类型，否则函数调用的计算结果为右值。 具有引用返回类型的函数的计算结果为左值，并且可在赋值语句的左侧使用该函数，如下所示：

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

前面的代码定义了一个名为 `Point`的类，该类包含表示*x*和*y*坐标的私有数据对象。 必须修改这些数据对象，并且必须检索其值。 该程序只是针对此类的多个设计之一；另一种可能的设计是使用 `GetX` 与 `SetX` 函数或使用 `GetY` 与 `SetY` 函数。

返回类类型的函数、指向类类型的指针或对类类型的引用可以用作成员选择运算符的左操作数。 因此，以下代码是合法的：

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

## <a name="see-also"></a>另请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[函数调用](../c-language/function-call-c.md)
