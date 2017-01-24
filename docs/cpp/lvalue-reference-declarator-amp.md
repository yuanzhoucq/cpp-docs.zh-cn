---
title: "Lvalue 引用声明符：&amp; | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 运算符, 引用运算符"
  - "引用运算符"
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Lvalue 引用声明符：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

保留对象的地址，但行为方式在语法上与对象相似。  
  
## 语法  
  
```  
  
type-id & cast-expression  
```  
  
## 备注  
 您可以将左值引用视为对象的另一名称。  左值引用声明由说明符的可选列表后跟一个引用声明符组成。  引用必须初始化且无法更改。  
  
 地址可转换为给定指针类型的任何对象也可转换为相似的引用类型。  例如，地址可转换为类型 `char *` 的任何对象也可转换为类型 `char &`。  
  
 不要将引用声明与 [address\-of 运算符](../cpp/address-of-operator-amp.md)的用法混淆。  `&` *标识符*前面有 `int` 或 `char` 之类的类型时，*标识符*将声明为对该类型的引用。  `&` *标识符*前面没有类型时，用法就是 address\-of 运算符的用法。  
  
## 示例  
 以下示例通过声明 `Person` 对象和对该对象的引用演示了引用声明符。  由于 `rFriend` 是对 `myFriend` 的引用，因此更新任一变量都将更改同一对象。  
  
```  
// reference_declarator.cpp  
// compile with: /EHsc  
// Demonstrates the reference declarator.  
#include <iostream>  
using namespace std;  
  
struct Person  
{  
    char* Name;  
    short Age;  
};  
  
int main()  
{  
   // Declare a Person object.  
   Person myFriend;  
  
   // Declare a reference to the Person object.  
   Person& rFriend = myFriend;  
  
   // Set the fields of the Person object.  
   // Updating either variable changes the same object.  
   myFriend.Name = "Bill";  
   rFriend.Age = 40;  
  
   // Print the fields of the Person object to the console.  
   cout << rFriend.Name << " is " << myFriend.Age << endl;  
}  
```  
  
  **Bill is 40**   
## 请参阅  
 [引用](../cpp/references-cpp.md)   
 [引用类型的函数参数](../cpp/reference-type-function-arguments.md)   
 [引用类型函数返回](../cpp/reference-type-function-returns.md)   
 [对指针的引用](../cpp/references-to-pointers.md)