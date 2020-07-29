---
title: 如何：在 C++/CLI 中使用 safe_cast
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: 56ac19871bcdc5162b959f6d60103387551ac2a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225652"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>如何：在 C++/CLI 中使用 safe_cast

本文介绍如何在 c + +/CLI 应用程序中使用 safe_cast。 有关 c + +/CX 中 safe_cast 的信息，请参阅[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)。

## <a name="upcasting"></a>向上转换

向上转换是指从派生类型转换为它的一个基类的转换。 此强制转换是安全的，不需要显式强制转换表示法。 下面的示例演示如何使用和不使用来执行向上转换 `safe_cast` 。

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Downcasting

向下转换是从基类转换为派生自基类的类。  仅当在运行时寻址的对象实际寻址派生的类对象时，向下转换是安全的。  与不同 **`static_cast`** ， `safe_cast` 执行动态检查，并 <xref:System.InvalidCastException> 在转换失败时引发。

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>用户定义的转换的 safe_cast

下一个示例演示如何使用 `safe_cast` 来调用用户定义的转换。

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>safe_cast 和装箱操作

### <a name="boxing"></a>装箱

装箱定义为编译器插入的用户定义的转换。  因此，您可以使用在 `safe_cast` CLR 堆上对值进行框。

下面的示例演示具有简单的和用户定义的值类型的装箱。  一个 `safe_cast` 框，它是本机堆栈上的值类型变量，以便可以将其分配给垃圾回收堆上的变量。

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

下一个示例显示，装箱的优先级高于操作中的用户定义的转换 `safe_cast` 。

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>取消装箱

取消装箱定义为编译器插入的用户定义的转换。  因此，您可以使用 `safe_cast` 对 CLR 堆上的值进行取消装箱。

取消装箱是用户定义的转换，但不同于装箱，取消装箱必须是显式的，也就是说，它必须由 **`static_cast`** 、C 样式强制转换执行， `safe_cast` 否则不能隐式执行取消装箱。

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

下面的示例演示如何取消装箱，其中包含值类型和基元类型。

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>safe_cast 和泛型类型

下一个示例演示如何使用 `safe_cast` 执行与泛型类型的向下转换。

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>另请参阅

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
