---
title: "后缀增量和减量运算符：++ 和 -- | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "--"
  - "++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-- 运算符, 后缀减量运算符"
  - "++ 运算符, 后缀增量运算符"
  - "减量运算符"
  - "减量运算符, 语法"
  - "增量运算符, 语法"
  - "成员选择运算符"
  - "运算符 [C++], 后缀"
  - "后缀运算符"
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 后缀增量和减量运算符：++ 和 --
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
      postfix-expression   
      ++  
postfix-expression ––  
```  
  
## 备注  
 C\+\+ 提供了前缀和后缀递增和递减运算符；本节仅介绍后缀递增和递减运算符。有关详细信息，请参阅[前缀递增和递减运算符](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)。）两者的区别在于，在后缀表示法中，运算符出现在 *postfix\-expression* 之后，而在前缀表示法中，运算符出现在 *expression* 之前。以下示例显示了一个后缀递增运算符：  
  
```  
i++;  
```  
  
 应用后缀递增运算符 \(`++`\) 的效果是操作数的值增加一个适当类型的单位。  同样，应用后缀递减运算符 \(**––**\) 的效果是操作数的值减少一个适当类型的单元。  
  
 值得注意的是，后缀递增或递减表达式的计算结果为应用各自的运算符之前的表达式的值。  递增或递减运算在计算操作数之后发生。  仅当在较大的表达式的上下文中发生后缀递增或递减运算时才会出现此问题。  
  
 当后缀运算符应用于函数参数时，在参数的值传递给函数之前，不能保证该值是递增还是递减。有关详细信息，请参阅 C\+\+ 标准中的 1.9.17 节。  
  
 将后缀递增运算符应用于指向 **long** 类型的对象数组的指针实际上会将指针的内部表示形式增加 4。  此行为会导致以前引用数组的第 *n* 个元素的指针引用第 \(*n*\+1\) 个元素。  
  
 后缀递增运算符和后缀递减运算符的操作数必须是算术或指针类型的可修改的（非 **const**）左值。  结果的类型与 *postfix\-expression* 的类型相同，但不再是左值。  
  
 后缀递增运算符的操作数也可以是 `bool` 类型，在这种情况下，将计算操作数，然后将其设置为 **true**）。  后缀递减运算符的操作数不能是 `bool` 类型。  
  
 以下代码演示了后缀递增运算符：  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 不支持对枚举类型执行后递增和后递减操作：  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## 请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 后缀增量和减量运算符](../c-language/c-postfix-increment-and-decrement-operators.md)