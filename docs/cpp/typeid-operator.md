---
title: "typeid 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typeid 运算符"
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# typeid 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## 备注  
 `typeid` 运算符允许在运行时确定对象的类型。  
  
 `typeid` 的结果是 **const type\_info&**。  该值是对表示 *type\-id* 或 *expression* 的类型的 **type\_info** 对象的引用，具体取决于所使用的 `typeid` 的形式。  有关详细信息，请参阅 [type\_info 类](../cpp/type-info-class.md)。  
  
 `typeid` 运算符不适用于托管类型（抽象声明符或实例），有关获取指定类型的 <xref:System.Type> 的信息，请参阅 [typeid](../windows/typeid-cpp-component-extensions.md)。  
  
 `typeid` 运算符在应用于多态类类型的左值时执行运行时检查，其中对象的实际类型不能由提供的静态信息确定。  此类情况是：  
  
-   对类的引用  
  
-   使用 \* 取消引用的指针  
  
-   带下标的指针（即 \[ \]）。（请注意，通常情况下，将下标与指向多态类型的指针一起使用不安全。）  
  
 如果 *expression* 指向基类类型，但该对象实际上是派生自该基类的类型，则派生类的 **type\_info** 引用是结果。  *expression* 必须指向多态类型（具有虚函数的类）。  否则，结果是 *expression* 中引用的静态类的 **type\_info**。  此外，必须取消引用指针以使用它指向的对象。  如果未取消引用指针，结果将是指针的 **type\_info**，而不是它指向的内容。  例如：  
  
```  
// expre_typeid_Operator.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <typeinfo.h>  
  
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
  
 如果 *expression* 正在取消引用某个指针，并且该指针的值是零， **typeid** 将引发 [bad\_typeid 异常](../cpp/bad-typeid-exception.md)。  如果该指针没有指向有效的对象，则会引发 `__non_rtti_object` 异常来指示尝试了分析引发错误（如访问冲突）的 RTTI，因为该对象在某种程度上是无效的（无效的指针或代码不是用 [\/GR](../build/reference/gr-enable-run-time-type-information.md) 编译的）。  
  
 如果 *expression* 既不是指针也不是对对象的基类的引用，则结果是表示 *expression* 的静态类型的 **type\_info** 引用。  表达式的 *static type* 将引用在编译时已知的表达式的类型。  在计算表达式的静态类型时，将忽略执行语义。  此外，在确定表达式的静态类型时，将忽略引用（如果可能）：  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid** 还可在模板中使用以确定模板参数的类型：  
  
```  
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## 请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)