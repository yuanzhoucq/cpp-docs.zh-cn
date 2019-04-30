---
title: 编译器错误 C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 0310f20854185a6f8a5ccb0ce7b087c4d7c5f29d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387059"
---
# <a name="compiler-error-c2259"></a>编译器错误 C2259

class： 不能实例化抽象类

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

无论何时从接口派生，并在具有非公共访问权限的派生类中实现接口方法，您可能会收到 C2259。  这是因为编译器需要具有公共访问权限在派生类中实现的接口方法。 当实现具有限制性更强的访问权限的接口的成员函数时，编译器不考虑它们是在界面中，这会使派生的类的抽象类定义的接口方法的实现。

有两个可能的问题的解决方法：

- 公开的访问权限，实现方法。

- 在派生类中实现的接口方法的使用范围解析运算符来限定实现的方法的接口的名称的名称。

已完成的视觉对象中的一致性工作也可能导致 C2259 C++ 2005 中， **/zc: wchar_t**默认情况下目前所在。 在此情况下，可被解析可以通过使用编译 C2599 **/zc: wchar_t-**，以获得的行为，从早期版本中，或最好是通过更新您的类型，使它们是否兼容。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

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
