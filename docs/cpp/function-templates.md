---
title: 函数模板
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: f2caf70dd90e76c7bc4f20ea4bf34845b343efc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179739"
---
# <a name="function-templates"></a>函数模板

类模板可定义一系列相关类，这些类基于在实例化时传递到类的类型参数。 函数模板类似于类模板，但定义的是一系列函数。 利用函数模板，你可以指定基于相同代码但作用于不同类型或类的函数集。 以下函数模板交换两个项：

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

此代码定义交换自变量的值的一系列函数。 从此模板中，你可以生成将交换**int**和**long**类型以及用户定义类型的函数。 如果正确定义了类的复制构造函数和赋值运算符，`MySwap` 甚至会交换类。

此外，函数模板会阻止你交换不同类型的对象，因为编译器知道在编译时的*a*和*b*参数的类型。

尽管非模板化函数可以使用 void 指针运行此函数，但模板版本是 typesafe。 请考虑以下调用：

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

第二个 `MySwap` 调用触发了编译时错误，因为编译器无法生成具有不同类型的参数的 `MySwap` 函数。 如果使用了 void 指针，两个函数调用都将正确编译，但函数在运行时无法正常工作。

允许显式指定函数模板的模板参数。 例如：

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

当显式指定模板参数时，将对函数自变量执行常规隐式转换以将其转换为对应的函数模板自变量的类型。 在上面的示例中，编译器会将 `j` 转换为**char**类型。

## <a name="see-also"></a>另请参阅

[模板](../cpp/templates-cpp.md)<br/>
[函数模板实例化](../cpp/function-template-instantiation.md)<br/>
[显式实例化](../cpp/explicit-instantiation.md)<br/>
[函数模板的显式专用化](../cpp/explicit-specialization-of-function-templates.md)
