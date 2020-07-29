---
title: 如何：在 C++/CLI 中使用属性
ms.date: 07/21/2017
helpviewer_keywords:
- simple properties
- properties [C++], simple
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
ms.openlocfilehash: 2b5543e9a9ff70e827778adf2aee89cbc96f0c1d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225665"
---
# <a name="how-to-use-properties-in-ccli"></a>如何：在 C++/CLI 中使用属性

本文介绍如何使用 c + +/CLI 中的属性

## <a name="basic-properties"></a>基本属性

对于基本属性（仅分配和检索专用数据成员的属性），无需显式定义 get 和 set 访问器函数，因为当给定仅提供属性的数据类型时，编译器会自动提供函数。 此代码演示了一个基本属性：

```cpp
// SimpleProperties.cpp
// compile with: /clr
using namespace System;

ref class C {
public:
   property int Size;
};

int main() {
   C^ c = gcnew C;
   c->Size = 111;
   Console::WriteLine("c->Size = {0}", c->Size);
}
```

```Output
c->Size = 111
```

## <a name="static-properties"></a>静态属性

此代码示例演示如何声明和使用静态属性。  静态属性只能访问其类的静态成员。

```cpp
// mcppv2_property_3.cpp
// compile with: /clr
using namespace System;

ref class StaticProperties {
   static int MyInt;
   static int MyInt2;

public:
   static property int Static_Data_Member_Property;

   static property int Static_Block_Property {
      int get() {
         return MyInt;
      }

      void set(int value) {
         MyInt = value;
      }
   }
};

int main() {
   StaticProperties::Static_Data_Member_Property = 96;
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);

   StaticProperties::Static_Block_Property = 47;
   Console::WriteLine(StaticProperties::Static_Block_Property);
}
```

```Output
96
47
```

## <a name="indexed-properties"></a>索引属性

索引属性通常公开通过使用下标运算符访问的数据结构。

如果使用默认的索引属性，只需引用类名即可访问数据结构，但如果使用用户定义的索引属性，则必须指定属性名称以访问数据结构。

有关如何使用以 c # 编写的索引器的信息，请参阅[如何：使用 c # 索引器（c + +/cli）](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md)。

此代码示例演示如何使用默认的和用户定义的索引属性：

```cpp
// mcppv2_property_2.cpp
// compile with: /clr
using namespace System;
public ref class C {
   array<int>^ MyArr;

public:
   C() {
      MyArr = gcnew array<int>(5);
   }

   // default indexer
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }

   // user-defined indexer
   property int indexer1[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};

int main() {
   C ^ MyC = gcnew C();

   // use the default indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC[i] = i;
      Console::Write("{0} ", MyC[i]);
   }

   Console::WriteLine("]");

   // use the user-defined indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC->indexer1[i] = i * 2;
      Console::Write("{0} ", MyC->indexer1[i]);
   }

   Console::WriteLine("]");
}
```

```Output
[ 0 1 2 3 4 ]
[ 0 2 4 6 8 ]
```

下一个示例演示如何使用指针调用默认索引器 **`this`** 。

```cpp
// call_default_indexer_through_this_pointer.cpp
// compile with: /clr /c
value class Position {
public:
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {
      this->default[x, y] = 1;
   }

   property int default[int, int] {
      int get(int x, int y) {
         return position[x, y];
      }

      void set(int x, int y, int value) {}
   }

private:
   array<int, 2> ^ position;
};
```

此示例演示如何使用 <xref:System.Reflection.DefaultMemberAttribute> 指定默认索引器：

```cpp
// specify_default_indexer.cpp
// compile with: /LD /clr
using namespace System;
[Reflection::DefaultMember("XXX")]
public ref struct Squares {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};
```

下一个示例使用上一示例中创建的元数据。

```cpp
// consume_default_indexer.cpp
// compile with: /clr
#using "specify_default_indexer.dll"
int main() {
   Squares ^ square = gcnew Squares();
   System::Console::WriteLine("{0}", square[3]);
}
```

```Output
9
```

## <a name="virtual-properties"></a>虚拟属性

此代码示例演示如何声明和使用虚拟属性：

```cpp
// mcppv2_property_4.cpp
// compile with: /clr
using namespace System;
interface struct IEFace {
public:
   property int VirtualProperty1;
   property int VirtualProperty2 {
      int get();
      void set(int i);
   }
};

// implement virtual events
ref class PropImpl : public IEFace {
   int MyInt;
public:
   virtual property int VirtualProperty1;

   virtual property int VirtualProperty2 {
      int get() {
         return MyInt;
      }
      void set(int i) {
         MyInt = i;
      }
   }
};

int main() {
   PropImpl ^ MyPI = gcnew PropImpl();
   MyPI->VirtualProperty1 = 93;
   Console::WriteLine(MyPI->VirtualProperty1);

   MyPI->VirtualProperty2 = 43;
   Console::WriteLine(MyPI->VirtualProperty2);
}
```

```Output
93
43
```

## <a name="abstract-and-sealed-properties"></a>抽象属性和密封属性

尽管在 ECMA c + +/CLI 规范中将[abstract](../extensions/abstract-cpp-component-extensions.md)和[sealed](../extensions/sealed-cpp-component-extensions.md)关键字指定为有效，但对于 Microsoft c + + 编译器，不能在普通属性上指定它们，也不能在非普通属性的属性声明上指定它们。

若要声明密封属性或抽象属性，必须定义一个非常重要的属性，然后 **`abstract`** **`sealed`** 在 get 和 set 访问器函数上指定或关键字。

```cpp
// properties_abstract_sealed.cpp
// compile with: /clr
ref struct A {
protected:
   int m_i;

public:
   A() { m_i = 87; }

   // define abstract property
   property int Prop_1 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }
};

ref struct B : A {
private:
   int m_i;

public:
   B() { m_i = 86; }

   // implement abstract property
   property int Prop_1 {
      virtual int get() override { return m_i; }
      virtual void set(int i) override { m_i = i; }
   }
};

ref struct C {
private:
   int m_i;

public:
   C() { m_i = 87; }

   // define sealed property
   property int Prop_2 {
      virtual int get() sealed { return m_i; }
      virtual void set(int i) sealed { m_i = i; };
   }
};

int main() {
   B b1;
   // call implementation of abstract property
   System::Console::WriteLine(b1.Prop_1);

   C c1;
   // call sealed property
   System::Console::WriteLine(c1.Prop_2);
}
```

```Output
86
87
```

## <a name="multidimensional-properties"></a>多维属性

可以使用多维属性定义采用非标准数量参数的属性访问器方法。

```cpp
// mcppv2_property_5.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0) {}
   property double MultiDimProp[int, int, int] {
      double get(int, int, int) {
         return d;
      }
      void set(int i, int j, int k, double l) {
         // do something with those ints
         d = l;
      }
   }

   property double MultiDimProp2[int] {
      double get(int) {
         return d;
      }
      void set(int i, double l) {
         // do something with those ints
         d = l;
      }
   }

};

int main() {
   X ^ MyX = gcnew X();
   MyX->MultiDimProp[0,0,0] = 1.1;
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);
}
```

```Output
1.1
```

## <a name="overloading-property-accessors"></a>重载属性访问器

下面的示例演示如何重载索引属性。

```cpp
// mcppv2_property_6.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0.0) {}
   property double MyProp[int] {
      double get(int i) {
         return d;
      }

      double get(System::String ^ i) {
         return 2*d;
      }

      void set(int i, double l) {
         d = i * l;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   MyX->MyProp[2] = 1.7;
   System::Console::WriteLine(MyX->MyProp[1]);
   System::Console::WriteLine(MyX->MyProp["test"]);
}
```

```Output
3.4
6.8
```

## <a name="see-also"></a>另请参阅

[property](../extensions/property-cpp-component-extensions.md)
