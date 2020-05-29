---
title: 后缀表达式
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 897eb80c713f786ecf0f7e6c9cf24cd8bdfc0aa8
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032273"
---
# <a name="postfix-expressions"></a>后缀表达式

后缀表达式包含主表达式或者其中的后缀运算符跟在主表达式之后的表达式。 下表列出了后缀运算符。

### <a name="postfix-operators"></a>后缀运算符

|运算符名称|运算符表示法|
|-------------------|-----------------------|
|[副脚本运算符](../cpp/subscript-operator.md)|**[ ]**|
|[函数调用运算符](../cpp/function-call-operator-parens.md)|**( )**|
|[显式类型转换运算符](../cpp/explicit-type-conversion-operator-parens.md)|*类型名称* **（ ）**|
|[成员访问运算符](../cpp/member-access-operators-dot-and.md)|**.** 或**->**|
|[后缀递增运算符](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[后缀递减运算符](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

以下语法描述了可能的后缀表达式：

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

上面的*后修复表达式*可以是主表达式或其他后缀表达式。  请参阅**主表达式**。  后缀表达式从左到右进行分组，这允许表达式按如下方式链接起来：

```cpp
func(1)->GetValue()++
```

在上面的表达式中，`func`是一个主表达式`func(1)`，是函数后缀表达式，`func(1)->GetValue`是指定类成员的后缀表达式，`func(1)->GetValue()`是另一个函数后缀表达式，整个表达式是递修复表达式，递增表达式，递价表达式增加了 GetValue 的返回值。  该表达式的整体含义是作为自变量传递 1 的 "call func，并作为返回值获取一个指向类的指针。  然后调用`GetValue()`该类，然后增加返回的值。

上面列出的表达式是赋值表达式，这意味着这些表达式的结果必须为右值。

后缀表达式形式

```cpp
simple-type-name ( expression-list )
```

指示构造函数的调用。  如果 simple-type-name 是基本类型，则表达式列表必须是单个表达式，并且该表达式指示表达式的值将转换为基础类型。  此类强制转换表达式模仿构造函数。  由于此形式允许使用相同的语法来构造基本类型和类，因此它在定义模板类时特别有用。

*强制关键字*是**dynamic_cast、static_cast**或**reinterpret_cast**之**static_cast**一。  更多信息可在**dynamic_cast、static_cast**和**reinterpet_cast**中找到**static_cast**。

**类型 id**运算符被视为后缀表达式。  请参阅**类型化运算符**。

## <a name="formal-and-actual-arguments"></a>形式和实际自变量

调用程序会将信息传递到“自变量”中的已调用函数。 已调用函数使用对应的“形式自变量”访问信息。

当调用函数时，将执行以下任务：

- 计算所有实参（调用方提供的参数）。 没有计算这些自变量的隐含顺序，但所有自变量都会计算，并且所有副作用都会在进入该函数前完成。

- 使用每个形参在表达式列表中对应的实参来初始化该形参。 （正式参数是在函数标头中声明并在函数正文中使用的参数。转换就像通过初始化来完成一样 - 在将实际参数转换为正确的类型时，执行标准和用户定义的转换。 以下代码从概念上演示了所执行的初始化：

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

   调用前的概念性初始化为：

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

   请注意，初始化就像使用等号语法（而不是括号语法）一样执行。 在将值传递到函数之前制作了 `i` 的副本。 （有关详细信息，请参阅[初始化器](../cpp/initializers.md)和[转换](../cpp/user-defined-type-conversions-cpp.md)。

   因此，如果函数原型（声明）调用类型**为长**的参数，并且调用程序提供**类型 int**的实际参数，则使用标准类型转换将实际参数提升到**类型长**（请参阅[标准转换](../cpp/standard-conversions.md)）。

   如果提供了一个实际自变量，但它没有到形式自变量类型的标准的或用户定义的转换，则是一个错误。

   对于类类型的实际自变量，将通过调用类的构造函数初始化形式自变量。 （有关这些特殊类成员函数的更多，请参阅[构造函数](../cpp/constructors-cpp.md)。

- 执行函数调用。

以下程序片段演示了函数调用：

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

当`func`从 main 调用时，正式`param1`参数用`i`的值初始`i`化（转换为类型**长**，以对应于使用标准转换的正确类型），并且用 值`param2``j``j`（使用标准转换转换为类型**双**号）来初始化形式参数。

## <a name="treatment-of-argument-types"></a>自变量类型的处理

不能在函数主题内更改声明为 const 类型的形参。 函数可以更改任何不是类型**const**的参数。 但是，更改是函数的局部更改，不会影响实际参数的值，除非实际参数是对类型**const**对象的引用。

以下函数阐释了其中的一些概念：

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipsis-and-default-arguments"></a>省略号和默认参数

通过使用下列两种方法之一，可以声明函数以接受比函数定义中指定的自变量更少的自变量：省略号 (`...`) 或默认自变量。

椭圆表示可能需要参数，但声明中未指定数字和类型。 这通常是较差的 C++ 编程做法，因为它使您无法获得 C++ 的一个优点，即类型安全。 与已知形式参数类型和实际参数类型的函数相比，使用省略号声明的函数的转换不同：

- 如果实际参数为 **"浮点**"类型，则在函数调用之前将其提升为**双**精度类型。

- 使用积分提升将任何已签名或未签名**的字符**、**短**字符、枚举类型或位字段转换为已签名或未签名**的 int。**

- 类类型的所有参数都作为数据结构通过值进行传递；副本是由二进制复制创建的，而不是通过调用类的复制构造函数（如果存在）创建的。

如果使用椭圆，则必须在参数列表中最后声明。 有关传递可变参数数的详细信息，请参阅*运行时库参考*中讨论[va_arg、va_start和va_list。](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)

有关 CLR 编程中的默认参数的信息，请参阅[变量参数列表 （...） （C++/CLI）。](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)

如果函数调用中没有提供值，则可通过默认参数指定参数应采用的值。 以下代码片段演示默认自变量的工作方式。 有关指定默认参数的限制的详细信息，请参阅[默认参数](../cpp/default-arguments.md)。

```cpp
// expre_Ellipsis_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

上面的程序声明一个采用两个参数的函数 `print`。 但是，第二个参数*终止符*具有默认值`"\n"`。 在`main`中，前两个`print`调用允许默认第二个参数提供新行以终止打印的字符串。 第三个调用为第二个参数指定显式值。 该程序的输出为

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>请参阅

[表达式的类型](../cpp/types-of-expressions.md)
