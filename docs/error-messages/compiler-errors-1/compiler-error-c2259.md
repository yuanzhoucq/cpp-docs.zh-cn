---
title: "编译器错误 C2259 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2259"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2259"
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2259
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 不能实例化抽象类  
  
 代码声明抽象类或结构的实例。  
  
 无法实例化具有一个或多个纯虚函数的类或结构。  若要实例化派生类的对象，该派生类必须重写每个纯虚函数。  
  
 有关更多信息，请参见[隐式抽象类](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。  
  
 下面的示例生成 C2259：  
  
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
  
 只要从接口派生并在派生类中用公共访问权限之外的访问权限实现接口方法，就可能会收到 C2259。这一错误的发生是因为编译器要求在派生类中实现的接口方法必须具有公共访问权限。  在使用较为严格的访问权限实现接口的成员函数时，编译器并不将其视为接口中定义的接口方法的实现，而这会使派生类成为抽象类。  
  
 对于这一问题，有两种可能的解决方法：  
  
-   将已实现的方法的访问权限变更为公共访问权限。  
  
-   为派生类中实现的接口方法使用范围解析运算符，以便用接口名称来限定已实现方法的名称。  
  
 在 Visual C\+\+ 2005 中执行的一致性工作也可能导致 C2259，默认情况下，**\/Zc:wchar\_t** 现在处于打开状态。  在这种情况下，可通过下列两种方式来解决 C2599 错误：通过使用 **\/Zc:wchar\_t\-** 来编译以获取早期版本行为，或采用更可取的方式，即通过更新类型使这些类型都相互兼容。  有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
 下面的示例生成 C2259：  
  
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
  
 下面的示例生成 C2259：  
  
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
  
 下面的示例生成 C2259：  
  
```  
// C2259d.cpp  
// compile with: /clr:oldSyntax  
public __gc __interface MyInterface {  
   void MyMethod();  
};  
  
__gc class MyDerivedClass : public MyInterface {  
// Uncomment the following line to resolve.  
// public:  
   void MyMethod() {};  
   // or the following line  
   // void MyInterface::MyMethod() {};  
};  
  
int main() {  
   MyDerivedClass *instance = new MyDerivedClass();   // C2259  
}  
```