---
title: "编译器错误 C2440 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2440
dev_langs:
- C++
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5f0472f7d318de24c38898388906a264cf56db7b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2440"></a>编译器错误 C2440
conversion︰ 不能从 type1 转换到 type2  
  
编译器不能强制转换从`type1`到`type2`。  
  
## <a name="example"></a>示例  
如果您尝试初始化非 const，就会导致 C2440 `char*` (或`wchar_t*`) 通过使用 c + + 代码中的字符串文字时的编译器一致性选项[/zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)设置。 在 C 中，字符串文字的类型是数组`char`，但在 c + +，它是构成的数组`const char`。 此示例生成 C2440:  
  
```cpp  
// C2440s.cpp  
// Build: cl /Zc:strictStrings /W3 C2440s.cpp  
// When built, the compiler emits:  
// error C2440: 'initializing' : cannot convert from 'const char [5]'   
// to 'char *'  
//        Conversion from string literal loses const qualifier (see  
// /Zc:strictStrings)  
  
int main() {  
   char* s1 = "test"; // C2440  
   const char* s2 = "tests"; // OK  
}  
```  
  
## <a name="example"></a>示例  
 如果您尝试将指针转换为 void * 的成员，也可能导致 C2440。 下一步的示例生成 C2440:  
  
```cpp  
// C2440.cpp  
class B {  
public:  
   void  f(){;}  
  
   typedef void (B::*pf)();  
  
   void f2(pf pf) {  
       (this->*pf)();  
       void* pp = (void*)pf;   // C2440  
   }  
  
   void f3() {  
      f2(f);  
   }  
};  
```  
  
## <a name="example"></a>示例  
 如果您尝试从仅前向声明但未定义的类型强制转换，也可能导致 C2440。 此示例生成 C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## <a name="example"></a>示例  
 15 和 16 的下一个采样行上的 C2440 错误使用限定`Incompatible calling conventions for UDT return value`消息。 一个*UDT*是用户定义类型，如类、 结构或联合。 UDT 的调用约定指定与实际的调用约定的用户定义的类型和所涉及的函数指针前向声明冲突的返回类型中，会导致这种不兼容性错误。  
  
 在示例中，第一类是前向声明某结构和结构，则将返回一个函数编译器将假定该结构使用 c + + 调用约定。 接下来结构定义，这在默认情况下，使用 C 调用约定。 因为编译器不知道该结构的调用约定，直到它完成读取整个结构中的返回类型的结构的调用约定`get_c2`还假定为 c + +。  
  
 该结构跟返回该结构的另一个函数声明，但在这种情况下，编译器知道结构的调用约定为 c + +。 同样，函数指针，它将返回该结构，定义在结构定义之后，以便编译器知道该结构使用 c + + 调用约定。  
  
 若要解决由于不兼容的调用约定发生 C2440，声明在 UDT 定义之后返回 UDT 的函数。  
  
```cpp  
// C2440b.cpp  
struct MyStruct;  
  
MyStruct get_c1();  
  
struct MyStruct {  
   int i;  
   static MyStruct get_C2();  
};  
  
MyStruct get_C3();  
  
typedef MyStruct (*FC)();  
  
FC fc1 = &get_c1;   // C2440, line 15  
FC fc2 = &MyStruct::get_C2;   // C2440, line 16  
FC fc3 = &get_C3;  
  
class CMyClass {  
public:  
   explicit CMyClass( int iBar)  
      throw()   {  
   }  
  
   static CMyClass get_c2();  
};  
  
int main() {  
   CMyClass myclass = 2;   // C2440  
   // try one of the following  
   // CMyClass myclass{2};  
   // CMyClass myclass(2);  
  
   int *i;  
   float j;  
   j = (float)i;   // C2440, cannot cast from pointer to int to float  
}  
```  
  
## <a name="example"></a>示例  
 如果将分配给内部指针的零，也可能发生 C2440:  
  
```cpp  
// C2440c.cpp  
// compile with: /clr  
int main() {  
   array<int>^ arr = gcnew array<int>(100);  
   interior_ptr<int> ipi = &arr[0];  
   ipi = 0;   // C2440  
   ipi = nullptr;   // OK  
}  
```  
  
## <a name="example"></a>示例  
 C2440 还可能会导致使用错误的用户定义的转换。 例如，如果转换运算符具有已定义为`explicit`，编译器不能将其隐式转换。 有关用户定义的转换的详细信息，请参阅[用户定义的转换 (C + + /cli CLI)](../../dotnet/user-defined-conversions-cpp-cli.md))。 此示例生成 C2440:  
  
```cpp  
// C2440d.cpp  
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
   int i;  
   i = d;   // C2440  
   // Uncomment the following line to resolve.  
   // i = static_cast<int>(d);  
}  
```  
  
## <a name="example"></a>示例  
 如果您尝试创建一个其类型是一种<xref:System.Array>。</xref:System.Array> Visual c + + 数组的实例，也可能发生 C2440  有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  下一步的示例生成 C2440:  
  
```cpp  
// C2440e.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440  
   // try the following line instead  
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));  
}  
```  
  
## <a name="example"></a>示例  
 属性功能中的更改也会导致 C2440。  下面的示例生成 C2440。  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## <a name="example"></a>示例  
 Visual c + + 编译器不会再允许[const_cast Operator](../../cpp/const-cast-operator.md)向下转换时使用的源代码**/clr**编译编程。  
  
 若要解决此 C2440，请使用正确的强制转换运算符。 有关详细信息，请参阅[强制转换运算符](../../cpp/casting-operators.md)。  
  
 此示例生成 C2440:  
  
```cpp  
// c2440g.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
int main() {  
   Derived ^d = gcnew Derived;  
   Base ^b = d;  
   d = const_cast<Derived^>(b);   // C2440  
   d = dynamic_cast<Derived^>(b);   // OK  
}  
```  
  
## <a name="example"></a>示例  
可以更改会导致 C2440 一致性到 Visual Studio 2015 Update 3 中的编译器。 以前，编译器错误地处理某些不同表达式的类型相同标识的模板匹配项时`static_cast`操作。 现在，编译器正确区分类型和代码，依赖于上一个`static_cast`行为被破坏。 若要修复此问题，请更改模板参数与匹配模板参数类型，或使用`reinterpret_cast`或 C 样式强制转换。
  
此示例生成 C2440:  
  
```cpp  
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3 
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.

```

