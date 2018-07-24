---
title: typeid 运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b51d2a3861cb26073063058aa4124244d94df40b
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207447"
---
# <a name="typeid-operator"></a>typeid 运算符
## <a name="syntax"></a>语法  
  
```  
  
typeid(type-id)  
typeid(expression)  
```  
  
## <a name="remarks"></a>备注  
 **Typeid**运算符允许在运行时确定对象的类型。  
  
 结果**typeid**是`const type_info&`。 值是指`type_info`表示的对象*类型 id*或类型的*表达式*，具体哪种形式的取决于**typeid**使用。 请参阅[type_info 类](../cpp/type-info-class.md)有关详细信息。  
  
 **Typeid**不适用于托管类型 （抽象声明符或实例），请参阅[typeid](../windows/typeid-cpp-component-extensions.md)有关获取信息<xref:System.Type>的指定类型。  
  
 **Typeid**运算符执行运行时检查时应用于多态类类型的左值的对象的真实类型不能由提供的静态信息。 此类情况是：  
  
-   对类的引用  
  
-   使用取消引用指针 \*  
  
-   带下标的指针（即 [ ]）。 （请注意，通常情况下，将下标与指向多态类型的指针一起使用不安全。）  
  
 如果*表达式*指向基类类型，但该对象实际上是从该基类，派生的类型的`type_info`引用派生的类的结果。 *表达式*必须指向多态类型 （具有虚函数的类）。 否则，会得到`type_info`中引用的静态类*表达式*。 此外，必须取消引用指针以使用它指向的对象。 如果未取消引用指针，结果将是`type_info`指针，它不指向。 例如：  
  
```cpp 
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
  
 如果*表达式*正在取消引用指针和指针的值为零， **typeid**引发[bad_typeid 异常](../cpp/bad-typeid-exception.md)。 如果指针不指向有效的对象，`__non_rtti_object`引发异常，指示试图分析错误的 RTTI （如访问冲突），因为该对象是以某种方式无效 （无效的指针或代码不使用编译[/GR](../build/reference/gr-enable-run-time-type-information.md))。  
  
 如果*表达式*是一个指针和对该对象的基类的引用都不会得到`type_info`表示的静态类型的引用*表达式*。 *静态类型*表达式的引用类型的表达式在编译时已知。 在计算表达式的静态类型时，将忽略执行语义。 此外，在确定表达式的静态类型时，将忽略引用（如果可能）：  
  
```cpp 
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid**还可在模板中以确定模板参数的类型：  
  
```cpp 
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [关键字](../cpp/keywords-cpp.md)