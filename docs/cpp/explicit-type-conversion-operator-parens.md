---
title: "显式类型转换运算符：() | Microsoft Docs"
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
  - "转换 [C++], explicit"
  - "数据类型转换 [C++], explicit"
  - "显式数据类型转换运算符"
  - "运算符 [C++], 显式类型转换"
  - "类型转换 [C++], 显式转换"
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 显式类型转换运算符：()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 允许使用与函数调用语法类似的语法进行显式类型转换。  
  
## 语法  
  
```  
  
simple-type-name ( expression-list )  
```  
  
## 备注  
 后跟包含在括号中的 *expression\-list* 的 *simple\-type\-name* 使用指定表达式构造指定类型的对象。  以下示例显示到类型 int 的显式类型转换：  
  
```  
int i = int( d );  
```  
  
 以下示例使用在[函数调用结果](../misc/function-call-results.md)中定义的 `Point` 类的修改版本。  
  
## 示例  
  
```  
// expre_Explicit_Type_Conversion_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
public:  
    // Define default constructor.  
    Point() { _x = _y = 0; }  
    // Define another constructor.  
    Point( int X, int Y ) { _x = X; _y = Y; }  
  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
    void Show()   { cout << "x = " << _x << ", "  
                         << "y = " << _y << "\n"; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
int main()  
{  
    Point Point1, Point2;  
  
    // Assign Point1 the explicit conversion  
    //  of ( 10, 10 ).  
    Point1 = Point( 10, 10 );  
  
    // Use x() as an l-value by assigning an explicit  
    //  conversion of 20 to type unsigned.  
    Point1.x() = unsigned( 20 );  
    Point1.Show();  
  
    // Assign Point2 the default Point object.  
    Point2 = Point();  
    Point2.Show();  
}  
```  
  
## 输出  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 尽管前面的示例演示了使用常量的显式类型转换，但在对对象执行转换时，此方法也同样有效。  以下代码片段对此进行了演示：  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 还可以使用“cast”语法指定显式类型转换。  使用 cast 语法重写的上一个示例是：  
  
```  
d = (float)i;  
```  
  
 当从单个值转换时，强制转换和函数样式转换都有相同的结果。  但是，在函数样式语法中，可以为转换指定多个参数。  此差异对用户定义的类型非常重要。  请考虑 `Point` 类及其转换：  
  
```  
struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  
```  
  
 前面的使用函数样式转换的示例演示了如何将两个值（一个用于 *x*，另一个用于 *y*）转换为用户定义的类型 `Point`。  
  
> [!CAUTION]
>  请谨慎使用显式类型转换，因其会重写 C\+\+ 编译器的内置类型检查。  
  
 [强制转换](../cpp/cast-operator-parens.md)批注必须用于到没有 *simple\-type\-name*（例如，指针或引用类型）的类型的转换。  到可与 *simple\-type\-name* 一起表示的类型的转换可以使用任何一种形式写入。  有关 *simple\-type\-name* 的构造详细信息，请参阅[类型说明符](http://msdn.microsoft.com/zh-cn/34b6c737-0ef1-4470-9b77-b26e46c0bbd4)。  
  
 在强制转换中的类型定义是非法的。  
  
## 请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)