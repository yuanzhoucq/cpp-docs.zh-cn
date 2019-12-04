---
title: 编译器错误 C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 403d674eae696eb42a837aef9d6e97c4b5b8f6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758783"
---
# <a name="compiler-error-c2259"></a>编译器错误 C2259

"class"：不能实例化抽象类

代码声明抽象类或结构的实例。

不能使用一个或多个纯虚函数实例化类或结构。 为了实例化派生类的对象，派生类必须重写每个纯虚函数。

有关详细信息，请参阅[隐式抽象类](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)。

下面的示例生成 C2259：

```cpp
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

每当从接口派生并在派生类中实现公共访问权限以外的接口方法时，可能会收到 C2259。  出现这种情况的原因是编译器要求在派生类中实现的接口方法具有公共访问权限。 当你为具有限制性更强的访问权限的接口实现成员函数时，编译器不会将其视为接口中定义的接口方法的实现，这反过来使派生类成为抽象类。

此问题有两种可能的解决方法：

- 为实现的方法公开访问权限。

- 为在派生类中实现的接口方法使用范围解析运算符，以使实现的方法名称符合接口的名称。

C2259 在 Visual Studio 2005、 **/zc： wchar_t**现在默认处于启用状态，因此也可能导致。 在这种情况下，可以通过使用 **/zc： wchar_t**进行编译来解决 C2599，以便从以前的版本获取行为，或通过更新类型使其兼容。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

下面的示例生成 C2259：

```cpp
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

```cpp
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
