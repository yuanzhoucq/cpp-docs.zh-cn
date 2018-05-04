---
title: 指针到成员运算符:。 * 和-&gt;* |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- .*
- ->*
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdece555ea58f0a1321258405fa76ba02cf12efa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="pointer-to-member-operators--and--gt"></a>指针到成员运算符:。 * 和-&gt;*
## <a name="syntax"></a>语法  
  
```  
expression .* expression  
expression ->* expression  
```  
  
## <a name="remarks"></a>备注  
 指针到成员的指针运算符，。 * 和->\*，返回表达式左侧指定的对象的特定类成员的值。  右侧必须指定该类的成员。  下面的示例演示如何使用这些运算符：  
  
```  
// expre_Expressions_with_Pointer_Member_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
class Testpm {  
public:  
   void m_func1() { cout << "m_func1\n"; }  
   int m_num;  
};  
  
// Define derived types pmfn and pmd.  
// These types are pointers to members m_func1() and  
// m_num, respectively.  
void (Testpm::*pmfn)() = &Testpm::m_func1;  
int Testpm::*pmd = &Testpm::m_num;  
  
int main() {  
   Testpm ATestpm;  
   Testpm *pTestpm = new Testpm;  
  
// Access the member function  
   (ATestpm.*pmfn)();  
   (pTestpm->*pmfn)();   // Parentheses required since * binds  
                        // less tightly than the function call.  
  
// Access the member data  
   ATestpm.*pmd = 1;  
   pTestpm->*pmd = 2;  
  
   cout  << ATestpm.*pmd << endl  
         << pTestpm->*pmd << endl;  
   delete pTestpm;  
}  
```  
  
## <a name="output"></a>输出  
  
```  
m_func1  
m_func1  
1  
2  
```  
  
 在前面的示例中，指向成员的指针 `pmfn` 用于调用成员函数 `m_func1`。 另一个指向成员的指针 `pmd` 用于访问 `m_num` 成员。  
  
 二元运算符 .* 将其第一操作数（必须是类类型的对象）与其第二操作数（必须是指向成员的指针类型）组合在一起。  
  
 二元运算符-> * 将合并其第一个操作数，它必须是指向类类型的对象的指针必须是指向成员的指针类型与其第二个操作数。  
  
 在包含 .* 运算符的表达式中，第一操作数必须是类类型且可访问，而指向第二操作数中指定的成员的指针或可访问类型的成员的指针明确从该类派生并且可供该类访问。  
  
 在表达式中包含-> * 运算符，第一个操作数必须类型的类型"指向类类型"中指定第二个操作数，或它必须派生的类型明确从该类。  
  
## <a name="example"></a>示例  
 考虑以下类和程序段：  
  
```  
// expre_Expressions_with_Pointer_Member_Operators2.cpp  
// C2440 expected  
class BaseClass {  
public:  
   BaseClass(); // Base class constructor.  
   void Func1();  
};  
  
// Declare a pointer to member function Func1.  
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;  
  
class Derived : public BaseClass {  
public:  
   Derived();  // Derived class constructor.  
   void Func2();  
};  
  
// Declare a pointer to member function Func2.  
void (Derived::*pmfnFunc2)() = &Derived::Func2;  
  
int main() {  
   BaseClass ABase;  
   Derived ADerived;  
  
   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.  
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to  
                           // access pointers to members of  
                           // derived classes.   
  
   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously  
                              // derived from BaseClass.   
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.  
}  
```  
  
 结果。 * 或->\*指针到成员运算符是对象或指向成员的指针的声明中指定的类型的函数。 因此，在前面的示例中，表达式 `ADerived.*pmfnFunc1()` 的结果是指向返回 void 的函数的指针。 如果第二操作数是左值，则此结果为左值。  
  
> [!NOTE]
>  如果某个指向成员的指针运算符的结果是函数，则该结果只能用作函数调用运算符的操作数。  
  
## <a name="see-also"></a>请参阅  
 [C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

