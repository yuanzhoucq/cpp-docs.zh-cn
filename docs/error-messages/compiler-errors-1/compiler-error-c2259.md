---
title: "编译器错误 C2259 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2259
dev_langs:
- C++
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 0837d8f5e48ccf0de0ba8630801667da2ddb6bfa
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2259"></a>编译器错误 C2259
class︰ 无法实例化的抽象类  
  
 代码声明抽象类或结构的实例。  
  
 无法实例化类或结构具有一个或多个纯虚函数。 若要实例化派生类的对象，派生的类必须重写每个纯虚函数。  
  
 有关详细信息，请参阅[隐式抽象类](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。  
  
 下面的示例生成 C2259:  
  
```  
// C2259.cpp  
// compile with: /c  
class V {  
public:  
   void virtual func() = 0;  
};  
class A : public V {};  
class B : public V {  
public:  
   void func();  
};  
V v;  // C2259, V is an abstract class  
A a;  // C2259, A inherits func() as pure virtual  
B b;  // OK, B defines func()  
```  
  
 只要从接口派生，并在具有非公共访问权限的派生类中实现接口方法，您可能会收到 C2259。  这是因为编译器需要具有公共访问权限的派生类中实现的接口方法。 当实现更为严格的访问权限的接口的成员函数时，编译器不考虑它们可以在接口中，这会使一个抽象类派生的类定义的接口方法的实现。  
  
 有两种可能的问题的解决方法︰  
  
-   公开的访问权限，实现的方法。  
  
-   在派生类中实现的接口方法的使用范围解析运算符来限定实现的方法的接口的名称的名称。  
  
 Visual c + + 2005 中，执行的一致性工作也可能导致 C2259 **/zc: wchar_t**现在默认是打开的。 在此情况下，可被解析或者通过使用编译 C2599 **/Zc:wchar_t-**，以获得的行为，从早期版本中，或最好是通过更新您的类型，使它们互相兼容。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
 下面的示例生成 C2259:  
  
```  
// C2259b.cpp  
// compile with: /c  
#include <windows.h>   
  
class MyClass {  
public:  
   // WCHAR now typedef'ed to wchar_t  
   virtual void func(WCHAR*) = 0;  
};  
  
class MyClass2 : MyClass {  
public:  
   void func(unsigned short*);  
};  
  
MyClass2 x;   // C2259  
  
// OK  
class MyClass3 {  
public:  
   virtual void func(WCHAR*) = 0;  
   virtual void func2(wchar_t*) = 0;  
   virtual void func3(unsigned short*) = 0;  
};  
  
class MyClass4 : MyClass3 {  
public:  
   void func(WCHAR*) {}  
   void func2(wchar_t*) {}  
   void func3(unsigned short*) {}  
};  
  
MyClass4 y;  
```  
  
 下面的示例生成 C2259:  
  
```  
// C2259c.cpp  
// compile with: /clr  
interface class MyInterface {  
   void MyMethod();  
};  
  
ref class MyDerivedClass: public MyInterface {  
private:  
   // Uncomment the following line to resolve.  
   // public:  
   void MyMethod(){}  
   // or the following line  
   // void MyInterface::MyMethod() {};  
};  
  
int main() {  
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259  
}  
```  

