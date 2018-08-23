---
title: 如何： 使用属性中 C + + /cli CLI |Microsoft 文档
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- simple properties
- properties [C++], simple
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4873b7d37ef55c050ef074323c4644e4277f593d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134333"
---
# <a name="how-to-use-properties-in-ccli"></a>如何：在 C++/CLI 中使用属性
这篇文章演示如何使用属性中 C + + /cli CLI。  
  
## <a name="basic-properties"></a>基本属性  
 基本属性-那些只分配和检索的私有数据成员-无需显式定义 get 和 set 访问器函数，因为编译器自动提供它们在给定只是属性的数据类型。 此代码演示了基本属性：  
  
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
 此代码示例演示如何声明和使用静态属性。  静态属性仅可以访问其类的静态成员。  
  
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
  
## <a name="indexed-properties"></a>索引的属性  
 索引的属性通常显示使用下标运算符访问的数据结构。  
  
 如果你使用默认索引属性，你可以访问数据结构，只需通过引用类名称，但如果你使用用户定义的索引的属性，则必须指定要访问的数据结构的属性名称。  
  
 有关如何使用用 C# 编写索引器的信息，请参阅[如何： 使用 C# 索引器 (C + + /cli CLI)](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md)。  
  
 此代码示例演示如何使用默认值和用户定义的索引的属性：  
  
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
  
 下一个示例演示如何通过使用调用的默认索引器`this`指针。  
  
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
  
 此示例演示如何使用<xref:System.Reflection.DefaultMemberAttribute>指定的默认索引器：  
  
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
  
 下一个示例使用在前面的示例中创建的元数据。  
  
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
  
## <a name="abstract-and-sealed-properties"></a>抽象和密封属性  
 尽管[抽象](../windows/abstract-cpp-component-extensions.md)和[密封](../windows/sealed-cpp-component-extensions.md)关键字指定为有效在 ECMA C + + /cli CLI 规范，对于 Visual c + + 编译器，不能指定它们普通属性，也不属性非 trivial 属性的声明。  
  
 若要声明密封的或抽象属性，必须定义非 trivial 属性，然后指定`abstract`或`sealed`关键字为 get 和 set 访问器函数。  
  
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
 多维属性可用于定义采用非标准数目的参数的属性访问器方法。  
  
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
 下面的示例演示如何重载索引的属性。  
  
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
  
## <a name="see-also"></a>请参阅  
 [属性](../windows/property-cpp-component-extensions.md)