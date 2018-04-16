---
title: "主表达式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a6e811e1fe074ce488b09fca29926989bc7f355
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="primary-expressions"></a>主要表达式
主表达式是更复杂的表达式的构造块。 它们是文本、名称以及范围解析运算符 (`::`) 限定的名称。  主表达式可以具有以下任一形式：  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A*文本*是常量主表达式。 其类型取决于其规范的形式。 请参阅[文本](../cpp/numeric-boolean-and-pointer-literals-cpp.md)有关指定文本的完整信息。  
  
 **这**关键字是指向类对象的指针。 它在非静态成员函数中可用，并指向为其调用函数的类的实例。 **这**关键字不能使用外部类成员函数体。  
  
 一种**这**指针`type`  **\*const** (其中`type`是类名称) 不是专门修改的函数中**此**指针。 下面的示例演示成员函数声明和类型的**这**:  
  
```  
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
  
 请参阅[此指针](this-pointer.md)有关修改的类型的详细信息**这**指针。  
  
 范围解析运算符 (`::`) 后跟名称构成了主表达式。  此类名称必须是全局范围内的名称，而不是成员名称。  此表达式的类型由名称的声明决定。 如果声明的名称是左值，则该类型是左值（即，它可以出现在赋值运算符表达式的左侧）。 范围解析运算符允许引用全局名称，即使该名称隐藏在当前范围中也如此。 请参阅[作用域](../cpp/scope-visual-cpp.md)有关如何使用范围解析运算符的示例。  
  
 用括号括起的表达式是与不带括号的表达式具有相同的类型和值的主表达式。 如果不带括号的表达式是左值，则用括号括起的表达式也是左值。  
  
 在上面，给出的主表达式语法的上下文中*名称*意味着在语法中所述的任何内容[名称](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db)，但当使用范围解析运算符之前的名称，类型的名称可仅发生类中不允许。  这包括用户定义的转换函数名称和析构函数名称。  
  
 主表达式的示例包括：  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 下面的示例所有考虑*名称*，并以各种形式的主表达式：  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>请参阅  
 [表达式类型](../cpp/types-of-expressions.md)