---
title: "函数调用 (C++) | Microsoft Docs"
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
  - "函数调用运算符 ( )"
  - "函数调用, C++ 函数"
  - "函数调用, 运算符"
  - "函数重载, 函数调用运算符"
  - "函数 [C++], 调用"
  - "运算符重载, 示例"
  - "运算符重载, 函数调用"
  - "运算符 [C++], 重载"
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数调用 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用括号调用的函数调用运算符是二元运算符。  
  
## 语法  
  
```  
  
primary-expression ( expression-list )  
```  
  
## 备注  
 在此上下文中，`primary-expression` 为第一个操作数，并且 `expression-list`（可能为参数的空列表）为第二个操作数。  函数调用运算符用于需要大量参数的操作。  这之所以有效，是因为 `expression-list` 是列表而非单一操作数。  函数调用运算符必须是非静态成员函数。  
  
 函数调用运算符在重载时不会修改函数的调用方式；相反，它会在运算符应用于给定类的类型的对象时修改解释该运算符的方式。  例如，以下代码通常没有意义：  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 但是，如果存在一个适当的重载函数调用运算符，则此语法可用于将 `x` 坐标偏移 3 个单位并将 `y` 坐标偏移 2 个单位。  下面的代码显示了这样的定义：  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 请注意，函数调用运算符适用于对象的名称，而不是函数的名称。  
  
 也可以使用指向函数的指针（而非该函数本身）重载函数调用运算符。  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
  
```  
  
## 请参阅  
 [运算符重载](../cpp/operator-overloading.md)