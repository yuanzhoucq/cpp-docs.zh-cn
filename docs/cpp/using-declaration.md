---
title: 使用声明 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3c2cfb8088ec8b160abeeeda6400f9f109c1722
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462318"
---
# <a name="using-declaration"></a>using 声明
Using 声明引入到在其中的声明性区域的名称将显示使用声明。  
  
## <a name="syntax"></a>语法  
  
```  
using [typename] nested-name-specifier unqualified-id ;  
using declarator-list ;  
```  
  
### <a name="parameters"></a>参数
  
*嵌套名称说明符*  
    一系列命名空间、 类或枚举名称和范围解析运算符 （:），范围解析运算符被终止。 单个作用域解析运算符可能用于引入与全局命名空间的名称。 关键字**typename**是可选的可能用于解析依赖项时从基类引入到类模板的名称。  
  
*非限定 id*  
    非限定的 id-，该表达式可以是标识符、 重载的运算符名称、 用户定义的文本运算符或转换函数名、 类析构函数名称或模板名称和参数列表。  
  
*声明符列表*  
    逗号分隔的列表 [**typename**]*嵌套名称说明符**非限定 id*声明符，可以选择跟省略号。
    
## <a name="remarks"></a>备注  
一个使用声明的实体的同义词形式引入了非限定的名称在其他位置声明。 它允许从特定的命名空间，而无需显式限定它在其中出现的声明区域中使用单一名称。 这是与此相反[using 指令](../cpp/namespaces-cpp.md#using_directives)，它允许*所有*中要使用而无需限定命名空间的名称。 **使用**关键字还用于[类型的别名](../cpp/aliases-and-typedefs-cpp.md)。  
  
## <a name="example"></a>示例  
 一个声明可以使用类定义中。  
  
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
   using B::f;    // B::f(char) is now visible as D::f(char)  
   using B::g;    // B::g(char) is now visible as D::g(char)  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');     // Invokes B::f(char) instead of recursing  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');     // Invokes B::g(char) instead of recursing  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
```Output  
In D::f()  
In B::f()  
In B::g()  
```  
  
## <a name="example"></a>示例  
当用于声明的成员 using 声明必须引用基类的成员。  
  
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
  
```Output  
In B::f()  
```  
  
## <a name="example"></a>示例  
使用 using 声明成员可以使用显式限定引用声明。 `::`前缀引用全局命名空间。  
  
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
   using ::f;   // global f is also visible as X::f  
   using A::g;   // A's g is now visible as X::g 
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
  
```Output  
In h  
In f  
In A::g  
```  
  
## <a name="example"></a>示例  
使用时进行声明，由声明所创建的同义词仅指在使用时有效的定义声明。 定义在使用后添加到命名空间声明不是有效的同义词。  
  
由定义的名称**使用**声明是其原始名称的别名。 它不会影响的类型、 链接或原始声明的其他特性。  
  
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
  
## <a name="example"></a>示例  
对于命名空间，如果本地声明的一组中的函数和使用声明性区域中提供了一个名称，它们必须都引用同一个实体，或者它们必须都引用函数的声明。  
  
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
  
 在上述示例中，`using B::i`语句将导致第二个`int i`中声明`g()`函数。 `using B::f`语句不与冲突`f(char)`函数，因为函数名称引入`B::f`具有不同的参数类型。  
  
## <a name="example"></a>示例  
 本地函数声明不能将作为由 using 声明引入的函数相同的名称和类型。 例如：  
  
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
  
## <a name="example"></a>示例  
 相对于继承时 using, 声明引入了一个名称从基类到派生的类作用域，在派生的类重写虚拟成员函数具有相同名称和参数类型的基类中的成员函数。  
  
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
   pd->f(1);     // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);     // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
```Output  
In D::f(int)  
In B::f(char)  
In B::g  
In D::g(char)  
```  
  
## <a name="example"></a>示例  
使用中所述的名称的所有实例声明必须是可访问。 具体而言，如果派生的类使用 using 声明访问成员的基类的成员名称必须是可访问。 如果名称为的一个重载的成员函数，则名为的所有函数必须都是可访问。  
  
有关可访问性成员的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。  
  
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
  
## <a name="see-also"></a>请参阅  
 [命名空间](../cpp/namespaces-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)