---
title: "用户定义的转换 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 329461338579dc0787c6e3d208abac89ec762004
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-conversions-ccli"></a>用户定义的转换 (C++/CLI)
本部分讨论用户定义的转换 (UDC) 中转换的类型之一时引用或值类型或引用类型的实例。  
  
## <a name="implicit-and-explicit-conversions"></a>隐式和显式转换  
 用户定义的转换可以是隐式或显式。  UDC 应是隐式的如果转换不会导致信息丢失。 否则应定义显式 UDC。  
  
 本机类的构造函数可用来将引用或值类型转换为本机类。  
  
 有关转换的详细信息，请参阅[装箱](../windows/boxing-cpp-component-extensions.md)和[标准转换](../cpp/standard-conversions.md)。  
  
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
  
 **输出**  
  
```Output  
in N::N  
in N::N  
```  
  
## <a name="convert-from-operators"></a>转换自运算符  
 转换自运算符从某个其他类的对象创建在其中定义运算符的类的对象。  
  
 标准 c + + 不支持转换自运算符;标准 c + + 实现此目的使用构造函数。 但是，使用 CLR 类型时，Visual c + + 调用转换自运算符提供语法支持。  
  
 若要很好地与其他符合 cls 的语言进行互操作，你可能希望使用相应的转换自运算符包装给定类每个用户定义的一元构造函数。  
  
 转换自运算符：  
  
-   应将定义为静态函数。  
  
-   可以是 （对于不会丢失精度如 short int 的转换） 隐式或显式转换时可能发生精度损失。  
  
-   应返回的包含类的对象。  
  
-   应具有唯一的参数类型为"从"类型。  
  
 下面的示例演示一个隐式和显式"转换自"、 用户定义的转换 (UDC) 运算符。  
  
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
  
 **输出**  
  
```Output  
in operator  
in constructor  
10  
1  
```  
  
## <a name="convert-to-operators"></a>转换为运算符  
 转换为运算符转换在其中定义了此运算符与某些其他对象的类的对象。 下面的示例演示隐式的转换为，用户定义的转换运算符：  
  
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
  
 **输出**  
  
```Output  
10  
```  
  
 显式用户定义转换为转换运算符是适用于可能会丢失在某种程度的数据的转换。 若要调用的显式转换为运算符，必须使用强制转换。  
  
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
  
 **输出**  
  
```Output  
10.3  
10  
```  
  
## <a name="to-convert-generic-classes"></a>要转换泛型类  
 可以将一个泛型类转换为 t。  
  
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
  
 **输出**  
  
```Output  
True  
```  
  
 转换构造函数接受一个，并使用它来创建对象。  使用直接初始化; 仅调用转换构造函数强制转换将不会调用转换构造函数。 默认情况下，转换构造函数是 CLR 类型显式的。  
  
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
  
 **输出**  
  
```Output  
5  
R  
```  
  
 在此代码示例中，静态的隐式转换函数执行同样的操作在作为显式转换构造函数。  
  
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
  
## <a name="see-also"></a>请参阅  
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)