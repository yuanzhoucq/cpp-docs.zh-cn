---
title: 依赖类型的名称解析
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: 04db4b0efc5e58dbd3de6fc9979c3a3cdd44d84e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563145"
---
# <a name="name-resolution-for-dependent-types"></a>依赖类型的名称解析

使用**typename**为模板定义，以告知编译器给定的限定的名称标识的类型中的限定名。 有关详细信息，请参阅[typename](../cpp/typename.md)。

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

针对依赖名称的名称查找将检查模板定义的上下文中的名称，在以下示例中，此上下文将查找`myFunction(char)`— 和模板实例化的上下文。在以下示例中，模板实例化在 main 中;因此，`MyNamespace::myFunction`从实例化的点可见，并且将选取它作为更好的匹配。 如果重命名 `MyNamespace::myFunction`，则将调用 `myFunction(char)`。

所有名称都会得到解析，就如同它们是依赖名称一样。 尽管如此，如果存在任何可能的冲突，建议您使用完全限定名。

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>输出

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>模板消除歧义

Visual Studio 2012 对强制执行 C + + 98/03/11 标准规则使用"template"关键字消除歧义。 在以下示例中，Visual C++ 2010年以接受不一致性行和一致性行。  Visual Studio 2012 接受仅一致性行。

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

需要符合消除歧义规则，因为默认情况下，C++ 假定 `AY::Rebind` 不是模板，因此编译器会将后面的“`<`”解释为小于。 它必须知道 `Rebind` 是模板，这样才能正确地将“`<`”分析为尖括号。

## <a name="see-also"></a>请参阅

[名称解析](../cpp/templates-and-name-resolution.md)