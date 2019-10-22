---
title: typeid 运算符
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 93a2d3c494cd5aadafedcaaae9ec72809d633a4a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998748"
---
# <a name="typeid-operator"></a>typeid 运算符

## <a name="syntax"></a>语法

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>备注

**Typeid**运算符允许在运行时确定对象的类型。

**Typeid**的结果是 `const type_info&`。 值是对 `type_info` 对象的引用，该对象表示*表达式*的*类型 id*或类型，具体取决于所使用的**typeid**形式。 有关详细信息，请参阅[Type_info 类](../cpp/type-info-class.md)。

**Typeid**运算符不适用于托管类型（抽象声明符或实例）。 有关获取指定类型的 @no__t 的信息，请参阅[typeid](../extensions/typeid-cpp-component-extensions.md)。

当应用于多态类类型的左值时， **typeid**运算符执行运行时检查，其中对象的 true 类型无法由提供的静态信息确定。 此类情况是：

- 对类的引用

- 一个指针，用 `*` 取消引用

- 下标指针（`[ ]`）。 （使用带有指向多态类型的指针的下标是不安全的。）

如果*表达式*指向基类类型，但该对象实际上是派生自该基类的类型，则结果是派生类的 @no__t 1 引用。 *表达式*必须指向多态类型（具有虚函数的类）。 否则，结果为*表达式*中引用的静态类的 `type_info`。 此外，必须取消引用指针，以便使用的对象是它所指向的对象。 如果没有取消引用指针，结果将是指针的 `type_info`，而不是它所指向的内容。 例如：

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

如果*表达式*取消引用指针，并且该指针的值为零，则**typeid**将引发[bad_typeid 异常](../cpp/bad-typeid-exception.md)。 如果指针不指向有效的对象，则会引发 `__non_rtti_object` 异常。 它指示尝试分析因对象无效而触发了错误的 RTTI。 （例如，它是错误指针，或代码未使用[/GR](../build/reference/gr-enable-run-time-type-information.md)进行编译）。

如果该*表达式*不是指针，而不是对该对象的基类的引用，则结果为表示该*表达式*的静态类型的 `type_info` 引用。 表达式的*静态类型*引用表达式的类型，因为它在编译时是已知的。 在计算表达式的静态类型时，将忽略执行语义。 此外，在确定表达式的静态类型时，将忽略引用（如果可能）：

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

还可以在模板中使用**typeid**来确定模板参数的类型：

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)\
[关键字](../cpp/keywords-cpp.md)
