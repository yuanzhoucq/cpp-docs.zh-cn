---
title: "如何：在 C++/CLI 中使用 safe_cast | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "safe_cast 关键字 [C++], 向上转换"
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用 safe_cast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示如何在 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 应用程序使用safe\_cast。  有关 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]的 safe\_cast 信息，请参见 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
## 向上转换  
 向上转换是从派生的类型到它基类之一的转换。  此转换是安全的，不需要显式强制转换表示形式。  下面的示例显示如何执行向上转换，使用 `safe_cast`，且不包含它。  
  
```  
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
  
  **在 C::Test**  
**在B::Test**  
**在 C::Test**  
**在B::Test**   
## 向下转换  
 向下转换是从基类到从基类派生的类转换。向下转换是安全的，仅当在运行时寻址的对象实际上正在寻址派生类对象。与 `static_cast`不同，如果转换失败，`safe_cast` 将执行动态检查并引发 <xref:System.InvalidCastException>。  
  
```  
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
  
  **在C::Test\(\)**  
**在C::Test\(\)**  
**在 B::Test2\(\)**   
## 用户定义的转换safe\_cast。  
 下面的示例演示如何使用 `safe_cast` 调用用户定义的转换。  
  
```  
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
  
  **在运算符R^\(V& v**  
**在运算符V^\(R^ r\)**   
## safe\_cast 和装箱操作  
 **装箱**  
  
 装箱定义为编译器注入的，用户定义的转换。因此，可以使用 `safe_cast` 使 CLR 堆上的装箱值。  
  
 下面的示例演示带简单和用户定义的值类型的装箱。`safe_cast` 将在本机堆栈上的值类型变量装箱，以便分配给在垃圾回收堆的变量。  
  
```  
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
  
 下面的示例表示装箱在`safe_cast` 操作中具有在用户定义转换之上的优先级。  
  
```  
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
  
 **取消装箱**  
  
 取消装箱定义为编译器注入的，用户定义的转换。因此，可以使用 `safe_cast` 使 CLR 堆上的值从箱子中取出。  
  
 取消装箱是用户定义转换，但是，不同于装箱，取消装箱是限制级的，必须由 `static_cast`、C 样式转换或 `safe_cast`执行；取消装箱无法隐式执行。  
  
```  
// safe_cast_unboxing.cpp  
// compile with: /clr  
int main() {  
   System::Object ^ o = 42;  
   int x = safe_cast<int>(o);  
}  
```  
  
 下面的示例显示具有值类型和原类型的取消装箱。  
  
```  
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
  
## safe\_cast 和泛型类型  
 下面的示例演示如何使用 `safe_cast` 执行向下转换与泛型类型。  
  
```  
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
  
## 请参阅  
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)