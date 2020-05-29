---
title: using 声明
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: d762ea36e83d2384b7bb50c2914f6a634c134d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187838"
---
# <a name="using-declaration"></a>using 声明

**Using**声明将一个名称引入声明性区域，其中显示了 using 声明。

## <a name="syntax"></a>语法

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>parameters

*嵌套名称说明符*命名空间、类或枚举名称与范围解析运算符（：:)，由范围解析运算符终止的序列。 单个范围解析运算符可用于引入全局命名空间的名称。 关键字**typename**是可选的，可用于在从基类引入类模板时解析依赖名称。

*非限定 id*非限定 id 表达式，可以是标识符、重载运算符名称、用户定义的文本运算符或转换函数名称、类析构函数名称或模板名称和参数列表。

*声明符-列表*一个逗号分隔列表，其中列出了 [**typename**]*嵌套名称说明符*非*限定 id*声明符，后面跟有省略号。

## <a name="remarks"></a>备注

使用声明会将非限定名称引入到在其他位置声明的实体的同义词。 它允许使用特定命名空间中的单个名称，而无需在其出现的声明区域中进行显式限定。 这与[using 指令](../cpp/namespaces-cpp.md#using_directives)相反，后者允许使用命名空间中的*所有*名称而无需进行限定。 **Using**关键字还用于[类型别名](../cpp/aliases-and-typedefs-cpp.md)。

## <a name="example"></a>示例

使用声明可在类定义中使用。

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

用于声明成员时，using 声明必须引用基类的成员。

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

使用 using 声明声明的成员可以通过使用显式限定来引用。 `::` 前缀引用全局命名空间。

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

当使用声明时，由声明创建的同义词只引用在使用声明点有效的定义。 在 using 声明后面添加到命名空间的定义是无效同义词。

**使用**声明定义的名称是其原始名称的别名。 它不会影响原始声明的类型、链接或其他特性。

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

对于命名空间中的函数，如果声明区域中提供了一组本地声明和使用单个名称的声明，则它们必须引用同一实体，或者它们必须都引用函数。

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

在上面的示例中，`using B::i` 语句导致第二个 `int i` 在 `g()` 函数中声明。 `using B::f` 语句与 `f(char)` 函数不冲突，因为 `B::f` 引入的函数名称具有不同的参数类型。

## <a name="example"></a>示例

局部函数声明不能与使用声明引入的函数具有相同的名称和类型。 例如：

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

就继承而言，当 using 声明将基类中的名称引入派生类作用域时，派生类中的成员函数会重写基类中具有相同名称和参数类型的虚拟成员函数。

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

使用声明中提到的名称的所有实例都必须是可访问的。 特别是，如果派生类使用 using 声明访问基类的成员，则该成员名称必须是可访问的。 如果名称是重载成员函数的名称，则所有名为的函数都必须是可访问的。

有关成员的可访问性的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。

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

## <a name="see-also"></a>另请参阅

[命名空间](../cpp/namespaces-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
