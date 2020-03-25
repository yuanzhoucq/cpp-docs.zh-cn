---
title: 主表达式
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 03f0d0d04ad8ef2b052b9303d15437c53369a003
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177620"
---
# <a name="primary-expressions"></a>主表达式

主表达式是更复杂的表达式的构造块。 它们是文本、名称以及范围解析运算符 (`::`) 限定的名称。  主表达式可以具有以下任一形式：

```
literal
this
name
::name ( expression )
```

*文本*是常量主表达式。 其类型取决于其规范的形式。 有关指定文本的完整信息，请参阅[文本](../cpp/numeric-boolean-and-pointer-literals-cpp.md)。

**This**关键字是指向类对象的指针。 它在非静态成员函数中可用，并指向为其调用函数的类的实例。 不能在类成员函数的主体外使用**this**关键字。

**此**指针的类型在未专门修改**this**指针的函数中 `type` **\*const** （其中 `type` 是类名）。 下面的示例显示了成员函数声明以及**此**的类型：

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

有关修改**this**指针的类型的详细信息，请参阅[此指针](this-pointer.md)。

范围解析运算符 (`::`) 后跟名称构成了主表达式。  此类名称必须是全局范围内的名称，而不是成员名称。  此表达式的类型由名称的声明决定。 如果声明的名称是左值，则该类型是左值（即，它可以出现在赋值运算符表达式的左侧）。 范围解析运算符允许引用全局名称，即使该名称隐藏在当前范围中也如此。 有关如何使用范围解析运算符的示例，请参阅[范围](../cpp/scope-visual-cpp.md)。

用括号括起的表达式是与不带括号的表达式具有相同的类型和值的主表达式。 如果不带括号的表达式是左值，则用括号括起的表达式也是左值。

主表达式的示例包括：

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

下面的示例是所有考虑的*名称*，因此在各种形式下都是主表达式：

```cpp
MyClass // a identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>另请参阅

[表达式类型](../cpp/types-of-expressions.md)
