---
title: "如何：在 C++/CLI 中使用属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "属性 [C++], 简单"
  - "简单属性"
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文在 C\+\+\/CLI 演示如何使用属性。  
  
## 基本属性  
 对于基本属性这些该仅分配并检索这些成员无需显式定义 get 和 set 访问函数的专用数据，因为编译器将自动提供它们，同时使这些属性的数据类型。  此代码演示的基本属性：  
  
```  
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
  
 **Output**  
  
  **C\# 范围\>为 111**   
## 静态属性  
 此代码示例演示如何声明和使用静态属性。静态属性来只访问其类的静态成员。  
  
```  
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
  
 **Output**  
  
  **96**  
**47**   
## 索引属性  
 索引属性通常公开使用具有写在下方的运算符，访问数据结构。  
  
 如果要使用默认索引属性，则可以引用类名访问数据结构，但是，如果要使用用户定义的和带索引的属性，必须指定属性名访问数据结构。  
  
 使用 `this` 指针，有关如何访问默认索引器的信息，请参见 [此指针在值和引用类型中的语义](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md)。  
  
 有关如何使用 C\# 编写的索引数的信息，请参见 [如何：使用 C\# 索引器](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md)。  
  
 此代码示例演示如何使用默认的和用户定义索引的属性：  
  
```  
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
  
 **Output**  
  
  **\[ 0 1 2 3 4 \]**  
**\[ 0 2 4 6 8 \]** 使用 `this` 指针，下示例演示如何调用默认索引器。  
  
```  
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
  
```  
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
  
 下面的示例使用在前面示例中创建的元数据。  
  
```  
// consume_default_indexer.cpp  
// compile with: /clr  
#using "specify_default_indexer.dll"  
int main() {  
   Squares ^ square = gcnew Squares();  
   System::Console::WriteLine("{0}", square[3]);  
}  
```  
  
 **Output**  
  
 **9**   
## 虚拟属性  
 此代码示例演示如何声明和使用虚拟属性：  
  
```  
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
  
 **Output**  
  
  **93**  
**43**   
## 抽象类和封装的属性  
 虽然和 [abstract](../windows/abstract-cpp-component-extensions.md)[sealed](../windows/sealed-cpp-component-extensions.md) 关键字指定有效的。ECMA C\+\+\/CLI 规范，Visual C\+\+ 编译器的，不能指定这些在常用的属性，也不在一个重要的属性声明。  
  
 若要声明一个密封的抽象或属性，在 get 和 set 访问器函数定义必须一个重要属性然后指定 `abstract` 或 `sealed` 关键字。  
  
```  
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
  
 **Output**  
  
  **86**  
**87**   
## 多维属性  
 可以将多维属性定义特性参数的非标准编号的访问器方法。  
  
```  
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
  
 **Output**  
  
  **1.1**   
## 重载属性访问器  
 下面的示例演示如何重载索引属性。  
  
```  
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
  
 **Output**  
  
  **3.4**  
**6.8**   
## 请参阅  
 [属性](../windows/property-cpp-component-extensions.md)