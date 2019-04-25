---
title: 编译器错误 C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: 1920af8873578c63ab768dae4bcdf4d91fe7cd57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164808"
---
# <a name="compiler-error-c2668"></a>编译器错误 C2668

function： 对重载函数的调用不明确

无法解析指定的重载的函数调用。 您可能想要将一个或多个实参显式转换。

此外可以通过模板使用收到此错误。 如果在同一类中，有的常规成员函数和具有相同签名的模板化的成员函数，模板化一个必须出现在最前面。 这是一个限制视觉对象的当前实现的C++。

## <a name="example"></a>示例

下面的示例生成 C2668:

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

若要解决此错误的另一种方法是使用[using 声明](../../cpp/using-declaration.md):

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

此外可以为 Visual Studio.NET 2003年执行的编译器一致性工作生成此错误： 强制转换为常量 0 上的不明确转换。

由于 int 需要这两个到转换长时间和为 void *，强制转换使用常量 0 上的转换不明确。 若要解决此错误，强制转换到它要使用的以便执行所需的任何转换的函数参数的确切类型 0 (此代码将是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的视觉对象中C++)。

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

由于 CRT 现在具有 float 和 double 形式的所有数学函数，则可能出现此错误。

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

由于 pow （int，int） 已从 CRT 中的 math.h 中删除，可能出现此错误。

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>示例

此代码在 Visual Studio 2015 中成功，但在 Visual Studio 2017 和更高版本与 C2668 将失败。 在 Visual Studio 2015 中，编译器以与常规复制初始化相同的方式错误地处理复制列表初始化；它只考虑将转换构造函数用于重载决策。

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