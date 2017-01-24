---
title: "using 声明 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "using 声明"
  - "声明命名空间, 命名空间中的非限定名称"
  - "声明 [C++], using 声明"
  - "命名空间 [C++], 中的非限定名称"
  - "using 关键字 [C++]"
  - "声明 [C++], 命名空间"
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# using 声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`using` 声明引入名称到 `using` 说明出现的声明区域。  
  
## 语法  
  
```  
  
      using [typename][::] nested-name-specifier unqualified-id  
using :: unqualified-id  
```  
  
## 备注  
 该名称成为了在其他地方声明的某个实体的同义词。  它允许从特定的命名空间的 *individual* 名称使用，而不需要[显式限定](../misc/explicit-qualification.md)。  与 `using` 指令不同，这允许命名空间中的 *all* 名称无限制地使用。  有关更多信息，请参见[使用指令](../misc/using-directive-cpp.md)。  这个关键字还被用于 [“类型别名”](../cpp/aliases-and-typedefs-cpp.md).  
  
## 示例  
 using 声明可用于类定义。  
  
```cpp  
// using_declaration1.cpp  
#include <stdio.h>  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class D : B {  
public:  
   using B::f;  
   using B::g;  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
  **在D::f\(\)中**  
**In B::f\(\)**  
**在B::g\(\)中**   
## 示例  
 当用于声明成员时，使用的声明必须引用基类的成员。  
  
```cpp  
// using_declaration2.cpp  
#include <stdio.h>  
  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class C {  
public:  
   int g();  
};  
  
class D2 : public B {  
public:  
   using B::f;   // ok: B is a base of D2  
   // using C::g;   // error: C isn't a base of D2  
};  
  
int main() {  
   D2 MyD2;  
   MyD2.f('a');  
}  
```  
  
  **In B::f\(\)**   
## 示例  
 使用显式限定可以引用使用声明声明的成员。  `::` 前缀指的是全局命名空间。  
  
```cpp  
// using_declaration3.cpp  
#include <stdio.h>  
  
void f() {  
   printf_s("In f\n");  
}  
  
namespace A {  
   void g() {  
      printf_s("In A::g\n");  
   }  
}  
  
namespace X {  
   using ::f;   // global f  
   using A::g;   // A's g  
}  
  
void h() {  
   printf_s("In h\n");  
   X::f();   // calls ::f  
   X::g();   // calls A::g  
}  
  
int main() {  
   h();  
}  
```  
  
  **在 h中**  
**在 f中**  
**在 A::g中**   
## 示例  
 当创建 using 声明时，声明创建一个同义词只引用有效的 using 声明来定义。  在使用的声明不是有效同义词后，定义添加到命名空间中。  
  
 通过使用的声明定义的名称为其原始名称的别名。  它不影响原始声明的类型、链接或其他特性。  
  
```cpp  
// post_declaration_namespace_additions.cpp  
// compile with: /c  
namespace A {  
   void f(int) {}  
}  
  
using A::f;   // f is a synonym for A::f(int) only  
  
namespace A {  
   void f(char) {}  
}  
  
void f() {  
   f('a');   // refers to A::f(int), even though A::f(char) exists  
}  
  
void b() {  
   using A::f;   // refers to A::f(int) AND A::f(char)  
   f('a');   // calls A::f(char);  
}  
```  
  
## 示例  
 就命名空间中的函数而言，如果在声明区域中给定一组本地声明，为单个名称使用声明，则其所有必须引用相同的实体或必须引用函数。  
  
```cpp  
// functions_in_namespaces1.cpp  
// C2874 expected  
namespace B {  
    int i;  
    void f(int);  
    void f(double);  
}  
  
void g() {  
    int i;  
    using B::i;   // error: i declared twice  
    void f(char);  
    using B::f;   // ok: each f is a function  
}  
```  
  
 在上面的示例中，在 `g()` 函数中 `using B::i` 语句会导致声明第二个 `int i`。  因为由 `B::f` 介绍的函数名称具有不同的参数类型，`using B::f` 语句不与 `f(char)` 函数发生冲突。  
  
## 示例  
 本地函数声明不能与通过使用声明引入的函数具有相同的名称和类型。  例如：  
  
```cpp  
// functions_in_namespaces2.cpp  
// C2668 expected  
namespace B {  
    void f(int);  
    void f(double);  
}  
  
namespace C {  
    void f(int);  
    void f(double);  
    void f(char);  
}  
  
void h() {  
    using B::f;          // introduces B::f(int) and B::f(double)  
    using C::f;          // C::f(int), C::f(double), and C::f(char)  
    f('h');              // calls C::f(char)  
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?  
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)  
}  
```  
  
## 示例  
 就继承而言，当使用声明从基类将名称为引入派生的类作用域时，派生类中的成员函数将使用相同的名称和基类中的参数类型重写虚拟成员函数。  
  
```cpp  
// using_declaration_inheritance1.cpp  
#include <stdio.h>  
struct B {  
   virtual void f(int) {  
      printf_s("In B::f(int)\n");  
   }  
  
   virtual void f(char) {  
      printf_s("In B::f(char)\n");  
   }  
  
   void g(int) {  
      printf_s("In B::g\n");  
   }  
  
   void h(int);  
};  
  
struct D : B {  
   using B::f;  
   void f(int) {   // ok: D::f(int) overrides B::f(int)  
      printf_s("In D::f(int)\n");  
   }  
  
   using B::g;  
   void g(char) {   // ok: there is no B::g(char)  
      printf_s("In D::g(char)\n");  
   }  
  
   using B::h;  
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)  
};  
  
void f(D* pd) {  
   pd->f(1);   // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);   // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
  **在 D::f\(int\)中**  
**在 B::f\(char\)中**  
**在 B::g中**  
**在 D::g\(char\)中**   
## 示例  
 在 using 声明中提到的名称的所有实例必须是可访问的。  具体来说，如果派生类使用 using 声明访问基类的成员，成员名称必须是可访问的。  如果名称是一个重载成员函数的名称，则所有命名的函数必须是可访问的。  
  
 有关成员辅助性的更多信息，请参见[Member\-Access Control](../cpp/member-access-control-cpp.md)（成员访问控制）。  
  
```cpp  
// using_declaration_inheritance2.cpp  
// C2876 expected  
class A {  
private:  
   void f(char);  
public:  
   void f(int);  
protected:  
   void g();  
};  
  
class B : public A {  
   using A::f;   // C2876: A::f(char) is inaccessible  
public:  
   using A::g;   // B::g is a public synonym for A::g  
};  
```  
  
## 请参阅  
 [命名空间](../cpp/namespaces-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)