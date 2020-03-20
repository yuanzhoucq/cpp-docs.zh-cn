---
title: 用户定义的转换 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545131"
---
# <a name="user-defined-conversions-ccli"></a>用户定义的转换 (C++/CLI)

本部分讨论在转换中的某个类型是值类型或引用类型的引用或实例时，用户定义的转换（UDC）。

## <a name="implicit-and-explicit-conversions"></a>隐式和显式转换

用户定义的转换可以是隐式的，也可以是显式的。  如果转换不会导致信息丢失，则 UDC 应为隐式。 否则应定义显式 UDC。

本机类的构造函数可用于将引用或值类型转换为本机类。

有关转换的详细信息，请参阅[装箱](../extensions/boxing-cpp-component-extensions.md)和[标准转换](../cpp/standard-conversions.md)。

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**输出**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>转换自运算符

Convert from 运算符创建类的对象，在该对象中，运算符是从某个其他类的对象定义的。

标准C++不支持转换 from 运算符;标准C++版使用构造函数来实现此目的。 但是，在使用 CLR 类型时， C++ Visual 提供对调用转换 from 运算符的语法支持。

若要很好地与其他符合 CLS 的语言进行互操作，你可能希望使用相应的 "转换自" 运算符来包装给定类的每个用户定义的一元构造函数。

转换-从运算符：

- 应定义为静态函数。

- 当可能丢失精度时，可以是隐式的（适用于不会丢失精度的转换，如 short 到 int 的转换）或显式的。

- 应返回包含类的对象。

- 应将 "from" 类型作为唯一参数类型。

下面的示例显示了隐式和显式的 "转换源" （用户定义的转换（UDC）运算符）。

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**输出**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>转换为运算符

Convert to 运算符将向其中定义运算符的类的对象转换为其他某个对象。 下面的示例显示了一个隐式转换到用户定义的转换运算符：

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**输出**

```Output
10
```

显式用户定义的转换到转换运算符适用于可能会以某种方式丢失数据的转换。 若要调用显式转换到运算符，必须使用强制转换。

```cpp
// clr_udc_convert_to_2.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**输出**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>转换泛型类

可以将泛型类转换为 T。

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**输出**

```Output
True
```

转换构造函数采用类型并使用它来创建对象。  只使用直接初始化调用转换构造函数;强制转换不会调用转换构造函数。 默认情况下，转换构造函数对于 CLR 类型是显式的。

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**输出**

```Output
5
R
```

在此代码示例中，隐式静态转换函数与显式转换构造函数具有相同的功能。

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**输出**

```Output
13
12
500
2000
```

## <a name="see-also"></a>另请参阅

[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)
