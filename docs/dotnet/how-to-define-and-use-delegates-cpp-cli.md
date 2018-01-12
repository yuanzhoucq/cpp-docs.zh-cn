---
title: "如何： 定义和使用委托 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7f400a03f1b9ae877ee7ec681cb038698a92598a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-define-and-use-delegates-ccli"></a>如何：定义和使用委托 (C++/CLI)
这篇文章演示如何定义和使用委托在 C + + /cli CLI。  
  
 尽管.NET Framework 提供了大量的委托，但有时你可能需要定义新委托。  
  
 下面的代码示例定义一个名为的委托`MyCallback`。 事件处理代码-激发此新的委托时调用的函数-必须具有返回类型的`void`并采取<xref:System.String>引用。  
  
 主函数使用静态方法定义的`SomeClass`来实例化`MyCallback`委托。 委托随后将成为调用此函数的另一种方法，通过将字符串"单个"发送到的委托对象所示。 下一步，其他实例`MyCallback`链接在一起，然后执行一次调用的委托对象。  
  
```  
  
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
  
 **输出**  
  
```Output  
static SomeClass::Func - single  
static SomeClass::Func - chained  
static SomeClass::Func - chained  
OtherClass::Method - chained, num = 99  
OtherClass::Method - chained, num = 100  
```  
  
 下一步的代码示例演示如何将委托关联的值类成员。  
  
```  
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
  
 **输出**  
  
```Output  
test  
test  
```  
  
## <a name="how-to-compose-delegates"></a>如何撰写的委托  
 你可以使用"`-`"运算符以从组合的委托移除组件委托。  
  
```  
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
  
## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>将委托传递 ^ 到需要函数指针的本机函数  
 从托管组件你可以调用本机函数使用函数指针参数其中本机函数然后可以调用成员函数的托管的组件的委托。  
  
 此示例将创建.dll 导出本机函数：  
  
```  
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
  
 下一步的示例使用.dll 文件，并将委托句柄传递给需要函数指针的本机函数。  
  
```  
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
  
## <a name="to-associate-delegates-with-unmanaged-functions"></a>若要将委托关联与非托管函数  
 若要将委托与本机函数的关联，必须在托管类型中包装本机函数并声明函数以通过调用`PInvoke`。  
  
```  
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
  
## <a name="to-use-unbound-delegates"></a>若要使用未绑定的委托  
 未绑定的委托可用于将你想要调用时调用的委托的函数的类型的实例传递。  
  
 未绑定的委托将非常有用，如果你想要循环访问集合中的对象-通过使用[对于每个，在](../dotnet/for-each-in.md)关键字-在每个实例中调用成员函数。  
  
 下面介绍了如何声明、 实例化，并调用绑定和未绑定的委托：  
  
|操作|绑定委托|未绑定的委托|  
|------------|---------------------|-----------------------|  
|声明|委托签名必须与你想要通过委托调用的函数的签名匹配。|委托签名的第一个参数是一种`this`你想要调用的对象。<br /><br /> 之后的第一个参数的委托签名必须匹配你想要通过委托调用函数的签名。|  
|实例化|当实例化绑定的委托时，你可以指定一个实例的函数或全局或静态成员函数。<br /><br /> 若要指定实例函数，第一个参数是你想要调用的成员函数的类型的实例和第二个参数是你想要调用的函数的地址。<br /><br /> 如果你想要调用的全局或静态成员函数，只需传递全局函数的名称或静态成员函数的名称。|当实例化未绑定的委托时，只需传递要调用的函数的地址。|  
|调用|在调用绑定的委托时，只需将所需的委托签名的参数传递。|绑定相同委托，但应记住的第一个参数必须是包含你想要调用的函数对象的实例。|  
  
 此示例演示如何声明、 实例化和调用未绑定的委托：  
  
```  
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
  
 下一个示例演示如何使用未绑定的委托和[对于每一个，在](../dotnet/for-each-in.md)关键字来循环访问集合中的对象并对每个实例中调用成员函数。  
  
```  
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
  
 此示例创建一个属性访问器函数未绑定的委托：  
  
```  
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
  
 下面的示例演示如何调用多路广播的委托，绑定一个实例，其中一个实例是未绑定。  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>请参阅  
 [委托（C++ 组件扩展）](../windows/delegate-cpp-component-extensions.md)