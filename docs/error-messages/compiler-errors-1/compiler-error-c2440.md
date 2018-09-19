---
title: 编译器错误 C2440 |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2440
dev_langs:
- C++
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80107f3adf4b460fd2563026a1b7ff6ab6394167
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091213"
---
# <a name="compiler-error-c2440"></a>编译器错误 C2440

conversion： 无法从 type1 转换为 type2

编译器不能强制转换从`type1`到`type2`。

## <a name="example"></a>示例

如果你尝试初始化非常量会导致 C2440 `char*` (或`wchar_t*`) 通过使用 c + + 代码中的字符串文字时编译器一致性选项[/zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)设置。 在 C 中，字符串文字的类型是数组`char`，但在 c + +，它是数组`const char`。 此示例生成 C2440:

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

如果你尝试将一个指针转换为成员添加到 void *，也会导致 C2440。 下一步的示例生成 C2440:

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

如果你尝试从只向前声明但未定义的类型强制转换还会导致 C2440。 此示例生成 C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}

```

## <a name="example"></a>示例

第 15 和 16 的下一个示例行上的 C2440 错误限定与`Incompatible calling conventions for UDT return value`消息。 一个*UDT*是用户定义类型，如类、 结构或联合。 UDT 的调用约定指定与实际的调用约定的 udt 并且涉及函数指针前向声明冲突的返回类型中，会导致这些类型的不兼容性错误。

在示例中，首先有某结构和函数返回该结构中; 前向声明编译器将假定该结构使用 c + + 调用约定。 接下来结构定义，其中，默认情况下，使用 C 调用约定。 因为编译器不知道该结构的调用约定，直到它完成读取整个结构中的返回类型的结构的调用约定`get_c2`也被假定为 c + +。

该结构后跟另一个返回该结构的函数声明，但此时，编译器知道该结构的调用约定为 c + +。 同样，函数指针，它返回该结构，定义在结构定义之后，以便让编译器知道该结构使用 c + + 调用约定。

若要解决由于不兼容调用约定而发生的 C2440，声明在 UDT 定义之后返回 UDT 的函数。

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

如果将零分配给内部指针，也可能出现 C2440:

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

错误使用的用户定义的转换也可能出现 C2440。 例如，如果转换运算符具有已定义为`explicit`，编译器不能将其隐式转换。 有关用户定义的转换的详细信息，请参阅[用户定义的转换 (C + + CLI)](../../dotnet/user-defined-conversions-cpp-cli.md))。 此示例生成 C2440:

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

如果你尝试创建其类型为的 Visual c + + 数组的实例，也可能出现 C2440 <xref:System.Array>。  有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  下一步的示例生成 C2440:

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

特性功能中的更改也会导致 C2440。  下面的示例生成 C2440。

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>示例

Visual c + + 编译器不再允许[const_cast 运算符](../../cpp/const-cast-operator.md)向下强制转换时使用的源代码 **/clr**编译编程。

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

为 Visual Studio 2015 Update 3 中的编译器符合性更改会导致 C2440。 以前，编译器错误地处理某些非重复表达式为相同的类型标识的模板匹配项时`static_cast`操作。 现在，编译器正确区分类型和代码的依赖以前`static_cast`行为已中断。 若要解决此问题，请更改要匹配的模板参数类型，或使用的模板自变量`reinterpret_cast`或 C 样式强制转换。

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

## <a name="example"></a>示例

### <a name="copy-list-initialization"></a>复制列表初始化

Visual Studio 2017 和更高版本正确引发与使用 Visual Studio 2015 中已不捕获并可能导致故障的初始值设定项列表的对象创建相关的编译器错误或未定义的运行时行为。 在 C + + 17 复制列表初始化，编译器需要考虑用于重载决策的显式构造函数，但如果实际选择该重载必须引发错误。

在 Visual Studio 2015，但在 Visual Studio 2017 中不会编译下面的示例。

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

为更正此错误，应使用直接初始化：

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

## <a name="example"></a>示例

### <a name="cv-qualifiers-in-class-construction"></a>类构造中的 cv 限定符

在 Visual Studio 2015 中，编译器有时会在通过构造函数调用生成类对象时错误地忽略 cv 限定符。 这可能会导致故障或意外的运行时行为。 下面的示例在 Visual Studio 2015 中编译，但引发了编译器错误在 Visual Studio 2017 及更高版本：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正此错误，将运算符 int() 声明为 const。
