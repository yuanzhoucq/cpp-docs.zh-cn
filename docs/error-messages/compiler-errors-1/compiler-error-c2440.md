---
title: "编译器错误 C2440 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2440"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2440"
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# 编译器错误 C2440
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“conversion”: 无法从 “type1”转换到“type2”  
  
 编译器无法从“`type1`”强制转换到“`type2`”。  
  
## 示例  
 如果您在设置了编译器一致性选项 [\/Zc:strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 时通过使用 C\+\+ 代码中的字符串来尝试初始化非常量 `char*`（或 `wchar_t*`），就会导致 C2440。  在 C 中，字符串文本的类型为 `char`，但是在 C\+\+ 中，为 `const` `char` 的数组。  此示例生成 C2440：  
  
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
  
## 示例  
 如果尝试将指向成员的指针转换为 void\*，也可能导致 C2440。  下一个示例生成 C2440：  
  
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
  
## 示例  
 如果您尝试对只做了向前声明但未定义的类型进行强制转换，也会导致 C2440。  此示例生成 C2440：  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## 示例  
 下一个示例的 15 和 16 行上的 C2440 错误用 `Incompatible calling conventions for UDT return value` 消息限定。（UDT 指用户定义的类型，如类、结构或联合。）在前向声明的返回类型中指定的 UDT 调用约定与该 UDT 的实际调用约定有冲突并且涉及函数指针时，会导致上述类型的不兼容性错误。  
  
 在该示例中，首先有某结构和返回该结构的函数的前向声明；编译器假定该结构使用 C\+\+ 调用约定。  下一个是该结构定义，默认情况下，该结构定义使用 C 调用约定。  因为编译器在读完整个结构前，不知道该结构的调用约定，所以也假定在 `get_c2` 的返回类型中该结构的调用约定为 C\+\+。  
  
 该结构后面跟有另一个返回该结构的函数声明，但在此时，编译器知道该结构的调用约定为 C\+\+。  同样，返回该结构的函数指针在结构定义之后定义，所以编译器知道该结构使用 C\+\+ 调用约定。  
  
 若要解决由于不兼容的调用约定而产生的 C2440，请在 UDT 定义之后声明返回 UDT 的函数。  
  
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
  
## 示例  
 如果将零分配给内部指针，也可能出现 C2440：  
  
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
  
## 示例  
 不正确地使用用户定义的转换也可能出现 C2440。  有关用户定义的转换的更多信息，请参阅 [用户定义的转换](../../dotnet/user-defined-conversions-cpp-cli.md)。  此示例生成 C2440：  
  
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
  
## 示例  
 如果尝试创建 Visual C\+\+ 数组的实例，该数组的类型为 <xref:System.Array>，也会出现 C2440。有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。下一个示例生成 C2440：  
  
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
  
## 示例  
 特性功能中的更改也会导致 C2440。下面的示例生成 C2440。  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## 示例  
 对使用 **\/clr** 编程的源代码进行编译时，Visual C\+\+ 编译器不再允许 [const\_cast 运算符](../../cpp/const-cast-operator.md) 向下强制转换。  
  
 若要解决此 C2440，请使用正确的强制转换运算符。  有关详细信息，请参阅[强制转换运算符](../../cpp/casting-operators.md)。  
  
 此示例生成 C2440：  
  
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
  
## 示例  
 使用 **\/clr:oldSyntax** 也会生成 C2440：  
  
```cpp  
// c2440h.cpp  
// compile with: /clr:oldSyntax  
__gc class Base {};  
__gc class Derived : public Base {};  
int main() {  
   Derived *d = new Derived;  
   Base *b = d;  
   d = const_cast<Derived*>(b);   // C2440  
   d = dynamic_cast<Derived*>(b);   // OK  
}  
```