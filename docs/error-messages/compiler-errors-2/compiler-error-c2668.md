---
title: 编译器错误 C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177152"
---
# <a name="compiler-error-c2668"></a>编译器错误 C2668

"function"：对重载函数的调用不明确

未能解析指定的重载函数调用。 可能需要显式转换一个或多个实际参数。

还可以通过使用模板来获取此错误。 如果在同一个类中，你有一个常规成员函数和一个具有相同签名的模板成员函数，则必须先进行模板化。 这是当前视觉对象C++实现的限制。

## <a name="example"></a>示例

下面的示例生成 C2668：

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>示例

解决此错误的另一种方法是[使用 using 声明](../../cpp/using-declaration.md)：

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>示例

此错误还可能是由于对 Visual Studio .NET 2003 执行的编译器一致性工作引起的，因为对常量0的转换不明确。

使用常量0对强制转换的转换是不明确的，因为 int 要求转换为 long 和 void *。 若要解决此错误，请将0强制转换为其正用于的函数参数的确切类型，以便无需进行转换（此代码将在 Visual Studio .NET 2003 和 visual Studio .NET 版本的 Visual C++studio 中有效）。

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>示例

之所以会出现此错误，是因为 CRT 现在具有所有数学函数的浮点和双精度形式。

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>示例

出现此错误的原因可能是从 CRT 中的 pow （int，int）中删除了它。

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>示例

此代码在 Visual Studio 2015 中成功，但在 Visual Studio 2017 和更高版本中与 C2668 发生故障。 在 Visual Studio 2015 中，编译器以与常规复制初始化相同的方式错误地处理复制列表初始化；它只考虑将转换构造函数用于重载决策。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
