---
title: 如何：定义和使用委托 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: 495ceea6afb222d13953b3a25b7a1c836b299de6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216396"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>如何：定义和使用委托 (C++/CLI)

本文介绍如何在 c + +/CLI 中定义和使用委托。

尽管 .NET Framework 提供了许多委托，但有时你可能需要定义新的委托。

下面的代码示例定义一个名为的委托 `MyCallback` 。 事件处理代码（触发此新委托时调用的函数）的返回类型必须为 **`void`** 并采用 <xref:System.String> 引用。

Main 函数使用定义的静态方法 `SomeClass` 来实例化 `MyCallback` 委托。 然后，委托将成为调用此函数的替代方法，通过将字符串 "single" 发送到委托对象进行演示。 接下来，的其他实例 `MyCallback` 链接在一起，然后通过调用委托对象来执行。

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

下面的代码示例演示如何将委托与值类的成员相关联。

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>如何编写委托

您可以使用 " `-` " 运算符从组合委托中删除组件委托。

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**输出**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>将委托 ^ 传递到需要函数指针的本机函数

从托管组件中，可以使用函数指针参数调用本机函数，其中本机函数随后可以调用托管组件的委托的成员函数。

此示例创建导出本机函数的 .dll：

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

下一个示例使用 .dll，并向需要函数指针的本机函数传递委托句柄。

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**输出**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>将委托与非托管函数关联

若要将委托与本机函数关联，必须将本机函数包装在托管类型中，并声明要通过调用的函数 `PInvoke` 。

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**输出**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>使用未绑定的委托

在调用委托时，可以使用未绑定的委托传递要调用其函数的类型的实例。

如果您想要循环访问集合中的对象（通过[在关键字中](../dotnet/for-each-in.md)使用）并在每个实例上调用成员函数，则未绑定的委托特别有用。

下面介绍了如何声明、实例化和调用绑定委托和未绑定委托：

|操作|绑定委托|未绑定的委托|
|------------|---------------------|-----------------------|
|Declare|委托签名必须与要通过委托调用的函数的签名匹配。|委托签名的第一个参数是 **`this`** 要调用的对象的类型。<br /><br /> 在第一个参数之后，委托签名必须与你要通过委托调用的函数的签名匹配。|
|上述|实例化绑定委托时，可以指定实例函数或全局或静态成员函数。<br /><br /> 若要指定实例函数，第一个参数是要调用其成员函数的类型的实例，第二个参数是要调用的函数的地址。<br /><br /> 如果要调用全局或静态成员函数，只需传递全局函数的名称或静态成员函数的名称。|实例化未绑定的委托时，只需传递要调用的函数的地址。|
|调用|调用绑定委托时，只传递委托签名所需的参数。|与绑定委托相同，但请记住，第一个参数必须是包含要调用的函数的对象的实例。|

此示例演示如何声明、实例化和调用未绑定的委托：

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**输出**

```Output
2
3
2
3
2
7
8
7
8
7
```

下一个示例演示如何使用未绑定的委托，并[在关键字中](../dotnet/for-each-in.md)循环访问集合中的对象并在每个实例上调用成员函数。

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

此示例将创建一个未绑定的委托给属性的访问器函数：

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**输出**

```Output
11
```

下面的示例演示如何调用多播委托，其中一个实例是绑定的，一个实例未绑定。

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**输出**

```Output
in f(R ^ r)
in f()
```

下一个示例演示如何创建和调用未绑定的泛型委托。

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**输出**

```Output
12
14
```

## <a name="see-also"></a>另请参阅

[委托（C++ 组件扩展）](../extensions/delegate-cpp-component-extensions.md)
