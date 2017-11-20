---
title: "typeid 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b9b9df3203b580f21b27d7b4a27fb806b3ae7e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="typeid-operator"></a>typeid 运算符
## <a name="syntax"></a>语法  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## <a name="remarks"></a>备注  
 `typeid` 运算符允许在运行时确定对象的类型。  
  
 结果`typeid`是**const type_info &**。 该值是对引用**type_info**表示的对象*类型 id*或何种*表达式*，取决于哪种形式的`typeid`使用. 请参阅[type_info 类](../cpp/type-info-class.md)有关详细信息。  
  
 `typeid`运算符并不适用于托管类型 （抽象声明符或实例），请参阅[typeid](../windows/typeid-cpp-component-extensions.md)有关获取信息<xref:System.Type>的指定类型。  
  
 `typeid` 运算符在应用于多态类类型的左值时执行运行时检查，其中对象的实际类型不能由提供的静态信息确定。 此类情况是：  
  
-   对类的引用  
  
-   使用 * 取消引用的指针  
  
-   带下标的指针（即 [ ]）。 （请注意，通常情况下，将下标与指向多态类型的指针一起使用不安全。）  
  
 如果*表达式*指向基类类型，但该对象的实际类型是派生自该基类， **type_info**引用派生的类为结果。 *表达式*必须指向多态类型 （具有虚函数的类）。 否则，结果是**type_info**中引用的静态类*表达式*。 此外，必须取消引用指针以使用它指向的对象。 如果未取消引用指针，则结果将为**type_info**指针，它不指向。 例如:   
  
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
  
 如果*表达式*取消引用指针和指针的值为零， **typeid**引发[bad_typeid 异常](../cpp/bad-typeid-exception.md)。 如果指针不指向有效的对象，`__non_rtti_object`引发异常，来分析错误的 RTTI 指示尝试 （如访问冲突），因为该对象在某种程度上是无效 （无效的指针或代码不使用编译[/GR](../build/reference/gr-enable-run-time-type-information.md))。  
  
 如果*表达式*既不是指针，也不对基类的对象的引用的结果是**type_info**表示的静态类型的引用*表达式*. *静态类型*的表达式引用的表达式类型在编译时已知。 在计算表达式的静态类型时，将忽略执行语义。 此外，在确定表达式的静态类型时，将忽略引用（如果可能）：  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid**还可在模板中以确定模板参数的类型：  
  
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
  
## <a name="see-also"></a>另请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [关键字](../cpp/keywords-cpp.md)