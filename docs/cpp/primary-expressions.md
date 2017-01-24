---
title: "主要表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "表达式 [C++], 文本"
  - "表达式 [C++], 名称"
  - "表达式 [C++], 主"
  - "表达式 [C++], 限定名称"
  - "主要表达式"
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 主要表达式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

主表达式是更复杂的表达式的构造块。  它们是文本、名称以及范围解析运算符 \(`::`\) 限定的名称。主表达式可以具有以下任一形式：  
  
```  
  
        literal  
this  
:: name  
name   
( expression )  
```  
  
 *literal* 是常量主表达式。  其类型取决于其规范的形式。  有关指定文本的完整信息，请参阅[文本](../cpp/numeric-boolean-and-pointer-literals-cpp.md)。  
  
 **this** 关键字是指向类对象的指针。  它在非静态成员函数中可用，并指向为其调用函数的类的实例。  **this** 关键字只能在类成员函数体的外部使用。  
  
 **this** 指针的类型是未特别修改 **this** 指针的函数中的 `type` **\*const**（其中 `type` 是类名）。  以下示例演示成员函数声明以及 **this** 的类型：  
  
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
  
 有关修改 **this** 指针的类型的详细信息，请参阅 [this 指针的类型](../misc/type-of-this-pointer.md)。  
  
 范围解析运算符 \(`::`\) 后跟名称构成了主表达式。此类名称必须是全局范围内的名称，而不是成员名称。此表达式的类型由名称的声明决定。  如果声明的名称是左值，则该类型是左值（即，它可以出现在赋值运算符表达式的左侧）。  范围解析运算符允许引用全局名称，即使该名称隐藏在当前范围中也如此。  有关如何使用范围解析运算符的示例，请参阅[范围](../cpp/scope-visual-cpp.md)。  
  
 用括号括起的表达式是与不带括号的表达式具有相同的类型和值的主表达式。  如果不带括号的表达式是左值，则用括号括起的表达式也是左值。  
  
 在上面给出的主表达式语法的上下文中，*name* 表示为 [name](http://msdn.microsoft.com/zh-cn/1c49cc24-08d5-4884-b170-ba8ed42d80db) 描述的语法中的任何内容，不过，当在名称前使用范围解析运算符时，不允许使用只能在类中出现的名称的类型。这包括用户定义的转换函数名称和析构函数名称。  
  
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
  
 下面的示例是所有考虑的 *name* 以及各种形式的主表达式：  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## 请参阅  
 [表达式的类型](../cpp/types-of-expressions.md)