---
title: 编译器错误 C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 75b2ba62182a33137b433c836b4acf7c9e1fc231
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207974"
---
# <a name="compiler-error-c2440"></a>编译器错误 C2440

"转换"：不能从 "type1" 转换为 "type2"

编译器无法从强制转换 `type1` 为 `type2` 。

## <a name="example"></a>示例

如果在 **`char*`** `wchar_t*` 设置编译器一致性选项[/zc： strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)时尝试使用 c + + 代码中的字符串来初始化非常量（或），则可能会导致 C2440。 在 C 中，字符串文本的类型为的数组 **`char`** ，但在 c + + 中，它是的数组 `const char` 。 此示例生成 C2440：

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

如果尝试将指向成员的指针转换为 void *，也会导致 C2440。 下一个示例生成 C2440：

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

如果尝试强制转换类型，而该类型只是已声明但未定义的类型，则也会导致 C2440。 此示例生成 C2440：

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

## <a name="example"></a>示例

下一个示例中第15行和第16行的 C2440 错误都是通过消息进行限定的 `Incompatible calling conventions for UDT return value` 。 *UDT*是用户定义的类型，如类、结构或联合。 当前向声明的返回类型中指定的 UDT 的调用约定与 UDT 的实际调用约定冲突以及涉及函数指针时，将导致这种不兼容性错误。

在此示例中，第一个结构和一个返回该结构的函数的前向声明;编译器假定结构使用 c + + 调用约定。 接下来是结构定义，默认情况下使用 C 调用约定。 由于编译器不知道结构的调用约定，直到它完成整个结构的读取，因此的返回类型中的结构的调用约定 `get_c2` 也假设为 c + +。

结构后跟另一个返回该结构的函数声明，但此时编译器知道该结构的调用约定为 c + +。 同样，返回该结构的函数指针在 struct 定义之后定义，以便编译器知道该结构使用 c + + 调用约定。

若要解决由于调用约定不兼容而发生的 C2440，请在 UDT 定义之后声明返回 UDT 的函数。

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

如果将零赋给内部指针，也会出现 C2440：

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

如果不正确地使用用户定义的转换，也会出现 C2440。 例如，当转换运算符定义为时 **`explicit`** ，编译器不能在隐式转换中使用它。 有关用户定义的转换的详细信息，请参阅[用户定义的转换（c + +/cli）](../../dotnet/user-defined-conversions-cpp-cli.md)。 此示例生成 C2440：

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

如果尝试创建类型为的 Visual C++ 数组的实例，也可能出现 C2440 <xref:System.Array> 。  有关详细信息，请参阅 [array](../../extensions/arrays-cpp-component-extensions.md)。  下一个示例生成 C2440：

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

由于特性功能发生更改，也可能出现 C2440。  下面的示例生成 C2440。

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>示例

当编译使用 **/clr**编程的源代码时，Microsoft c + + 编译器不再允许[const_cast 运算符](../../cpp/const-cast-operator.md)向下转换。

若要解决此 C2440，请使用正确的强制转换运算符。 有关详细信息，请参阅[强制转换运算符](../../cpp/casting-operators.md)。

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

## <a name="example"></a>示例

由于 Visual Studio 2015 Update 3 中对编译器进行了一致性更改，导致出现 C2440。 以前，编译器在标识操作的模板匹配项时将某些非重复表达式错误地处理为同一类型 **`static_cast`** 。 现在，编译器会正确区分类型，而依赖于先前行为的代码 **`static_cast`** 会中断。 若要解决此问题，请将模板参数更改为与模板参数类型匹配，或使用 **`reinterpret_cast`** 或 C 样式强制转换。

此示例生成 C2440：

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

Visual Studio 2017 和更高版本使用未在 Visual Studio 2015 中捕获的初始值设定项列表正确地引发与对象创建相关的编译器错误，并可能导致崩溃或未定义的运行时行为。 在 c + + 17 的复制列表初始化中，要求编译器考虑用于重载决策的显式构造函数，但如果实际选择了该重载，则必须引发错误。

下面的示例在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中未进行编译。

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

在 Visual Studio 2015 中，编译器有时会在通过构造函数调用生成类对象时错误地忽略 cv 限定符。 这可能会导致故障或意外的运行时行为。 下面的示例在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 和更高版本中引发编译器错误：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正此错误，将运算符 int() 声明为 const。
