---
title: "用户定义的转换 (C++/CLI) | Microsoft Docs"
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
  - "用户定义的转换 [C++]"
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用户定义的转换 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当某个类型在转换为值类型或引用类型的引用或实例时，本节讨论用户定义的转换 \(UDC\)。  
  
## 隐式转换和显式转换  
 用户定义的转换是隐式转换或显式的。转换，不会导致信息丢失，UDC 应是隐式的。  否则应定义显式 UDC。  
  
 本机类的构造函数只能用于转换引用或值类型对本机类。  
  
 有关指针转换的更多信息，请参见[装箱](../windows/boxing-cpp-component-extensions.md) 和 [标准转换](../cpp/standard-conversions.md)。  
  
```  
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
  
 **Output**  
  
  **在 N::N**  
**在 N::N**   
## 转换自运算符  
 转换从运算符创建运算符从其他某类对象定义类的对象。  
  
 标准 C\+\+ 转换不从运算符支持；标准 C\+\+ 使用构造函数。为此  但是，在中，如果使用 CLR 类型时，Visual C\+\+ 为调用提供语法支持转换从运算符。  
  
 与其他符合 CLS 的语言兼容，则要好可能需要将特定类的每个用户定义元的构造函数具有转换对应从运算符。  
  
 转换自运算符  
  
-   将定义为静态函数。  
  
-   可能为隐式 \(对于不丢失精度如短对 int\) 的转换或显式的，如果可能，都有精度时丢失。  
  
-   将返回一类的对象。  
  
-   将会获得“从”类型作为唯一的参数类型。  
  
 下面的示例演示一个隐式和显式转换“从”，用户定义的转换运算符。\(UDC\)  
  
```  
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
  
 **Output**  
  
  **in 运算符**  
**构造函数中**  
**10**  
**1**   
## 转换为运算符  
 转换对运算符将转换运算符定义对其他对象的类的对象。  下面的示例演示一个隐式转换，对，用户定义的转换运算符：  
  
```  
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
  
 **Output**  
  
  **10** 显式用户定义转换对转换运算符。在某方面可能会丢失数据的转换为相应的。  若要调用显式转换对运算符，必须使用强制转换。  
  
```  
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
  
 **Output**  
  
  **10.3**  
**10**   
## 转换泛型类  
 可以转换泛型类为 T。  
  
```  
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
  
 **Output**  
  
  **True** 转换的构造函数采用类型并使用它创建一个对象。转换的构造函数只调用直接初始化；转换不会转换构造函数。  默认情况下，变换将构造函数为 CLR 类型是显式的。  
  
```  
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
  
 **Output**  
  
  **5**  
**R** 在此代码示例，隐式的静态转换函数执行和显式转换相同构造函数。  
  
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
  
 **Output**  
  
  **13**  
**12**  
**500**  
**2000**   
## 请参阅  
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)